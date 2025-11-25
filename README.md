# 🛒 Retail 360 Intelligence: End-to-End Analytics

![Python](https://img.shields.io/badge/Python-3.9-blue)
![SQL](https://img.shields.io/badge/MySQL-8.0-orange)
![Power BI](https://img.shields.io/badge/Power_BI-Desktop-yellow)

**A full-stack business intelligence solution transforming raw transaction logs into actionable customer and product insights.**

---

## 🚀 Project Overview

The goal of this project was to move beyond basic reporting and build a scalable analytics engine. Instead of loading flat CSV files directly into a visualization tool, I architected a modern data pipeline that handles data cleaning, enrichment, and modeling *before* visualization.

**The Business Problem:**
A retail stakeholder needed to identify "At Risk" VIP customers and optimize their inventory, but their data lacked demographic context and was trapped in unstructured transaction logs.

**The Solution:**
I built an end-to-end system that:
1.  **Extracts** raw sales data and enriches it with synthetic demographics using **Python**.
2.  **Segments** customers using an **RFM (Recency, Frequency, Monetary)** algorithm.
3.  **Loads** data into a **MySQL Star Schema** warehouse.
4.  **Visualizes** performance in **Power BI** using advanced DAX for Pareto and Churn analysis.

---

## 📊 Dashboards & Insights

### 1. Customer Intelligence
*Focus: Segmentation & Retention*
![Customer Dashboard](./assets/customer_dashboard.png)
* **RFM Segmentation:** Customers are algorithmically clustered into "Champions", "Loyal", "Standard", and "At Risk".
* **Key Insight:** "Champions" represent only 5% of the customer base but drive 40% of total revenue.
* **Action:** The marketing team can export the "At Risk" list directly from the table visual for retargeting.

### 2. Product Portfolio
*Focus: Inventory Optimization*
![Product Dashboard](./assets/product_pareto.png)
* **Pareto Analysis (80/20):** Identifying the top 20% of products that drive 80% of revenue.
* **Product Positioning:** A Scatter Plot (Price vs. Volume) identifies "Cash Cows" vs. "Dead Stock".
* **Key Insight:** The bottom 30% of inventory contributes less than 1% to the bottom line and is a candidate for clearance.

---

## 🏗️ Technical Architecture

```mermaid
graph LR
A[Raw CSV Data] -- Python Pandas --> B(ETL & Cleaning)
B -- Faker Library --> C{Data Enrichment}
C -- RFM Algorithm --> D[MySQL Data Warehouse]

D -- Star Schema --> E[Power BI]
