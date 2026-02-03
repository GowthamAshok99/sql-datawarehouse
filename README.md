# SQL Data Warehouse Project 🚀

**Building a Modern Data Warehouse with SQL Server**

Welcome to the SQL Data Warehouse project! This repository contains all the code, scripts, and documentation for building a complete data engineering solution. The project demonstrates how to build a modern data warehouse using **Microsoft SQL Server**, following best practices like the **Medallion Architecture** (Bronze, Silver, Gold layers) and **Star Schema** modeling.

## 📌 Project Overview

The goal is to consolidate sales data from multiple source systems (ERP and CRM) into a centralized warehouse for analytical reporting.

### Key Objectives:
* **Data Ingestion:** Import data from source systems (CSV files) using `BULK INSERT`.
* **Data Cleaning:** Clean and standardize data using T-SQL Stored Procedures.
* **Architecture:** Implement the Medallion Architecture using SQL Schemas (`bronze`, `silver`, `gold`).
* **Data Modeling:** Design a Star Schema (Fact & Dimensions) optimized for Power BI/Tableau.

## 🏗️ Solution Architecture

This project uses **Schemas** to logically separate data layers within a single database:

1.  **Bronze Layer (`bronze` schema):**
    * Stores raw data as-is from the source.
    * **Method:** Full Load (Truncate & Insert).
    * **Focus:** Quick ingestion and historical record.
2.  **Silver Layer (`silver` schema):**
    * Cleaned, normalized, and enriched data.
    * **Transformations:** Handling nulls, removing duplicates, and standardizing values.
    * **Method:** Stored Procedures (`AS BEGIN ... END`).
3.  **Gold Layer (`gold` schema):**
    * Business-ready data for reporting.
    * **Objects:** Views (`dim_customers`, `dim_products`, `fact_sales`).
    * **Focus:** Aggregation, Star Schema, and business logic.

## 🛠️ Technologies Used

* **Database:** Microsoft SQL Server (or Azure SQL Edge)
* **GUI Tool:** SQL Server Management Studio (SSMS) or Azure Data Studio
* **ETL:** T-SQL (Stored Procedures, Bulk Insert)
* **Version Control:** Git & GitHub

## 📂 Repository Structure

```text
├── datasets/           # Raw CSV files from source systems (ERP & CRM)
├── scripts/            # SQL scripts for the Data Warehouse
│   ├── init_database.sql   # Creates Database and Schemas (bronze, silver, gold)
│   ├── bronze/             # DDLs and 'BULK INSERT' procedures
│   ├── silver/             # Stored Procedures for cleaning data
│   └── gold/               # View definitions for reporting
└── README.md           # Project documentation
