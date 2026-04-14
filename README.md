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
The purpose of this layer is to clean and standardize the data from the sources. For that, in this layer the following transformations are applied: 
- Data cleansing (TRIM, NULL handling, invalid value filtering)
- Data deduplication using window functions (ROW_NUMBER)
- Standardization of categorical values
- Data type corrections and formatting
- Basic business logic and enrichment

### Gold Layer
Implements a star schema.
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

## Data Analysis
![Gráficas](scripts/4_DataAnalysis/plt_merge_plts.png)

---

## Greetings
I would like to thanks to the Youtube channel DataWithBaraa, which I used to learn about SQL language and get some knowledge about Data Engeneering. A great part of the material presented in this project is extracted from the project course of the channel.
