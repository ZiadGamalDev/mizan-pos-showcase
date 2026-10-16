# Project Context: Mizan POS

## 🎯 Objective
To build a web-based Point of Sale system that bridges the gap between complex ERPs and simple cashier apps. The goal was reliable checkout (database transactions, role-based access) with a simple, modern interface.

## 👥 Target Audience
-   **Primary**: Retail store owners (Supermarkets, Clothing, Electronics).
-   **Secondary**: Warehouse managers requiring precise stock control.

## 🧩 The Challenge
Most affordable POS systems suffer from one of two issues:
1.  **Complexity**: Built as legacy desktop apps that are hard to use.
2.  **Unreliable stock numbers**: sales and inventory that drift apart.

## 💡 The Solution
Mizan POS is a Laravel + Inertia React monolith:
-   **Frontend**: React pages served through Inertia.js.
-   **Backend**: Laravel services as the single source of truth, enforcing data integrity with database transactions.
