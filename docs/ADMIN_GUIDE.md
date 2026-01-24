# MIZAN POS - Admin Guide

> A comprehensive guide for administrators managing the MIZAN POS system.

---

## Table of Contents
1. [Admin Overview](#admin-overview)
2. [User Management](#user-management)
3. [Product Management](#product-management)
4. [Category Management](#category-management)
5. [Inventory Management](#inventory-management)
6. [Customer Management](#customer-management)
7. [Reports & Analytics](#reports--analytics)
8. [System Settings](#system-settings)
9. [Security Best Practices](#security-best-practices)
10. [Backup & Maintenance](#backup--maintenance)

---

## Admin Overview

### Admin Capabilities
Administrators have full access to all system features:

| Feature           | Admin | Manager | Cashier |
| ----------------- | :---: | :-----: | :-----: |
| Process Sales     |   ✅   |    ✅    |    ✅    |
| View Reports      |   ✅   |    ✅    |    ❌    |
| Manage Products   |   ✅   |    ✅    |    ❌    |
| Manage Inventory  |   ✅   |    ✅    |    ❌    |
| Manage Users      |   ✅   |    ❌    |    ❌    |
| Manage Categories |   ✅   |    ✅    |    ❌    |
| System Settings   |   ✅   |    ❌    |    ❌    |
| Branding          |   ✅   |    ❌    |    ❌    |
| Void Sales        |   ✅   |    ✅    |    ❌    |

### Dashboard Metrics
The admin dashboard displays:
- **Today's Revenue**: Real-time sales total
- **Sales Count**: Number of transactions
- **Low Stock Alerts**: Products needing reorder
- **Out of Stock**: Unavailable products

---

## User Management

### Creating a New User
1. Navigate to **Users** from the sidebar
2. Click **Add User**
3. Fill in the required information:
   - **Name**: Full name of the user
   - **Email**: Login email (must be unique)
   - **Password**: Temporary password (user should change on first login)
   - **Role**: Select Admin, Manager, or Cashier
4. Click **Create User**

### User Roles Explained

#### Admin
- Full system access
- Can manage all users, settings, and data
- Access to sensitive reports and exports
- Can delete products and void any sale

#### Manager
- Can manage products, categories, and inventory
- Access to reports
- Can void sales
- Cannot manage users or system settings

#### Cashier
- POS access only
- Can process sales and manage cart
- Can view their own sales history
- Limited access to customer information

### Deactivating a User
1. Find the user in the **Users** list
2. Click **Edit**
3. Toggle **Active** to off
4. Click **Save**

> **Note**: Deactivated users cannot log in but their sales history is preserved.

### Resetting a User's Password
1. Go to the user's profile
2. Click **Reset Password**
3. Enter a new temporary password
4. Inform the user to change it upon login

---

## Product Management

### Adding a New Product
1. Navigate to **Products → Add Product**
2. Fill in product details:
   - **Name**: Product display name
   - **SKU**: Unique stock keeping unit code
   - **Description**: Optional product description
   - **Categories**: Assign to one or more categories
   - **Active**: Toggle to enable/disable for sale
3. Add at least one variant (see below)
4. Click **Save Product**

### Managing Product Variants
Each product can have multiple variants:

#### Adding a Variant
1. In the product edit page, go to **Variants** section
2. Click **Add Variant**
3. Fill in variant details:
   - **Name**: e.g., "Large", "Red", "500ml"
   - **SKU**: Unique identifier for this variant
   - **Price**: Selling price
   - **Cost**: Purchase cost (for profit calculations)
   - **Stock Quantity**: Current inventory level
   - **Low Stock Threshold**: Alert when stock falls below this
   - **Track Stock**: Enable/disable inventory tracking
4. Click **Save Variant**

#### Bulk Price Updates
1. Select multiple products from the list
2. Click **Bulk Edit**
3. Apply percentage increase/decrease
4. Review and confirm changes

### Importing Products
1. Go to **Products → Import**
2. Download the CSV template
3. Fill in product data following the template format
4. Upload the completed CSV
5. Review import preview
6. Click **Confirm Import**

### Exporting Products
1. Go to **Products**
2. Apply any filters (optional)
3. Click **Export CSV**
4. Use for backup or external analysis

---

## Category Management

### Creating Categories
1. Navigate to **Categories**
2. Click **Add Category**
3. Enter:
   - **Name**: Category display name
   - **Description**: Optional description
   - **Active**: Enable/disable on POS
4. Click **Save**

### Organizing Categories
- Categories appear in the POS for quick filtering
- Order categories by drag-and-drop (if supported)
- Keep category count manageable (5-10 recommended)

### Best Practices
- Use clear, concise category names
- Group similar products logically
- Consider your typical transaction flow

---

## Inventory Management

### Stock Overview
Navigate to **Inventory** to see:
- Total products and variants
- Items requiring attention
- Recent stock movements

### Receiving Stock
When new inventory arrives:
1. Go to **Inventory → Receive Stock**
2. Search for the product/variant
3. Enter quantity received
4. Add optional notes (supplier, PO number)
5. Click **Receive**

### Stock Adjustments
For corrections or counts:
1. Go to **Inventory → Adjust Stock**
2. Select the product/variant
3. Enter the new correct quantity
4. Select adjustment reason:
   - Physical count correction
   - Damage/loss
   - Theft
   - Other
5. Add notes explaining the adjustment
6. Click **Adjust**

### Stock Alerts
Configure alerts in **Settings → Inventory**:
- **Low Stock Threshold**: Default threshold for new products
- **Email Alerts**: Receive notifications when stock is low
- **Dashboard Alerts**: Show warnings on dashboard

### Stock History
Every stock movement is logged:
1. Go to a product's detail page
2. Click **Stock History**
3. View all receipts, adjustments, and sales

---

## Customer Management

### Customer Database
Maintain customer records for:
- Repeat purchase tracking
- Targeted promotions
- Sales history

### Adding Customers
1. Navigate to **Customers → Add Customer**
2. Enter customer information:
   - Name (required)
   - Phone
   - Email
   - Address
   - Notes
3. Click **Save**

### Customer Insights
Click on any customer to see:
- **Total Spent**: Lifetime purchase value
- **Visit Count**: Number of transactions
- **Last Visit**: Most recent purchase date
- **Purchase History**: List of all transactions

### Exporting Customer Data
1. Go to **Customers**
2. Click **Export**
3. Choose format (CSV, Excel)
4. Use for marketing or CRM systems

---

## Reports & Analytics

### Available Reports

#### Daily Summary
- Today's total revenue
- Number of sales
- Average order value
- Payment method breakdown

#### Sales Report
- Filter by date range
- Group by day, week, or month
- Compare periods

#### Top Products
- Best sellers by quantity
- Best sellers by revenue
- Slow-moving inventory

#### Payment Analysis
- Revenue by payment method
- Transaction count by method
- Trends over time

#### Z-Report (End of Day)
Complete daily closing report:
- All sales transactions
- Cash vs. card totals
- Discounts applied
- Tax collected
- Voids and returns

### Exporting Reports
All reports can be exported:
- **CSV**: For spreadsheet analysis
- **PDF**: For printing/archiving
- **Email**: Send directly to stakeholders

### Scheduling Reports
Set up automatic report delivery:
1. Go to **Settings → Reports**
2. Click **Schedule Report**
3. Select report type
4. Choose frequency (daily, weekly, monthly)
5. Enter recipient emails
6. Click **Save Schedule**

---

## System Settings

### General Settings
- **Store Name**: Displayed on receipts
- **Store Address**: Contact information
- **Tax Rate**: Default tax percentage
- **Currency**: Display currency symbol

### Branding
Customize the appearance:
- **Logo**: Upload store logo (recommended: 200x50px PNG)
- **Primary Color**: Main brand color
- **Secondary Color**: Accent color
- **Receipt Header**: Custom text for receipts
- **Receipt Footer**: Terms, thank you message

### Receipt Settings
- Include/exclude store logo
- Customize header and footer text
- Add terms and conditions
- Configure barcode printing

### Security Settings
- **Session Timeout**: Auto-logout after inactivity
- **Password Policy**: Minimum length, complexity
- **2FA Requirement**: Force for all users or admins only

---

## Security Best Practices

### Password Guidelines
- Minimum 8 characters
- Mix of letters, numbers, special characters
- Change every 90 days
- Never share passwords

### Two-Factor Authentication (2FA)
Strongly recommended for all admin accounts:
1. Go to **Settings → Security**
2. Enable 2FA
3. Use Google Authenticator or similar app
4. Store recovery codes securely

### Access Control
- Principle of least privilege
- Regular user access reviews
- Immediately deactivate departed staff
- Audit login history monthly

### Data Protection
- Regular backups
- Encrypted connections (HTTPS)
- Secure database access
- Limit export permissions

---

## Backup & Maintenance

### Database Backups
Automatic backups should be configured:
- **Frequency**: Daily recommended
- **Retention**: Keep 30 days of backups
- **Storage**: Off-site or cloud storage
- **Testing**: Verify backups monthly

### System Updates
Keep the system updated:
1. Review changelog before updating
2. Backup before any update
3. Test in staging if available
4. Update during low-traffic periods
5. Verify functionality after update

### Performance Monitoring
Monitor system health:
- Page load times
- Database performance
- Error logs
- Storage usage

### Support Escalation
For issues you cannot resolve:
1. Document the problem
2. Note steps to reproduce
3. Capture error messages/screenshots
4. Contact technical support

---

## Appendix: Quick Reference

### Keyboard Shortcuts (POS)
| Shortcut | Action        |
| -------- | ------------- |
| `F2`     | Focus search  |
| `F4`     | Complete sale |
| `F8`     | Hold sale     |
| `Esc`    | Cancel/close  |

### Common Tasks
| Task          | Path                |
| ------------- | ------------------- |
| Add product   | Products → Add      |
| Receive stock | Inventory → Receive |
| Create user   | Users → Add         |
| Daily report  | Reports → Z-Report  |

---

*Last updated: December 2025*
*MIZAN POS v0.2.0*
