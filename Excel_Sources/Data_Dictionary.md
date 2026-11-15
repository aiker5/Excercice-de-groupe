# Contoso Retail - Excel source files (data dictionary)

Synthetic, fictional data generated for the Power BI + GitHub Copilot hackathon (random seed 20261031).
No real company, customer or personal information is used. All monetary values are in **USD**.
Period covered: **1 January 2023 - 31 December 2025** (3 full years). Each file contains one worksheet named like the file.

| File | Sheet | Rows | Grain |
|---|---|---|---|
| Sales.xlsx | Sales | 182,567 | One row per sales order line |
| Products.xlsx | Products | 1,500 | One row per product |
| Customers.xlsx | Customers | 8,000 | One row per customer |
| Stores.xlsx | Stores | 79 | One row per store (including 7 online stores) |
| Targets.xlsx | Targets | 2,770 | One row per store and month |

## Sales.xlsx
| Column | Type | Description |
|---|---|---|
| SalesOrderID | integer | Sales order number (78,016 orders). An order contains 1-6 lines. |
| SalesOrderLineID | integer | Unique line identifier (technical key). |
| OrderDate | date | Order date (2023-01-01 to 2025-12-31). |
| ProductID | integer | Product key -> Products.ProductID |
| CustomerID | integer | Customer key -> Customers.CustomerID |
| StoreID | integer | Store key -> Stores.StoreID (online orders use the online store of the customer's country) |
| Quantity | integer | Units sold (1-24). |
| UnitPrice | decimal | Unit selling price before discount. |
| UnitCost | decimal | Unit cost of goods sold. |
| Discount | decimal | Discount rate (0.10 = 10%); 0 when no discount. |
| SalesChannel | text | `In-Store` or `Online`. |

Business rules: **Net revenue = Quantity x UnitPrice x (1 - Discount)**; **Cost = Quantity x UnitCost**; **Gross profit = Revenue - Cost**.
Prices and costs increase slightly each year (2023 < 2024 < 2025). A small share of heavily discounted lines has a negative margin.

## Products.xlsx
| Column | Type | Description |
|---|---|---|
| ProductID | integer | Product key (1-1500). |
| ProductName | text | Unique product name (brand + model + variant + colour). |
| Category | text | 5 categories: Electronics, Home and Kitchen, Clothing and Accessories, Sports and Outdoors, Toys and Games. |
| Subcategory | text | 24 subcategories; each belongs to exactly one category. |
| Brand | text | Fictional brand. |
| StandardCost | decimal | Current (2025) standard unit cost. |
| ListPrice | decimal | Current (2025) list price. |

## Customers.xlsx
| Column | Type | Description |
|---|---|---|
| CustomerID | integer | Customer key (1-8000). |
| CustomerName | text | Fictional, unique name (persons for Consumer/Premium, companies for Small Business/Corporate). |
| CustomerSegment | text | Consumer, Premium, Small Business, Corporate. |
| Country | text | Customer country (same 7 countries as the stores). |
| City | text | Customer city. |
| RegistrationDate | date | Registration date (2016-2025). Customers never buy before their registration date. |

## Stores.xlsx
| Column | Type | Description |
|---|---|---|
| StoreID | integer | Store key (1-79). |
| StoreName | text | Unique store name. |
| Country | text | United States, Canada, United Kingdom, France, Germany, Japan, Australia. |
| Region | text | North America, Europe, Asia Pacific. |
| City | text | Store city; `Online` for the 7 online stores. |
| StoreType | text | Flagship, Standard, Outlet, Express, Online. |
| OpeningDate | date | Opening date. 5 stores opened between April 2023 and May 2025 (no sales or targets before opening). |

## Targets.xlsx
| Column | Type | Description |
|---|---|---|
| Year | integer | Target year (2023-2025). |
| Month | integer | Target month (1-12). |
| StoreID | integer | Store key -> Stores.StoreID |
| SalesTarget | decimal | Monthly net revenue target (USD). |
| ProfitTarget | decimal | Monthly gross profit target (USD). |

Targets are **monthly**: analyse them at month, quarter or year level (for example by relating them to the date table on the first day of the month).

## Data quality
* All foreign keys exist in their dimension files (100% referential integrity).
* No sale occurs before the store opening date or the customer registration date.
* Every store-month with sales has a target, and every target row has sales.

