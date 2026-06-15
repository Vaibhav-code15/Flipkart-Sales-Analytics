# Flipkart Sales & Product Analytics

An end-to-end Data Analytics project built using **Python, SQL Server, and Tableau** to analyze Flipkart sales transactions and product catalog data. The project focuses on customer purchasing behavior, city-wise sales performance, product portfolio analysis, and business insights through interactive dashboards.

---

## Project Overview

This project follows a complete analytics workflow:

- Exploratory Data Analysis (EDA) using Python
- Data Cleaning & Business Analysis using SQL Server
- Interactive Dashboard Development using Tableau

The objective was to uncover sales trends, customer behavior patterns, product performance, and category-level insights that can support data-driven business decisions.

---

## Dataset

### Sales Dataset

- Original Dataset Size: **46.7 Million Rows (4.67 Crore Records)**
- Analysis Period: **April 2022 – July 2022**
- Cities Covered:
  - Delhi
  - HR-NCR
  - Bengaluru
  - Mumbai

### Product Dataset

- Unique Products: **32,226**
- Unique Brands: **2,192**
- Unique Manufacturers: **1,202**
- Product Categories: **21**

### Important Note

The original sales dataset contains **46.7 million transaction records**.

Due to local hardware limitations, a representative sample of **1.05 million rows** was used for Python-based Exploratory Data Analysis.

However, the **complete dataset (46.7 million rows)** was imported into SQL Server and used for all SQL analysis and Tableau dashboard development.

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SQL Server (SSMS)
- Tableau Public
- Jupyter Notebook

---

## Project Structure

```text
Flipkart-Sales-Analytics
│
├── data/
│
├── notebooks/
│   ├── 01_Sales_EDA.ipynb
│   └── 02_Product_EDA.ipynb
│
├── sql/
│   ├── SQL_Exploration.sql
│   └── Dashboard_Queries.sql
│
├── tableau/
│   └── Flipkart_Sales_Analytics_Final.twbx
│
├── images/
│   ├── 1_sales_dashboard.png
│   └── 2_product_dashboard.png
│
├── requirements.txt
└── README.md
```

---

## Exploratory Data Analysis

### Sales EDA

Analysis performed on:

- Revenue Distribution
- Order Volume Analysis
- Customer Analysis
- City-wise Revenue Performance
- Discount Impact Analysis
- Basket Size Analysis
- Daily Revenue Trends
- Day-of-Week Sales Patterns
- RFM Customer Segmentation

### Product EDA

Analysis performed on:

- Category Distribution
- Product Type Analysis
- Brand Analysis
- Manufacturer Analysis
- Category Hierarchy Analysis
- Product Variety Distribution
- Brand & Manufacturer Concentration

---

## SQL Analysis

The SQL phase focused on:

- Data Cleaning & Validation
- KPI Calculation
- Revenue Analysis
- Product Performance Analysis
- Brand Analysis
- Manufacturer Analysis
- Category Analysis
- Profit & Margin Analysis
- Dashboard Query Preparation

A consolidated analytical view was created by joining sales and product datasets using **product_id**.

---

## Tableau Dashboards

### Dashboard 1 – Sales Performance Dashboard

Features:

- Total Orders
- Total Customers
- Gross Revenue
- Net Revenue
- Average Order Value
- Discount Rate
- Revenue by City
- Orders by City
- Daily Revenue Trend
- Revenue Trend by City

### Dashboard 2 – Product Performance Dashboard

Features:

- Unique Products
- Unique Brands
- Unique Manufacturers
- Product Categories
- Revenue by Category
- Top Brands by Revenue
- Top Manufacturers by Revenue
- Top Products by Revenue
- Profit Analysis
- Gross Margin Analysis

---

## Dashboard Preview

### Sales Performance Dashboard

![Sales Dashboard](images/1_sales_dashboard.png)

### Product Performance Dashboard

![Product Dashboard](images/2_product_dashboard.png)

---

## Live Dashboard

View the interactive Tableau Dashboard:

🔗 https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard

---

## Key Insights

### Sales Insights

- Delhi generated the highest revenue and order volume.
- HR-NCR emerged as the second strongest market.
- Revenue showed a consistent upward trend during the analysis period.
- Most customer orders contained a single item, indicating cross-selling opportunities.
- Discount rates had limited impact on purchase quantity.
- Weekend periods contributed significantly to sales performance.

### Product Insights

- Home & Office contained the largest product variety.
- HOT emerged as the highest revenue-generating manufacturer.
- Revenue was concentrated among a relatively small group of brands.
- Several categories had limited product representation and expansion potential.
- Product portfolio concentration highlighted opportunities for assortment optimization.

---

## Skills Demonstrated

- Data Cleaning
- Exploratory Data Analysis (EDA)
- Statistical Analysis
- SQL Query Writing
- Joins & Views
- Business Intelligence
- Dashboard Development
- KPI Design
- Data Visualization
- Data Storytelling

---

## Author

### Vaibhav Khandelwal

B.Tech Computer Science Engineering  
Jaypee Institute of Information Technology, Noida

### GitHub

🔗 https://github.com/Vaibhav-code15

### LinkedIn

🔗 https://linkedin.com/in/vaibhav-khandelwal-5a532b28a

### Tableau Public

🔗 https://public.tableau.com/app/profile/vaibhav.khandelwal6292

---

## Dataset Source

Flipkart Sales Dataset (Kaggle)

This project was created for educational and portfolio purposes.
