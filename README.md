# data-warehouse-project-sql
This repository showcases how two different operational systems can be integrated into a single analytics-ready warehouse using SQL. The project walks through the full lifecycle: ingestion, cleaning, standardization, modeling, and building analytical views.

---

## 🌐 Project Summary

The goal of this project is to merge **CRM** (sales, products, customers) and **ERP** (extra product and customer attributes) into a unified data warehouse.
The final model supports clean **dimension tables**, a **sales fact table**, and an optimized schema for reporting.

This project demonstrates skills in:

* SQL development
* Data integration
* Star schema design
* ETL logic
* Medallion architecture

---

## 🧱 Data Architecture

The warehouse is designed using a Medallion-inspired layout:

### **Bronze Layer**

* Raw ingestion of CRM and ERP tables
* Minimal transformations
* Mirrors source systems

### **Silver Layer**

* Standardization of fields
* Cleaning invalid data (dates, nulls, mismatches)
* Joining CRM and ERP data
* Creation of:

  * `dim_customer`
  * `dim_product`
  * `fact_sales`

### **Gold Layer**

* Final analytical views
* Ready for dashboards and BI tools

---

## 🔗 Source System Overview

### **CRM**

* `crm_sales_details`: order-level transactions
* `crm_prd_info`: core product details
* `crm_cust_info`: customer master data

### **ERP**

* `erp_px_cat_g1v2`: extended product attributes
* `erp_cust_az12`: additional customer info
* `erp_loc_a101`: customer country/location

A key highlight of this project is the logic to match CRM product keys with ERP product IDs using a **first 5-character mapping**.

---

## 📊 Data Model

The final star schema includes:

### **Dimensions**

**dim_customer**
Merged from CRM + ERP, including demographic cleanup and country mapping.

**dim_product**
Built by enriching CRM product data with ERP product category and metadata.

### **Fact Table**

**fact_sales**
Sales transactions joined with customer + product dimensions, containing:

* Order number
* Product key
* Customer key
* Dates
* Quantity
* Revenue

<img width="661" height="521" alt="Untitled Diagram drawio" src="https://github.com/user-attachments/assets/b6aeee85-f5da-4900-b603-2354952d058c" />

---

## 📁 Repository Structure

```
data-warehouse-project-sql/
│
├── bronze/                 # Raw CRM + ERP ingestion scripts
├── silver/                 # Dimension and fact transformations
├── gold/                   # Final analytical views
│
├── docs/                   # ERD, mappings, and architecture diagrams
│
└── README.md               # Project overview
```

---

## ⚙️ Key Transformations

Some of the core logic implemented in SQL:

* Cleaning incorrectly formatted dates in sales
* Standardizing gender, marital status, and country fields
* Matching CRM and ERP products (first 5 characters)
* Deduplicating customer records
* Normalizing category fields
* Creating surrogate keys where needed

These transformations ensure all data is consistent, analysis-friendly, and BI-ready.

---

## 🛠️ Tools Used

* SQL Server
* SSMS
* GitHub
* Draw.io (for diagrams)

