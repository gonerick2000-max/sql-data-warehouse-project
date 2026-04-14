# SQL DataWareHouse Project

## Overview

This project implements a Data Warehouse in SQL Server following the Medallion Architecture (Bronze, Silver, Gold).

The pipeline ingests raw data from CRM and ERP systems, transforms it into structured datasets, and exposes it through a dimensional model (star schema) for analytics and reporting.

---

## Medallion Architecture
### Bronze Layer
- Raw Data from the source systems is stored
- No transformations are applied
### Silver Layer
Load data from the bronze layer and apply the following transformations:
- Data cleansing (TRIM, NULL handling, invalid value filtering)
- Data deduplication using window functions (ROW_NUMBER)
- Standardization of categorical values (e.g., gender, status)
- Data type corrections and formatting (e.g., date conversion)
- Basic business logic and enrichment (e.g., price correction, derived sales) 
### Gold Layer

---

## Data Analysis
![Gráficas](scripts/4_DataAnalysis/plt_merge_plts.png)

---

## Greetings
I would like to thanks to the Youtube channel DataWithBaraa, which I used to learn about SQL language and get some knowledge about Data Engeneering. A great part of the material presented in this project is extracted from the project course of the channel.
