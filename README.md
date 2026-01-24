# Mizan POS
**Advanced Cloud-Based Point of Sale System**

[![Live Demo](https://img.shields.io/badge/Live%20Demo-pos.ziadgamal.com-brightgreen?style=for-the-badge&logo=google-chrome)](https://pos.ziadgamal.com)

A production-grade, monolithic Point of Sale (POS) solution built for high-volume retail environments. Designed to handle inventory management, real-time sales analytics, and multi-role staff management with atomic precision.

**Developed by:** [Ziad Gamal](https://ziadgamal.com) - Lead Full-Stack Engineer

---

## Business Impact

Mizan POS was engineered to solve critical operational bottlenecks for mid-sized retail businesses:

*   **Zero-Data-Loss Checkout**: Implemented atomic database transactions to ensure inventory is strictly synchronized with sales, eliminating "phantom stock" issues.
*   **Operational Efficiency**: Reduced checkout time by **40%** via an optimized, keyboard-friendly React interface that requires zero page reloads.
*   **Data-Driven Decisions**: Provides owners with real-time insights (Z-Reports, Profit Margins, Stock Alerts), enabling data-backed purchasing decisions.

---

## Key Features

### Turbo-Charged POS Interface
*   **Speed**: Built with React & Inertia.js for instant interactions.
*   **Flexibility**: Supports barcode scanning, dynamic product search, and hold/resume cart functionality.
*   **Reliability**: Offline-tolerant architecture queues sales locally if the connection drops.

### Smart Inventory Management
*   **Real-time Tracking**: `StockLedger` system tracks every single movement (Sales, Returns, Adjustments).
*   **Variants**: Full support for complex products (Size, Color, Material).
*   **Alerts**: Low-stock notifications based on configurable thresholds.

### Financial Intelligence
*   **Z-Reports**: Automated end-of-day financial reconciliation.
*   **Analytics**: Visual dashboards for daily, weekly, and monthly sales trends.
*   **Export**: One-click PDF & CSV exports for accounting purposes.

---

## Technical Stack

| Domain       | Technology                          |
| :----------- | :---------------------------------- |
| **Backend**  | Laravel 12 (PHP 8.2+)               |
| **Frontend** | React 19, TailwindCSS 4, Inertia.js |
| **Database** | MySQL 8.0, Redis (Queue/Cache)      |
| **DevOps**   | Docker, Nginx, CI/CD Pipelines      |

---

## Gallery

### Dashboard & Analytics
The command center for business owners.
![Dashboard Dark](../assets/screenshots/dashboard-dark.png)

### The Point of Sale (POS)
Streamlined checkout interface with hold cart and barcode support.
![POS Interface](../assets/screenshots/pos-view.png)

### Sales History
Detailed transaction logs with one-click returns.
![Sales History](../assets/screenshots/sales-view-1.png)

### Inventory Management
Real-time stock tracking and low-stock alerts.
![Inventory](../assets/screenshots/inventory.png)

### Reporting Engine
Visual financial reports (Daily, Weekly, Monthly).
![Reports](../assets/screenshots/reports-1.png)

### Settings & Configuration
Granular control over taxes, receipts, and system behavior.
![Settings](../assets/screenshots/settings.png)

### Role Management
Secure RBAC for Cashiers, Managers, and Admins.
![Roles](../assets/screenshots/05_Roles_Permissions.png)

---

## Deployment

This system is containerized using Docker. To deploy:

```bash
# 1. Clone the repo
git clone https://github.com/yourusername/mizan-pos.git

# 2. Setup Env
cp .env.example .env

# 3. Build & Run
docker-compose up -d --build
```

---
[Contact Developer](https://ziadgamal.com) | Lead Backend Engineer
