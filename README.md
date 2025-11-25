# 🛒 Retail 360: End-to-End Customer & Product Analytics

### 🚀 Project Overview
A full-stack data analytics solution designed to transform raw retail transaction logs into actionable business insights. This project demonstrates an **end-to-end data pipeline** from Python-based ETL and feature engineering to SQL warehousing and advanced Power BI visualization.

**The Business Problem:**
The stakeholder needed to identify high-value customers (VIPs) and optimize the product portfolio, but the data was locked in flat files without demographic context.

**The Solution:**
I built a system to segment customers using **RFM Analysis** (Recency, Frequency, Monetary) and identify 80/20 product performance using **Pareto Analysis**.

---

### 🏗️ Architecture & Tech Stack

**1. Python (Data Engineering & Science)**
* **Libraries:** `pandas`, `numpy`, `sqlalchemy`, `faker`.
* **ETL Pipeline:** Extracted raw transaction data, cleaned null values/returns, and performed **Normalization** to split data into Dimension and Fact tables.
* **Advanced Logic:** Implemented an **RFM Algorithm** to score and segment customers (e.g., 'Champions', 'At Risk', 'Hibernating') before loading to the DB.
* **Data Enrichment:** Used `Faker` to generate synthetic demographic data (Names, Emails, Region) to simulate a complete CRM environment.

**2. MySQL (Data Warehousing)**
* Designed a **Star Schema** data model optimized for reporting.
* **Fact Table:** `fact_sales` (1M+ rows).
* **Dimension Tables:** `dim_customer`, `dim_product`, `dim_date`.
* Enforced data integrity and type constraints.

**3. Power BI (Business Intelligence)**
* **Data Modeling:** Established One-to-Many relationships with a dedicated Date Table.
* **DAX Mastery:** Created complex measures including **Time Intelligence** (YoY Growth), **Pareto Analysis** (Cumulative % logic), and Dynamic Titles.
* **UX/UI:** Implemented Report Page Tooltips for "Mini-Dashboards" on hover and Drill-through capabilities.

---

### 📊 Key Insights & Dashboards

#### 1. Customer Intelligence (RFM Segmentation)
* **Objective:** Who are our best customers?
* **Feature:** A Dynamic Scatter Plot (Recency vs. Monetary) that clusters customers into segments.
* **Insight:** "Champions" represent only 5% of the user base but drive 40% of total revenue.
* **Action:** Marketing team can export the "At Risk" list directly from the table visual for retargeting campaigns.

#### 2. Product Portfolio (Pareto & Positioning)
* **Objective:** Which products drive the business?
* **Feature:** A Pareto Chart (80/20 Rule) utilizing advanced DAX window functions.
* **Feature:** A "Product Positioning" Matrix (Price vs. Volume) identifying "Cash Cows" vs. "Dead Stock."
* **Insight:** Identified the bottom 30% of inventory that generates <1% of revenue (candidates for clearance).

---

### 💻 How to Run This Project

**Prerequisites:**
* Python 3.x
* MySQL Server (Local or Cloud)
* Power BI Desktop

**Step 1: The ETL Pipeline**
Run the Python script `etl_pipeline.py` to process the raw CSV and populate your MySQL database.
```bash
pip install pandas sqlalchemy mysql-connector-python faker
python etl_pipeline.py
