# Project Context: Mizan POS

## 🎯 Objective
To build a scalable, cloud-native Point of Sale system that bridges the gap between complex ERPs and simple cashier apps. The goal was to provide enterprise-grade reliability (Atomic Transactions, Role-Based Access) with a consumer-grade User Interface.

## 👥 Target Audience
-   **Primary**: Retail store owners (Supermarkets, Clothing, Electronics).
-   **Secondary**: Warehouse managers requiring precise stock control.

## 🧩 The Challenge
Most affordable POS systems suffer from one of two issues:
1.  **Complexity**: Built as legacy desktop apps that are hard to use.
2.  **Unreliability**: Web-based apps that lose data when the internet flickers.

## 💡 The Solution
Mizan POS uses a **Hybrid Cloud approach**:
-   **Frontend**: A React SPA that feels native and manages temporary state locally.
-   **Backend**: A robust Laravel API that acts as the single source of truth, enforcing data integrity via database transactions and locking mechanisms.
