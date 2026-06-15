# Flipkart Sales & Product Analytics

An end-to-end data analytics project on Flipkart's quick-commerce sales data covering exploratory data analysis, SQL-based data processing, and interactive dashboard creation.

[![Tableau Dashboard](https://img.shields.io/badge/Tableau-Dashboard-blue?logo=tableau)](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard)
[![Python](https://img.shields.io/badge/Python-3.8+-yellow?logo=python)](https://www.python.org/)
[![SQL Server](https://img.shields.io/badge/SQL-Server-red?logo=microsoftsqlserver)](https://www.microsoft.com/en-us/sql-server)

---

## 📊 Live Dashboard

👉 **[View on Tableau Public](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard)**

---

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [Project Workflow](#project-workflow)
- [Key Findings](#key-findings)
- [Business Recommendations](#business-recommendations)
- [How to Run](#how-to-run)
- [Author](#author)

---

## Project Overview

The objective of this project is to understand Flipkart's sales performance and product catalog structure by analyzing customer purchasing behavior, city-wise demand, pricing patterns, discount strategies, and product distribution across a 3-month period (April – July 2022).

The project is structured across three phases:

| Phase | Tool | Description |
|---|---|---|
| Exploratory Data Analysis | Python | Deep-dive EDA on Sales and Products datasets |
| SQL Analysis | SQL Server (SSMS) | Data cleaning, view creation, and dashboard query preparation |
| Dashboard | Tableau Public | Interactive Sales and Product Performance dashboards |

---

## Dataset

**Source:** [Flipkart Sales Dataset — Kaggle (iyumrahul)](https://www.kaggle.com/datasets/iyumrahul/flipkartsalesdataset)

| File | Records | Size | Description |
|---|---|---|---|
| `Sales.csv` | 4,67,06,387 rows | 4.57 GB | Transaction-level sales data |
| `products.csv` | 32,226 rows | 5.38 MB | Product catalog with category hierarchy |

> **📌 Note on Sampling:** The complete Sales dataset contains **4,67,06,387 rows (≈ 4.67 crore records)**, confirmed via SQL Server Import Wizard during data loading into SSMS. For the EDA notebooks, a sample of **10,50,000 rows (~2.2% of full data)** was loaded using `nrows=1050000` for efficient local execution. All insights are representative of the full dataset. The complete dataset was used for SQL analysis and dashboard creation.

**Period:** April 1, 2022 – July 10, 2022 &nbsp;|&nbsp; **Cities:** Delhi · Bengaluru · Mumbai · HR-NCR

### Sales.csv

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

### products.csv

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
├── data/                            # Raw data files (not pushed — too large)
│   ├── Sales.csv
│   └── raw/
│       └── products.csv
│
├── images/                          # Dashboard screenshots and visuals
│
├── notebooks/
│   ├── 01_Sales_EDA.ipynb           # Sales exploratory data analysis
│   └── 02_Product_EDA.ipynb         # Product catalog exploratory data analysis
│
├── sql/
│   ├── SQL_Exploration.sql          # Data exploration, cleaning & view creation
│   └── Dashboard_queries.sql        # Optimized queries for dashboard KPIs
│
├── tableau/                         # Tableau workbook file
│
├── requirements.txt                 # Python dependencies
└── README.md
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python 3 | EDA, data manipulation, visualization |
| Pandas | Data loading, cleaning, transformation |
| Matplotlib & Seaborn | Static visualizations |
| Plotly | Interactive charts |
| SQL Server (SSMS) | Data ingestion, cleaning, view creation, querying |
| Tableau Public | Interactive dashboard creation and publishing |

---

## Project Workflow

### Phase 1 — Exploratory Data Analysis

#### 01_Sales_EDA.ipynb

Complete EDA on the Sales dataset:

- Dataset overview — shape, dtypes, statistical summary
- Missing value assessment and duplicate detection
- Feature engineering — `Revenue`, `day_of_week`, `month_name`, `date_only`
- Univariate analysis — quantity, selling price, discount, and revenue distributions
- Bivariate analysis — city vs revenue, city vs quantity, discount vs revenue, quantity vs revenue
- Daily order trend analysis

**Six business questions answered:**

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

- Dataset overview and feature understanding with category hierarchy (L0 → L1 → L2)
- Missing value assessment — `brand_name` (4.46%), `manufacturer_name` (7.5%)
- Univariate analysis — L0 category distribution, top brands, top manufacturers, product types, L1 categories
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
- Date range validation
- Business overview metric computation
- Created `sales_products` view — inner join of sales and products on `product_id`
- Category-level revenue, brand revenue, manufacturer revenue, discount intensity, and margin analysis

#### Dashboard_queries.sql

Queries structured for two dashboards:

**Dashboard 1 — Sales Performance**
1. Business overview KPIs — Total Orders, Total Customers, Gross Revenue, Net Revenue, AOV, Discount Rate
2. City-wise performance — Orders, Units Sold, Revenue, AOV
3. Daily orders and revenue trend
4. Daily revenue trend by city

**Dashboard 2 — Product Performance**
1. Product catalog KPIs — Unique Products, Categories, Manufacturers, Brands
2. Revenue by L0 category
3. Top 15 brands by revenue
4. Top 10 manufacturers by revenue
5. Top 15 products by revenue
6. Discount intensity by category
7. Profit and gross margin analysis by category

---

### Phase 3 — Dashboard

Two interactive dashboards published on Tableau Public.

👉 **[View Live Dashboard](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard)**

**Dashboard 1 — Sales Performance**
- KPI cards: Total Orders, Total Customers, Gross Revenue, Net Revenue, AOV, Discount Rate
- Daily revenue trend with city breakdown
- City-wise performance table and revenue share donut
- Top 5 highest revenue days
- Day-of-week order activity pattern

**Dashboard 2 — Product Performance**
- Product catalog KPI cards
- Revenue by L0 category
- Top brands and manufacturers by revenue
- Discount intensity by category
- Gross margin analysis by category

---

## Key Findings

### Sales

- **Delhi** is the strongest market, leading across revenue, orders, quantity sold, and AOV.
- **HR-NCR** outperformed Bengaluru in overall sales performance despite being a smaller region.
- **Friday** consistently drives the highest revenue and order volume — end-of-week demand is a strong pattern across all cities.
- **Discounts showed limited influence** on purchase quantity — the majority of transactions had zero discount applied.
- **RFM segmentation** revealed a significant share of customers fall in Hibernating or Lost segments, signaling churn risk.
- **Basket size** is predominantly single-item — a large cross-sell and upsell opportunity exists.
- Revenue spikes on specific days are likely driven by promotional events or salary cycles.

### Products

- **Home & Office** is the largest category with 4,734 products — highest catalog depth and brand variety.
- **HOT** is the dominant manufacturer with 2,621 products — significant supply concentration risk.
- **Urban Platter** has the widest category presence, operating across 11 L0 categories.
- **Combo** is the most common product type, indicating a platform-wide bundling strategy.
- **Kitchen & Dining Needs** is the largest L1 sub-category by product count.
- Categories like Specials, Paan Corner, and Chicken, Meat & Fish have thin catalogs with limited SKUs.

---

## Business Recommendations

### Sales
- Focus marketing investment on **Delhi and HR-NCR** — the strongest performing markets.
- Increase customer acquisition in **Mumbai and Bengaluru** where growth headroom exists.
- **Re-evaluate discount strategy** — discounts are not strongly driving volume; a profitability-first approach is recommended.
- Run **Friday and weekend promotions** to capitalize on peak demand patterns.
- Launch **targeted retention campaigns** for At Risk and Hibernating customer segments from RFM analysis.
- Improve **cross-sell and product recommendation** systems to increase basket size beyond single-item orders.

### Products
- Strengthen high-variety categories — **Home & Office** and **Personal Care** should be prioritized for further catalog expansion.
- Expand underrepresented categories — **Specials, Paan Corner, Chicken/Meat/Fish** need more SKUs.
- Prioritize partnerships with multi-category brands — **Urban Platter, Dabur, GHD** for cross-category campaigns.
- **Diversify the supplier base** to reduce dependency on HOT and a small group of manufacturers.
- Improve **filtering and search** for high-density L1 categories to enhance product discoverability.

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
git clone https://github.com/yourusername/Flipkart-Sales-Analytics.git
cd Flipkart-Sales-Analytics
```

**2. Install Python dependencies**
```bash
pip install -r requirements.txt
```

**3. Download the dataset**

Download `Sales.csv` and `products.csv` from [Kaggle](https://www.kaggle.com/datasets/iyumrahul/flipkartsalesdataset) and place them inside the `data/` folder.

**4. Run the notebooks**
```bash
jupyter notebook
```
Open `notebooks/01_Sales_EDA.ipynb` first, then `notebooks/02_Product_EDA.ipynb`.

> Update the `pd.read_csv()` file path in each notebook to match your local directory before running.

**5. Run SQL scripts in SSMS**
- Import `Sales.csv` and `products.csv` into SQL Server using the Import and Export Wizard
- Run `sql/SQL_Exploration.sql` first — this cleans the data and creates the `sales_products` view
- Run `sql/Dashboard_queries.sql` to generate all dashboard-ready result sets

**6. View the dashboard**

Open directly on Tableau Public: [Flipkart Sales & Product Analytics Dashboard](https://public.tableau.com/app/profile/vaibhav.khandelwal6292/viz/FlipkartSalesProductAnalyticsDashboard/SalesDashboard)

Or open the `.twbx` file inside the `tableau/` folder in Tableau Desktop and connect to your local SQL Server instance.

---

## Author

**Vaibhav Khandelwal**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/yourprofile)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/yourusername)
[![Tableau](https://img.shields.io/badge/Tableau-Public-orange?logo=tableau)](https://public.tableau.com/app/profile/vaibhav.khandelwal6292)

---

*Dataset: [Flipkart Sales Dataset by iyumrahul on Kaggle](https://www.kaggle.com/datasets/iyumrahul/flipkartsalesdataset)*
