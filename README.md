# sql-datawarehouse
Building Data warehouse with MY SQL using ETL and Latest architecture
# MySQL Data Warehouse Project 🐬

**Building a Modern Data Warehouse with MySQL**

Welcome to the MySQL Data Warehouse project! This repository adapts the classic "Data with Baraa" SQL Server project for **MySQL**. It demonstrates how to build a modern data engineering solution using **MySQL 8.0+**, following best practices like the **Medallion Architecture** (Bronze, Silver, Gold layers) and **Star Schema** modeling.

## 📌 Project Overview

The goal is to consolidate sales data from multiple source systems (ERP and CRM) into a centralized MySQL warehouse for analytical reporting.

### Key Objectives:
* **Data Ingestion:** Import CSV data into MySQL using `LOAD DATA INFILE` or Workbench import wizards.
* **Data Cleaning:** Sanitize data using MySQL-specific functions and Stored Procedures.
* **Architecture:** Implement logical separation using distinct databases or table naming conventions.
* **Data Modeling:** Star Schema (Fact & Dimensions) optimized for Power BI/Tableau.

## 🏗️ Solution Architecture (MySQL Edition)

Since MySQL treats `SCHEMA` and `DATABASE` as synonyms, we use **separate databases** (or table prefixes) to logically separate the layers:

1.  **Bronze Layer (`dw_bronze`):**
    * Raw data ingestion.
    * **Method:** Full Load via `LOAD DATA LOCAL INFILE`.
2.  **Silver Layer (`dw_silver`):**
    * Cleansed and Standardized data.
    * **Transformations:** `TRIM()`, `STR_TO_DATE()`, and `CASE` logic.
3.  **Gold Layer (`dw_gold`):**
    * Reporting View layer.
    * **Objects:** Views (`v_dim_customers`, `v_fact_sales`).

## 🛠️ Technologies Used

* **Database:** MySQL 8.0+
* **GUI Tool:** MySQL Workbench or DBeaver
* **ETL:** Stored Procedures & `LOAD DATA` commands
* **Version Control:** Git & GitHub

## 📂 Repository Structure

```text
├── datasets/           # Raw CSV files
├── scripts/            # SQL scripts
│   ├── 00_init_database.sql    # Creates dw_bronze, dw_silver, dw_gold databases
│   ├── bronze/             # Loading scripts (LOAD DATA INFILE)
│   ├── silver/             # Stored Procedures (Data Cleaning)
│   └── gold/               # DDLs (Views for Reporting)
└── README.md           # Documentation
