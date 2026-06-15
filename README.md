# Flipkart Sales & Product Analytics

An end-to-end Data Analytics project built using **Python, SQL Server, and Tableau** to analyze Flipkart's quick-commerce sales transactions and product catalog. The project covers exploratory data analysis, SQL-based data processing, and interactive dashboard development to uncover sales trends, customer behavior, product performance, and category-level business insights.

<br>

[![Tableau](https://img.shields.io/badge/Tableau-Dashboard-blue?logo=tableau&logoColor=white)](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard)
[![Python](https://img.shields.io/badge/Python-3.8+-yellow?logo=python&logoColor=white)](https://www.python.org/)
[![SQL Server](https://img.shields.io/badge/SQL-Server-CC2927?logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/en-us/sql-server)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)](https://jupyter.org/)

---

## Live Dashboard

**[View on Tableau Public](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard)**

---

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [Project Workflow](#project-workflow)
- [Key Findings](#key-findings)
- [Business Recommendations](#business-recommendations)
- [Dashboard Preview](#dashboard-preview)
- [How to Run](#how-to-run)
- [Author](#author)

---

## Project Overview

This project follows a complete, industry-standard analytics workflow across three phases:

| Phase | Tool | Description |
|---|---|---|
| Exploratory Data Analysis | Python — Pandas, Matplotlib, Seaborn, Plotly | Deep-dive EDA on Sales and Products datasets |
| SQL Analysis | SQL Server (SSMS) | Data cleaning, KPI computation, view creation, dashboard query preparation |
| Dashboard | Tableau Public | Interactive Sales and Product Performance dashboards |

**Business Objective:** Understand Flipkart's sales performance and product catalog structure to identify revenue drivers, customer behavior patterns, discount effectiveness, product portfolio gaps, and actionable growth opportunities.

---

## Dataset

**Source:** [Flipkart Sales Dataset — Kaggle (iyumrahul)](https://www.kaggle.com/datasets/iyumrahul/flipkartsalesdataset)
**Period:** April 1, 2022 – July 10, 2022
**Cities:** Delhi · HR-NCR · Bengaluru · Mumbai

| File | Records | Size | Description |
|---|---|---|---|
| `Sales.csv` | **4,67,06,387 rows (4.67 crore)** | 4.57 GB | Transaction-level sales data |
| `products.csv` | 32,226 rows | 5.38 MB | Product catalog with category hierarchy |

> **Important Note on Dataset Size**
>
> The complete Sales dataset contains **4,67,06,387 rows (4.67 crore records)**, confirmed via SQL Server Import Wizard during loading into SSMS. For the EDA notebooks, a sample of **10,50,000 rows (~2.2% of full data)** was loaded using `nrows=1050000` for efficient local execution. All insights are representative of the full dataset. The **complete 4.67 crore row dataset** was used for all SQL analysis and Tableau dashboard development.

### Product Catalog Summary

| Metric | Value |
|---|---|
| Unique Products | 32,226 |
| Unique Brands | 2,192 |
| Unique Manufacturers | 1,202 |
| L0 Categories | 21 |

### Column Reference

**Sales.csv**

| Column | Description |
|---|---|
| `date_` | Transaction date |
| `city_name` | City where the order was placed |
| `order_id` | Unique order identifier |
| `cart_id` | Cart identifier grouping items in one session |
| `dim_customer_key` | Unique customer identifier |
| `product_id` | Product identifier — join key with products.csv |
| `procured_quantity` | Units ordered |
| `unit_selling_price` | Price per unit charged to the customer |
| `total_discount_amount` | Discount applied to the transaction |
| `total_weighted_landing_price` | Landed cost of the product |

**products.csv**

| Column | Description |
|---|---|
| `product_id` | Unique product identifier — join key with sales |
| `product_name` | Product name |
| `brand_name` | Brand name |
| `manufacturer_name` | Manufacturer name |
| `product_type` | Product type classification |
| `l0_category` | Top-level category |
| `l1_category` | Mid-level category |
| `l2_category` | Sub-category |

---

## Project Structure

```
Flipkart-Sales-Analytics/
│
├── data/                                        # Raw data files (not pushed — too large)
│
├── notebooks/
│   ├── 01_Sales_EDA.ipynb                       # Sales exploratory data analysis
│   └── 02_Product_EDA.ipynb                     # Product catalog exploratory data analysis
│
├── sql/
│   ├── SQL_Exploration.sql                      # Data exploration, cleaning & view creation
│   └── Dashboard_Queries.sql                    # Optimized queries for dashboard KPIs
│
├── tableau/
│   └── Flipkart_Sales_Analytics_Final.twbx      # Tableau workbook
│
├── images/
│   ├── 1_sales_dashboard.png
│   └── 2_product_dashboard.png
│
├── requirements.txt
└── README.md
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python 3 | Core language for EDA and analysis |
| Pandas | Data loading, cleaning, and transformation |
| Matplotlib & Seaborn | Static visualizations across EDA |
| Plotly | Interactive charts for day-of-week analysis |
| SQL Server (SSMS) | Full dataset ingestion, cleaning, view creation, KPI queries |
| Tableau Public | Interactive dashboard creation and publishing |
| Jupyter Notebook | Development environment for EDA |

---

## Project Workflow

### Phase 1 — Exploratory Data Analysis

#### 01_Sales_EDA.ipynb

Complete EDA on the Sales dataset:

- Dataset overview — shape, data types, statistical summary
- Missing value assessment and duplicate detection
- Feature engineering — `Revenue` (Net), `day_of_week`, `month_name`, `date_only`
- Univariate analysis — quantity, selling price, discount, and revenue distributions
- Bivariate analysis — city vs revenue, city vs quantity, discount vs revenue, quantity vs revenue
- Daily order trend analysis

**Six business questions answered through analysis and visualization:**

| # | Business Question |
|---|---|
| Q1 | Which days generated the highest revenue? |
| Q2 | Which city generates the most revenue, orders, quantity sold, and AOV? |
| Q3 | What does customer purchasing behavior look like? (RFM Analysis) |
| Q4 | Does discount influence purchase quantity? |
| Q5 | What is the basket size distribution? (Single-item vs multi-item orders) |
| Q6 | Which days of the week see the highest order activity? |

#### 02_Product_EDA.ipynb

Complete EDA on the Products catalog:

- Dataset overview and feature understanding including L0 → L1 → L2 category hierarchy
- Missing value assessment — `brand_name` (4.46%), `manufacturer_name` (7.5%)
- Univariate analysis — L0 category distribution, top brands, manufacturers, product types, L1 categories
- Bivariate analysis — brand diversity per category, manufacturer diversity per category

**Four business questions answered:**

| # | Business Question |
|---|---|
| Q1 | Which L0 categories have the highest product variety? |
| Q2 | Which brands have the widest category presence? |
| Q3 | Which manufacturers dominate the catalog? |
| Q4 | Which L1 categories have the highest product concentration? |

---

### Phase 2 — SQL Analysis

#### SQL_Exploration.sql

- Initial exploration of `sales` and `products$` tables
- Removed duplicate unnamed index columns from both tables
- Date range validation — confirmed April 1 to July 10, 2022
- Business overview KPI computation
- Created `sales_products` view — INNER JOIN of sales and products on `product_id`
- Category, brand, manufacturer, discount intensity, and gross margin analysis

#### Dashboard_Queries.sql

Structured queries for two dashboards:

**Dashboard 1 — Sales Performance**

| Query | Purpose |
|---|---|
| Business Overview KPIs | Total Orders, Customers, Gross Revenue, Net Revenue, AOV, Discount Rate |
| City-wise Performance | Orders, Units Sold, Revenue, AOV per city |
| Daily Revenue Trend | Orders and revenue grouped by date |
| Revenue Trend by City | Daily revenue split by city for multi-line trend chart |

**Dashboard 2 — Product Performance**

| Query | Purpose |
|---|---|
| Product Catalog KPIs | Unique Products, Categories, Manufacturers, Brands |
| Revenue by L0 Category | Category-level orders, units, and net revenue |
| Top 15 Brands | Brand-level orders, units sold, revenue |
| Top 10 Manufacturers | Manufacturer-level orders, units sold, revenue |
| Top 15 Products | Product-level orders, units sold, revenue |
| Discount Intensity | Discount percentage by category |
| Profit & Gross Margin | Estimated profit and margin % per category |

---

### Phase 3 — Dashboard

Two interactive dashboards published on Tableau Public.

**[View Live on Tableau Public](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard)**

**Dashboard 1 — Sales Performance**
- KPI cards: Total Orders, Total Customers, Gross Revenue, Net Revenue, AOV, Discount Rate
- Daily revenue trend line chart
- City-wise performance table — Orders, Units Sold, Revenue, AOV
- Revenue share by city
- Daily revenue trend by city (multi-line)
- Top 5 highest revenue days

**Dashboard 2 — Product Performance**
- Product catalog KPI cards
- Revenue and units sold by L0 category
- Top 15 brands and Top 10 manufacturers by revenue
- Top 15 products by revenue
- Discount intensity by category
- Gross margin and profit analysis by category

---

## Key Findings

### Sales

- **Delhi** is the strongest market with **₹227.25 Cr. revenue and 4.74M orders** — nearly double HR-NCR, the second-ranked city.
- **HR-NCR (₹113.42 Cr.)** outperformed Bengaluru (₹86.02 Cr.) despite being a smaller region — driven by higher average transaction values.
- **Friday** consistently drives the highest revenue and order volume across all cities — a clear end-of-week demand pattern.
- **Discount Rate is just 0.62%** of gross revenue — discounts play a minimal role, confirming customers buy largely at full price.
- **RFM segmentation** revealed a significant share of customers fall in Hibernating or Lost segments — indicating churn risk and a need for targeted retention.
- **Basket size is predominantly single-item** across all cities — a significant cross-sell and upsell opportunity exists platform-wide.
- Revenue spikes on specific days align with promotional events or monthly salary cycles.

### Products

- **Home & Office** is the largest category with 4,734 products — deepest catalog and highest brand variety.
- **HOT** is the dominant manufacturer with 2,621 products — significant supply concentration risk.
- **Urban Platter** has the widest category presence, operating across 11 L0 categories — strongest cross-category brand.
- **Combo** is the most common product type — indicating a platform-wide bundling and value-pack strategy.
- **Kitchen & Dining Needs** is the largest L1 sub-category by product count.
- **Specials, Paan Corner, and Chicken/Meat/Fish** have thin catalogs — clear catalog expansion opportunities.

---

## Business Recommendations

### Sales

- **Double down on Delhi and HR-NCR** — the two strongest markets deserve prioritized marketing investment and inventory planning.
- **Grow Mumbai and Bengaluru** — both cities show headroom in orders and AOV with targeted acquisition campaigns.
- **Re-evaluate discount strategy** — discounts are not meaningfully driving purchase volume; redirect budget toward loyalty programs for high-value RFM segments.
- **Run Friday and weekend promotions** — the highest traffic period across all cities; flash sales and push notifications will maximize conversion.
- **Retain at-risk customers** — RFM analysis identified significant Hibernating and Lost segments; targeted win-back campaigns can recover lost revenue.
- **Improve cross-sell and bundling** — with most baskets containing a single item, stronger product recommendation logic can meaningfully lift AOV.

### Products

- **Expand Home & Office and Personal Care** — already the largest categories with strong demand; deeper catalog investment is justified.
- **Build up thin categories** — Specials, Paan Corner, and Chicken/Meat/Fish need more SKUs to improve assortment coverage and category revenue.
- **Prioritize multi-category brand partnerships** — Urban Platter, Dabur, and GHD span many categories; strengthening these relationships enables broader cross-category promotions.
- **Diversify the manufacturer base** — HOT accounts for a disproportionate share of the catalog; expanding the supplier base reduces supply chain dependency risk.
- **Improve category navigation** — high-density L1 categories need stronger filtering, search, and recommendations to prevent product discovery drop-off.

---

## Dashboard Preview

### Sales Performance Dashboard

> **10.43M Orders · 1.99M Customers · ₹472.59 Cr. Gross Revenue · ₹469.65 Cr. Net Revenue · AOV ₹450.25 · Discount Rate 0.62%**

![Sales Dashboard](images/sales_dashboard.png)

<br>

### Product Performance Dashboard

> **32,226 Products · 2,192 Brands · 1,202 Manufacturers · 21 Categories**

![Product Dashboard](images/product_dashboard.png)

---

## How to Run

### Prerequisites

```
Python 3.8+
SQL Server / SSMS
Tableau Desktop (to edit) or Tableau Public (to view)
```

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/Vaibhav-code15/Flipkart-Sales-Analytics.git
cd Flipkart-Sales-Analytics
```

**2. Install Python dependencies**
```bash
pip install -r requirements.txt
```

**3. Download the dataset**

Download `Sales.csv` and `products.csv` from [Kaggle](https://www.kaggle.com/datasets/iyumrahul/flipkartsalesdataset) and place them inside the `data/` folder.

**4. Run the EDA notebooks**
```bash
jupyter notebook
```
Open `notebooks/01_Sales_EDA.ipynb` first, followed by `notebooks/02_Product_EDA.ipynb`.

> Update the `pd.read_csv()` file path in each notebook to match your local directory before running.

**5. Run SQL scripts in SSMS**
- Import `Sales.csv` and `products.csv` into SQL Server using the Import and Export Wizard
- Run `sql/SQL_Exploration.sql` first — cleans the data and creates the `sales_products` view
- Run `sql/Dashboard_Queries.sql` — generates all dashboard-ready result sets

**6. View the Dashboard**

Open directly on Tableau Public:
[Flipkart Sales & Product Analytics Dashboard](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard)

Or open `tableau/Flipkart_Sales_Analytics_Final.twbx` in Tableau Desktop and connect to your local SQL Server instance.

---

## Author

**Vaibhav Khandelwal**

B.Tech Computer Science Engineering <br>
Jaypee Institute of Information Technology, Noida

[![GitHub](https://img.shields.io/badge/GitHub-Vaibhav--code15-black?logo=github)](https://github.com/Vaibhav-code15)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Vaibhav%20Khandelwal-blue?logo=linkedin)](https://linkedin.com/in/vaibhav-khandelwal-5a532b28a)
[![Tableau Public](https://img.shields.io/badge/Tableau-Public-orange?logo=tableau)](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/vizzes)

---

*Dataset: [Flipkart Sales Dataset by iyumrahul on Kaggle](https://www.kaggle.com/datasets/iyumrahul/flipkartsalesdataset)*
*This project was built for educational and portfolio purposes.*
