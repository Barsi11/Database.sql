# Product Catalog Database (MySQL)

A MySQL database script for a simple e-commerce product catalog, created as the
database layer for a full-stack technical assignment (Angular + .NET Core + SQL Server spec).

## What's Included
- `schema.sql` — creates the `ProductCatalogDb` database and `Products` table
- Indexes on `Category` and `Price` for faster filtering
- 15 diverse sample products across 6 categories (Electronics, Clothing, Books,
  Home & Kitchen, Furniture, Sports & Outdoors)

## Schema

| Column | Type | Notes |
|---|---|---|
| Id | INT, AUTO_INCREMENT | Primary Key |
| Name | VARCHAR(200) | |
| Description | VARCHAR(1000) | |
| Price | DECIMAL(10,2) | |
| Category | VARCHAR(100) | Indexed |
| ImageUrl | VARCHAR(500) | |
| StockQuantity | INT | Default 0 |
| CreatedDate | DATETIME | Default CURRENT_TIMESTAMP |
| LastUpdatedDate | DATETIME | Default CURRENT_TIMESTAMP |

## How to Run
1. Open `schema.sql` in MySQL Workbench (or any MySQL client)
2. Execute the full script
3. Verify with:
   ```sql
   SELECT * FROM Products;
   SELECT COUNT(*) FROM Products;
   ```

## Sample Queries
```sql
-- Filter by category
SELECT * FROM Products WHERE Category = 'Electronics';

-- Search by name or description
SELECT * FROM Products WHERE Name LIKE '%wireless%' OR Description LIKE '%wireless%';

-- Filter by price range
SELECT * FROM Products WHERE Price BETWEEN 20 AND 100;

-- Combine filters
SELECT * FROM Products
WHERE Category = 'Electronics'
  AND Price BETWEEN 10 AND 100
  AND (Name LIKE '%mouse%' OR Description LIKE '%mouse%');
```

## Note
The original assignment specified MS SQL Server. This script was adapted to
MySQL syntax (`AUTO_INCREMENT` instead of `IDENTITY`, `VARCHAR` instead of
`NVARCHAR`, `CURRENT_TIMESTAMP` instead of `GETDATE()`). A SQL Server (T-SQL)
version is also available if needed.
