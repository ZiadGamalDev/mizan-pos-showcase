# MIZAN POS - Deployment Guide

> Quick deployment guide for setting up MIZAN POS on a new server.

---

## Table of Contents
1. [Requirements](#requirements)
2. [Server Setup](#server-setup)
3. [Application Deployment](#application-deployment)
4. [Database Setup](#database-setup)
5. [Environment Configuration](#environment-configuration)
6. [Nginx Configuration](#nginx-configuration)
7. [SSL Certificate](#ssl-certificate)
8. [Post-Deployment](#post-deployment)
9. [Troubleshooting](#troubleshooting)

---

## Requirements

### Server Requirements
| Component | Minimum       | Recommended      |
| --------- | ------------- | ---------------- |
| OS        | Ubuntu 20.04+ | Ubuntu 22.04 LTS |
| CPU       | 1 vCPU        | 2 vCPU           |
| RAM       | 1 GB          | 2 GB             |
| Storage   | 10 GB         | 20 GB SSD        |

### Software Requirements
- PHP 8.1+
- Composer 2.x
- Node.js 18+ & npm
- MySQL 8.0+ or PostgreSQL 14+
- Nginx or Apache
- Git
- Supervisor (for queues)

---

## Server Setup

### 1. Update System
```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Install PHP 8.2
```bash
sudo add-apt-repository ppa:ondrej/php -y
sudo apt update
sudo apt install php8.2 php8.2-fpm php8.2-cli php8.2-mysql php8.2-pgsql \
    php8.2-mbstring php8.2-xml php8.2-curl php8.2-zip php8.2-bcmath \
    php8.2-gd php8.2-intl -y
```

### 3. Install Composer
```bash
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```

### 4. Install Node.js 20
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install nodejs -y
```

### 5. Install MySQL
```bash
sudo apt install mysql-server -y
sudo mysql_secure_installation
```

### 6. Install Nginx
```bash
sudo apt install nginx -y
```

---

## Application Deployment

### 1. Create Application Directory
```bash
sudo mkdir -p /var/www/mizan-pos
sudo chown $USER:$USER /var/www/mizan-pos
```

### 2. Clone Repository
```bash
cd /var/www/mizan-pos
git clone https://github.com/your-repo/mizan-pos.git .
```

### 3. Install PHP Dependencies
```bash
composer install --no-dev --optimize-autoloader
```

### 4. Install Node Dependencies & Build
```bash
npm ci
npm run build
```

### 5. Set Permissions
```bash
sudo chown -R www-data:www-data /var/www/mizan-pos
sudo chmod -R 755 /var/www/mizan-pos
sudo chmod -R 775 /var/www/mizan-pos/storage
sudo chmod -R 775 /var/www/mizan-pos/bootstrap/cache
```

---

## Database Setup

### 1. Create Database
```bash
sudo mysql -u root -p
```

```sql
CREATE DATABASE mizan_pos CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'mizan_user'@'localhost' IDENTIFIED BY 'your_secure_password';
GRANT ALL PRIVILEGES ON mizan_pos.* TO 'mizan_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

### 2. Run Migrations
```bash
php artisan migrate --force
```

### 3. Seed Initial Data (Optional)
```bash
# For demo/development:
php artisan db:seed

# For production (admin user only):
php artisan db:seed --class=AdminUserSeeder
```

---

## Environment Configuration

### 1. Copy Environment File
```bash
cp .env.example .env
```

### 2. Configure Environment Variables
```bash
nano .env
```

Update these values:
```env
APP_NAME="MIZAN POS"
APP_ENV=production
APP_KEY=
APP_DEBUG=false
APP_URL=https://your-domain.com

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=mizan_pos
DB_USERNAME=mizan_user
DB_PASSWORD=your_secure_password

MAIL_MAILER=smtp
MAIL_HOST=smtp.example.com
MAIL_PORT=587
MAIL_USERNAME=your_email
MAIL_PASSWORD=your_password
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=noreply@your-domain.com
MAIL_FROM_NAME="${APP_NAME}"
```

### 3. Generate Application Key
```bash
php artisan key:generate
```

### 4. Cache Configuration
```bash
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

---

## Nginx Configuration

### 1. Create Site Configuration
```bash
sudo nano /etc/nginx/sites-available/mizan-pos
```

```nginx
server {
    listen 80;
    server_name your-domain.com;
    root /var/www/mizan-pos/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";

    index index.php;

    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }

    error_page 404 /index.php;

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }
}
```

### 2. Enable Site
```bash
sudo ln -s /etc/nginx/sites-available/mizan-pos /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```

---

## SSL Certificate

### Using Let's Encrypt (Free)
```bash
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d your-domain.com
```

### Auto-Renewal
```bash
sudo certbot renew --dry-run
```

---

## Post-Deployment

### 1. Create Admin User
```bash
php artisan tinker
```

```php
User::create([
    'name' => 'Admin User',
    'email' => 'admin@your-domain.com',
    'password' => bcrypt('secure_password'),
    'role' => 'admin',
    'email_verified_at' => now(),
]);
```

### 2. Set Up Scheduler (Cron)
```bash
sudo crontab -e
```

Add:
```cron
* * * * * cd /var/www/mizan-pos && php artisan schedule:run >> /dev/null 2>&1
```

### 3. Set Up Queue Worker (Supervisor)
```bash
sudo apt install supervisor -y
sudo nano /etc/supervisor/conf.d/mizan-worker.conf
```

```ini
[program:mizan-worker]
process_name=%(program_name)s_%(process_num)02d
command=php /var/www/mizan-pos/artisan queue:work --sleep=3 --tries=3
autostart=true
autorestart=true
user=www-data
numprocs=2
redirect_stderr=true
stdout_logfile=/var/www/mizan-pos/storage/logs/worker.log
```

```bash
sudo supervisorctl reread
sudo supervisorctl update
sudo supervisorctl start mizan-worker:*
```

### 4. Verify Deployment
- [ ] Application loads at your domain
- [ ] Admin can log in
- [ ] POS page works
- [ ] Products display correctly
- [ ] Sale completes successfully

---

## Troubleshooting

### Common Issues

#### "500 Internal Server Error"
```bash
# Check Laravel logs
tail -f /var/www/mizan-pos/storage/logs/laravel.log

# Check permissions
sudo chown -R www-data:www-data storage bootstrap/cache
```

#### "Page not found" (Nginx)
```bash
# Verify Nginx config
sudo nginx -t

# Check root directory
ls -la /var/www/mizan-pos/public/
```

#### Database Connection Failed
```bash
# Test MySQL connection
mysql -u mizan_user -p mizan_pos

# Check .env database settings
cat .env | grep DB_
```

#### Assets Not Loading
```bash
# Rebuild assets
npm run build

# Clear cache
php artisan cache:clear
php artisan config:clear
```

---

## Quick Update Procedure

When deploying updates:

```bash
cd /var/www/mizan-pos

# Enter maintenance mode
php artisan down

# Pull latest code
git pull origin main

# Install dependencies
composer install --no-dev --optimize-autoloader
npm ci && npm run build

# Run migrations
php artisan migrate --force

# Clear caches
php artisan config:cache
php artisan route:cache
php artisan view:cache

# Restart queue workers
sudo supervisorctl restart mizan-worker:*

# Exit maintenance mode
php artisan up
```

---

## Environment Variables Reference

| Variable           | Description     | Example                   |
| ------------------ | --------------- | ------------------------- |
| `APP_ENV`          | Environment     | `production`              |
| `APP_DEBUG`        | Debug mode      | `false`                   |
| `APP_URL`          | Application URL | `https://pos.example.com` |
| `DB_DATABASE`      | Database name   | `mizan_pos`               |
| `MAIL_HOST`        | SMTP server     | `smtp.gmail.com`          |
| `QUEUE_CONNECTION` | Queue driver    | `database`                |

---

*Last updated: December 2025*
*MIZAN POS v0.2.0*
