# MIZAN POS - User Guide

> A comprehensive guide for cashiers and staff using the MIZAN POS system.

---

## Table of Contents
1. [Getting Started](#getting-started)
2. [Dashboard Overview](#dashboard-overview)
3. [Point of Sale (POS)](#point-of-sale-pos)
4. [Managing Sales](#managing-sales)
5. [Customer Management](#customer-management)
6. [Products & Inventory](#products--inventory)
7. [Reports](#reports)
8. [Settings](#settings)
9. [Troubleshooting](#troubleshooting)

---

## Getting Started

### Logging In
1. Navigate to your MIZAN POS URL
2. Enter your email and password
3. If Two-Factor Authentication (2FA) is enabled, enter the code from your authenticator app
4. Click **Log In**

### Language Settings
- Click the **EN/AR** button in the top navigation to switch between English and Arabic
- The interface automatically adjusts for Right-to-Left (RTL) when Arabic is selected

### Theme Settings
- Go to **Settings → Appearance** to choose between Light, Dark, or System theme

---

## Dashboard Overview

The dashboard provides a quick snapshot of your business:

| Card                | Description                            |
| ------------------- | -------------------------------------- |
| **Today's Revenue** | Total sales amount for today           |
| **Today's Sales**   | Number of completed sales today        |
| **Low Stock Items** | Products below the low stock threshold |
| **Out of Stock**    | Products with zero inventory           |

### Weekly Revenue Chart
- Shows daily revenue for the past 7 days
- Hover over bars to see exact amounts

### Recent Sales
- Displays the 5 most recent transactions
- Click to view sale details

---

## Point of Sale (POS)

The POS screen is where you process customer transactions.

### Layout
- **Left Panel**: Cart and payment section
- **Center Panel**: Product search and results
- **Right Panel**: Category navigation (optional)

### Processing a Sale

#### Step 1: Find Products
- **Search**: Type product name, SKU, or barcode in the search bar
- **Scan**: Use a barcode scanner to automatically add items

#### Step 2: Add to Cart
- Click on a product to add it to the cart
- Adjust quantity using **+** and **-** buttons
- To remove an item, click the **×** button

#### Step 3: Apply Discounts (Optional)
- Click **Add Discount** to apply a percentage or fixed discount
- Discounts can be applied to individual items or the entire order

#### Step 4: Select Customer (Optional)
- Click **Select Customer** to link the sale to a customer profile
- This enables customer purchase history tracking

#### Step 5: Complete Payment
1. Select payment method: **Cash**, **Card**, **Mobile**, or **Other**
2. For cash payments, enter the amount tendered
3. The system calculates change automatically
4. Click **Complete Sale**

#### Step 6: Receipt
- A receipt is generated automatically
- Options: Print, Email, or Download PDF

### Quick Actions
- **Hold Sale**: Save the current cart for later
- **Recall Sale**: Retrieve a held sale
- **Clear Cart**: Remove all items from the cart

---

## Managing Sales

### Viewing Sales History
1. Navigate to **Sales** from the sidebar
2. Use filters to search by date, customer, or status
3. Click on any sale to view details

### Sale Statuses
| Status        | Description                      |
| ------------- | -------------------------------- |
| **Completed** | Sale successfully processed      |
| **Pending**   | Sale on hold or awaiting payment |
| **Voided**    | Sale cancelled/refunded          |

### Voiding a Sale
1. Open the sale details
2. Click **Void Sale**
3. Enter a reason for the void
4. Stock is automatically restored

---

## Customer Management

### Adding a New Customer
1. Go to **Customers** from the sidebar
2. Click **Add Customer**
3. Fill in the customer details:
   - Name (required)
   - Phone
   - Email
   - Address
   - Notes
4. Click **Save**

### Editing Customer Information
1. Find the customer in the list
2. Click the **Edit** button
3. Update the information
4. Click **Save Changes**

### Customer Purchase History
- Click on a customer to view their complete purchase history
- See total spent, number of visits, and average order value

---

## Products & Inventory

### Viewing Products
- Navigate to **Products** from the sidebar
- Use search and filters to find specific items
- Click on a product to view/edit details

### Product Variants
Products can have multiple variants (e.g., sizes, colors):
- Each variant has its own SKU, price, and stock level
- Example: "T-Shirt" product with "Small", "Medium", "Large" variants

### Checking Stock Levels
| Indicator          | Meaning                       |
| ------------------ | ----------------------------- |
| 🟢 **In Stock**     | Adequate inventory            |
| 🟡 **Low Stock**    | Below threshold, reorder soon |
| 🔴 **Out of Stock** | Zero inventory, cannot sell   |

### Quick Stock Check
- **Dashboard**: View low/out of stock counts
- **Inventory → Low Stock**: List all items needing reorder
- **Inventory → Out of Stock**: List all unavailable items

---

## Reports

### Accessing Reports
1. Navigate to **Reports** from the sidebar
2. Select date range (Today, This Week, This Month, Custom)

### Available Reports

#### Summary Report
- Total revenue, sales count, average order value
- Payment method breakdown
- Tax collected

#### Top Products
- Best-selling products by quantity
- Best-selling products by revenue

#### Z-Report (End of Day)
- Complete daily summary
- Cash drawer reconciliation
- Export to CSV/PDF

### Exporting Data
- Click **Export CSV** to download report data
- Use for accounting software or further analysis

---

## Settings

### Profile Settings
- Update your name and email
- Change your password

### Appearance
- Switch between Light/Dark/System themes
- Select preferred language

### Two-Factor Authentication (2FA)
For enhanced security:
1. Go to **Settings → Two-Factor Authentication**
2. Click **Enable**
3. Scan QR code with authenticator app
4. Enter verification code
5. Save recovery codes securely

### Branding (Admin Only)
- Customize store name and logo
- Update receipt footer text
- Set primary brand colors

---

## Troubleshooting

### Common Issues

#### "Product not found" when scanning
- Ensure the barcode is registered in the system
- Check if the product is active

#### Sale won't complete
- Verify payment amount is entered correctly
- Check internet connection
- Ensure sufficient stock is available

#### Can't log in
- Verify email and password
- Check if account is locked (contact admin)
- Clear browser cache and try again

### Getting Help
- Contact your system administrator
- Email support: support@example.com

---

## Keyboard Shortcuts

| Shortcut | Action               |
| -------- | -------------------- |
| `F2`     | Focus search bar     |
| `F4`     | Complete sale        |
| `F8`     | Hold sale            |
| `Esc`    | Clear current action |

---

*Last updated: December 2025*
*MIZAN POS v0.2.0*
