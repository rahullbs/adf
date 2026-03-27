# 📊 Metadata-Driven Incremental Data Pipeline (ADF + ADLS)

## 🚀 Project Overview

This project implements a metadata-driven incremental data pipeline using Azure Data Factory (ADF) to move data from an on-premises SQL Server to Azure Data Lake Storage Gen2 (ADLS).

The pipeline processes only new and updated records using a watermark-based approach, improving efficiency and reducing cost.

---

## 🏗️ Architecture

SQL Server (Source)  
↓  
Azure Data Factory (Pipeline)  
↓  
ADLS Gen2 (Parquet Storage)  
↓  
Star Schema (Analytics Layer)

---

## ⚙️ Key Components

### 🔹 Source
- On-prem SQL Server
- Tables: Customers, Orders, Products

### 🔹 Azure Data Factory
- Parent Pipeline (Orchestration)
- Child Pipeline (Incremental Processing)

### 🔹 Watermark Table
Table: `ADF_Watermark_Table`

Stores:
- Table Name
- Watermark Column
- Last Loaded Value

### 🔹 Target
- ADLS Gen2
- Parquet format
- Partitioned storage

---

## 🔁 Incremental Load Logic

1. Read last loaded value  
2. Get MAX value from source  
3. Compare values  
4. Load new data:

```sql
SELECT *
FROM table
WHERE watermark_column > last_loaded_value;
```

5. Update watermark  

---

## ⭐ Data Modeling

### 🌟 Fact Tables
- FactSales
- FactOrders

### 📘 Dimension Tables
- DimCustomer
- DimProduct
- DimDate
- DimRegion

---

## ⚡ Features

- Incremental loading  
- Metadata-driven pipelines  
- Dynamic processing  
- Parquet storage  
- Star schema design  

---

## 🧠 Technologies Used

- Azure Data Factory  
- SQL Server  
- ADLS Gen2  
- Parquet  
- ETL Pipelines  

---

## 🎯 Use Cases

- Data migration to cloud  
- Data lake creation  
- BI reporting (Power BI, Tableau)  

---

## 👨‍💻 Author

Rahul K