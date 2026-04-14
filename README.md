# SQL DataWareHouse Project

## Overview

This project implements a Data Warehouse in SQL Server following the Medallion Architecture (Bronze, Silver, Gold).

The pipeline ingests raw data from CRM and ERP systems, transforms it into structured datasets, and exposes it through a dimensional model (star schema) for analytics and reporting.

---

## Medallion Architecture
### Bronze Layer
- Raw Data from the source systems (CRM and ERP) is stored
- No transformations are applied

### Silver Layer
The purpose of this layer is to clean and standardize the data from the sources. To achieve that purpose, the following transformations are applied: 
- Data cleansing (TRIM, NULL handling, invalid value filtering)
- Data deduplication using window functions (ROW_NUMBER)
- Standardization of categorical values
- Data type corrections and formatting
- Basic business logic and enrichment

### Gold Layer
Implements a **star schema**.
#### Dimensions
* `gold.dim_customers`
* `gold.dim_products`
#### Fact Table:
* `gold.fact_sales`

Key features:
- Integration of CRM and ERP datasets
- Creation of surrogate keys for dimensions
- Business-friendly column naming
- Handling of temporal product data (validity ranges)
---
## ETL Process

### 1. Create database and schemas

```sql
EXEC bronze.create_tables;
```

### 2. Load raw data (Bronze)

```sql
EXEC bronze.load_val;
```
Key features: 
- Truncation and bulk insert methods are used for the loading of the data

### 3. Transform data (Silver)

```sql
EXEC silver.load_val;
```
Key features: 
- Data is stored using the truncation method

### 4. Create analytical views (Gold)

Run the gold layer script (`load_gold.sql`) to create the views:

* `dim_customers`
* `dim_products`
* `fact_sales`

## Data Analysis
Example of business insights generated in this project:
### 📈 Time-Based Analysis

* Order volume evolution over time

As a result of this analysis we could determine could separate the hystory of sales in two periods of time in which the monthly order trends are clearly different.

### 🛍️ Product Performance

* Sales contribution by category and subcategory
  
With this analysis we identify the top-performing product categories.

### 👤 Customer Classification

Based on the Total Sales and the Activity duration of each customer we can determine the type of customers of the business:
  * **VIP**: more than 2 years of activity and more than 5000$ in purchases
  * **Silver**: less than 2 years of activity and more than 5000$ in purchases
  * **New Customer**: less than 2 years of activity and less than 5000$ in purchases

![Gráficas](scripts/4_DataAnalysis/plt_merge_plts.png)

---

## Greetings
I would like to thanks to the Youtube channel DataWithBaraa, which I used to learn about SQL language and get some knowledge about Data Engeneering. A great part of the material presented in this project is extracted from the project course of the channel.
