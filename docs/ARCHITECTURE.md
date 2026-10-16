# System Architecture

## Overview
Mizan POS follows a **Monolithic Architecture** with a clear separation of concerns (SoC) between the Presentation Layer (React via Inertia) and the Domain Layer (Laravel).

```mermaid
graph TD
    User[Client Browser] -->|HTTPS| Nginx[Nginx]
    Nginx -->|PHP-FPM| App[Laravel App]
    App -->|Read/Write| DB[(MySQL Primary)]
    App -->|Backups| S3[AWS S3 via Spatie Backup]
```

## Data Model

### Key Entities
-   **`User`**: System actors (Admin, Manager, Cashier).
-   **`Product`**: The base item (e.g., "T-Shirt").
-   **`Variant`**: Specific SKUs (e.g., "T-Shirt Red XL").
-   **`StockLedger`**: Immutable record of logic inventory changes.
-   **`Sale`**: The header record for a transaction.
-   **`SaleLine`**: Individual items within a transaction.

## Design Patterns

### 1. Service Layer
Business logic is extracted from Controllers into Services (e.g., `SaleService`, `InventoryService`). This keeps controllers thin and keeps the checkout, void and return flows in one place.

### 2. Policy Pattern (Authorization)
Laravel Policies enforce RBAC.
-   `viewAny`: Can the user see the list?
-   `create`: Can they add a new item?
-   `void`: Special permission for Managers to void sales.
