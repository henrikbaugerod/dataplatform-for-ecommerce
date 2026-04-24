# 📊 E-commerce Data Platform (Databricks)

## 📌 Overview
This project demonstrates the design and implementation of an end-to-end data pipeline for e-commerce data using **Databricks** and the **Medallion Architecture (Bronze, Silver, Gold)**.

The pipeline ingests raw JSON data, performs data quality validation, transforms nested structures, and produces analytics-ready datasets.

---

## 🏗️ Architecture

The solution follows the **Medallion Architecture**:

- **Bronze Layer**  
  Raw ingestion of JSON data (customers, orders, items)

- **Silver Layer**  
  Cleaned and validated data:
  - Deduplication
  - Data type validation
  - Referential integrity checks
  - Handling of nested structures

- **Gold Layer**  
  Business-ready datasets for analytics and reporting

---

## 📂 Data Model

### Input Data
- `customers.json`
- `items.json`
- `orders.json` (with nested item arrays)

### Key Relationships
- Orders → Customers (`customer_id`)
- Orders → Items (nested array of `item_id`, `quantity`)

---

## ⚙️ Key Features

### 🔹 Data Ingestion
- Loaded semi-structured JSON into Databricks tables
- Schema inference and structured storage

### 🔹 Data Quality Validation
- Detection of duplicate primary keys
- Validation of foreign key relationships
- Identification of:
  - Missing values
  - Invalid dates
  - Invalid quantities
  - Missing item references

### 🔹 Data Transformation
- Flattening nested arrays using `explode`
- Rebuilding nested structures using `collect_list` / `collect_set`
- Deduplication using window functions (`ROW_NUMBER`)
- Type casting and validation (`try_to_date`)

### 🔹 Data Modeling
- Cleaned datasets in Silver layer
- Aggregated datasets in Gold layer:
  - Customer-level metrics
  - Order-level metrics
  - Product performance

---

## 🧪 Data Quality Scenarios Handled

The dataset includes intentional data issues to simulate real-world conditions:

- Duplicate IDs (customers, items, orders)
- Missing foreign key references
- Invalid date formats
- Null and inconsistent values
- Invalid nested records

---

## 📊 Example Outputs

- Validated and deduplicated customer table
- Cleaned orders with only valid nested items
- Flattened order line dataset
- Aggregated customer metrics:
  - Total revenue
  - Number of orders
  - Average order value

---

## 🛠️ Technologies Used

- **Databricks**
- **Apache Spark (SQL)**
- **JSON (semi-structured data)**

---

## 🚀 What This Project Demonstrates

- Building scalable data pipelines
- Handling semi-structured and nested data
- Implementing data quality checks
- Applying Medallion Architecture in practice
- Designing analytics-ready data models

---

## 📈 Possible Extensions

- Incremental data ingestion (streaming or batch)
- Slowly Changing Dimensions (SCD)
- Data quality monitoring dashboards
- Integration with BI tools (Power BI, Tableau)

---

## 👤 Author

This project was created as part of a hands-on data engineering learning initiative using Databricks.

---