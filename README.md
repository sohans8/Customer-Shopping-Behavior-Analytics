# 🛍️ Customer Shopping Behavior Analytics & Business Intelligence Platform

> **An end-to-end retail data analytics pipeline transforming 3,900 consumer transactional records into strategic retail insights using Python, Advanced SQL, and Microsoft Power BI.**

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15%2B-336791?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Power BI](https://img.shields.io/badge/Power_BI-Desktop-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-ORM%20%26%20Core-D71F00?logo=sqlalchemy&logoColor=white)](https://www.sqlalchemy.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

---

## 📌 Executive Summary

Modern retail organizations operate in hyper-competitive markets where understanding consumer preferences, basket size drivers, promotional efficiency, and loyalty lifecycles directly determines revenue velocity and EBITDA margins.

This project implements an end-to-end **Customer Shopping Behavior Analytics Platform** analyzing **3,900 consumer purchase transactions** across **50 US states** and **4 major retail categories** (Clothing, Accessories, Footwear, and Outerwear).

### Key Business Metrics at a Glance
| Metric | Value | Business Context |
| :--- | :--- | :--- |
| **Total Customers Analyzed** | **3,900** | Unique shoppers across 50 US locations |
| **Total Gross Revenue** | **\$233,081.00** | Cumulative gross merchandise value (GMV) |
| **Average Order Value (AOV)** | **\$59.76** | Uniform basket size distribution (\$20 – \$100) |
| **Average Review Rating** | **3.75 / 5.0** | Baseline customer satisfaction across 25 items |
| **Loyal Customer Segment** | **79.9% (3,116)** | Customers with >10 historical transactions |
| **Active Subscriber Rate** | **27.0% (1,053)** | Significant opportunity for loyalty program conversion |
| **Top Revenue Category** | **Clothing (\$104K+)** | Accounts for 44.5% of total retail sales volume |

---

## 📸 Executive Power BI Dashboard

The project features a business intelligence dashboard developed in **Microsoft Power BI** designed for retail executives and category managers.

![Power BI Customer Behavior Dashboard](docs/images/powerbi_dashboard.png)

### Dashboard Capabilities & Layout
* **Global Executive KPI Cards**: Real-time aggregation of **Total Customers (3.9K)**, **Average Purchase Amount (\$59.76)**, and **Average Review Rating (3.75)**.
* **Interactive Slicers & Cohort Filters**: Dynamic segmentation across **Subscription Status** (Yes/No), **Gender** (Male/Female), **Category** (Accessories, Clothing, Footwear, Outerwear), and **Shipping Type** (Standard, Express, Next Day Air, Free Shipping, 2-Day, Store Pickup).
* **Subscription Breakdown (Donut Chart)**: Visualizing customer distribution between active members (27%) and non-subscribers (73%).
* **Category Performance Analysis**: Comparing gross revenue contribution vs. physical unit sales across product lines.
* **Demographic Revenue Contribution**: Horizontal distribution benchmarking revenue velocity across generational cohorts (*Young Adult*, *Adult*, *Middle-aged*, *Senior*).

---

## 🏗️ System Architecture & Data Flow

```mermaid
flowchart TD
    subgraph Ingestion["1. Data Ingestion & Storage"]
        Raw_CSV["Raw Dataset: customer_shopping_behavior.csv (3,900 Rows)"]
    end

    subgraph Processing["2. Data Cleaning & Feature Engineering"]
        Jupyter_Engine["Jupyter Notebook: Customer_Shopping_Behavior_Analysis.ipynb"]
        Imputation["Category-Based Median Imputation (Review Rating)"]
        Standardization["Snake_case Schema Normalization"]
        Feature_Eng["Feature Engineering: age_group & purchase_frequency_days"]
        Redundancy_Check["Redundancy Removal: Promo Code Deduplication"]
    end

    subgraph Database["3. Multi-RDBMS Storage Layer"]
        SQLAlchemy_Core["SQLAlchemy Core Pipeline"]
        PG_DB[("PostgreSQL: customer Table")]
        MySQL_DB[("MySQL: customer Table")]
        MSSQL_DB[("MS SQL Server: customer Table")]
    end

    subgraph Analytics["4. Analytical Query Engine"]
        SQL_Script["Analytical SQL Engine: customer_behavior_sql_queries.sql"]
        Cohort_Analysis["Customer Loyalty Segmentation (RFM)"]
        Window_Functions["Window Functions: Category Rank & Percentiles"]
        Margin_Audits["Discount Dependency & Shipping Comparisons"]
    end

    subgraph BI["5. Executive Business Intelligence"]
        PBIX["Power BI Desktop: customer_behavior_dashboard.pbix"]
        Exec_Dash["Interactive Executive Dashboard"]
        Strategy_PDF["Strategic Deliverables: PDF & PPTX Reports"]
    end

    Raw_CSV --> Jupyter_Engine
    Jupyter_Engine --> Imputation
    Imputation --> Standardization
    Standardization --> Feature_Eng
    Feature_Eng --> Redundancy_Check
    Redundancy_Check --> SQLAlchemy_Core

    SQLAlchemy_Core --> PG_DB
    SQLAlchemy_Core -.-> MySQL_DB
    SQLAlchemy_Core -.-> MSSQL_DB

    PG_DB --> SQL_Script
    SQL_Script --> Cohort_Analysis
    SQL_Script --> Window_Functions
    SQL_Script --> Margin_Audits

    PG_DB --> PBIX
    Cohort_Analysis --> PBIX
    PBIX --> Exec_Dash
    Exec_Dash --> Strategy_PDF
```

---

## 📁 Repository Structure

```
Customer-Shopping-Behavior-Analytics/
├── customer_shopping_behavior.csv         # Raw transactional dataset (3,900 records, 18 columns)
├── Customer_Shopping_Behavior_Analysis.ipynb # Data cleaning, imputation, feature engineering & DB loader
├── customer_behavior_sql_queries.sql     # 10 production SQL analytics queries with window functions
├── customer_behavior_dashboard.pbix      # Microsoft Power BI interactive dashboard file
├── Customer Shopping Behavior Analysis.pdf # Executive PDF presentation & documentation
├── Customer-Shopping-Behavior-Analysis.pptx# Editable presentation deck with slide visuals
├── README.md                             # Comprehensive technical documentation & portfolio guide
└── docs/
    └── images/                           # Embedded visual assets and SQL query result captures
        ├── dataset_summary_statistics.png
        ├── powerbi_dashboard.png
        ├── sql_customer_segmentation.png
        ├── sql_discount_dependent_products.png
        ├── sql_high_spending_discount_users.png
        ├── sql_repeat_buyers_subscriptions.png
        ├── sql_revenue_by_age_group.png
        ├── sql_revenue_by_gender.png
        ├── sql_shipping_type_comparison.png
        ├── sql_subscribers_vs_non_subscribers.png
        ├── sql_top3_products_per_category.png
        └── sql_top_rated_products.png
```

---

## 📊 Dataset Architecture & Summary Statistics

The dataset captures transactional records from **3,900 consumer orders** across 18 initial dimensions:

| Attribute Name | Data Type | Missing Count | Description / Values |
| :--- | :--- | :--- | :--- |
| `Customer ID` | `INTEGER` | 0 | Unique sequential customer identifier (1 – 3,900) |
| `Age` | `INTEGER` | 0 | Customer age ranging from 18 to 70 years |
| `Gender` | `VARCHAR(10)` | 0 | `Male` (68.0%) or `Female` (32.0%) |
| `Item Purchased` | `VARCHAR(50)` | 0 | 25 distinct retail products (Blouse, Sweater, Jeans, etc.) |
| `Category` | `VARCHAR(50)` | 0 | `Clothing`, `Accessories`, `Footwear`, `Outerwear` |
| `Purchase Amount (USD)`| `INTEGER` | 0 | Transaction value ranging from \$20 to \$100 |
| `Location` | `VARCHAR(50)` | 0 | 50 US States (Montana top state with 96 transactions) |
| `Size` | `VARCHAR(5)` | 0 | `S`, `M` (top size: 1,755), `L`, `XL` |
| `Color` | `VARCHAR(30)` | 0 | 25 unique product colors (Olive, Yellow, Silver, etc.) |
| `Season` | `VARCHAR(10)` | 0 | `Spring` (999), `Fall` (975), `Winter` (971), `Summer` (955) |
| `Review Rating` | `FLOAT` | 37 (0.95%) | Customer rating (2.5 – 5.0). Imputed via category medians |
| `Subscription Status` | `VARCHAR(5)` | 0 | Loyalty program status: `Yes` (27.0%), `No` (73.0%) |
| `Shipping Type` | `VARCHAR(30)` | 0 | 6 shipping fulfillment methods |
| `Discount Applied` | `VARCHAR(5)` | 0 | Flag indicating promotional discount: `Yes` (43%), `No` (57%) |
| `Promo Code Used` | `VARCHAR(5)` | 0 | 100% duplicate of Discount Applied (pruned during ETL) |
| `Previous Purchases` | `INTEGER` | 0 | Historical order count prior to current visit (1 – 50) |
| `Payment Method` | `VARCHAR(30)` | 0 | 6 payment options (PayPal, Credit Card, Cash, etc.) |
| `Frequency of Purchases`| `VARCHAR(30)` | 0 | 7 cadence tiers (Weekly, Fortnightly, Monthly, etc.) |

![Dataset Summary Statistics](docs/images/dataset_summary_statistics.png)

---

## ⚙️ Data Cleaning & Feature Engineering Pipeline

The data preparation pipeline is authored in Python within `Customer_Shopping_Behavior_Analysis.ipynb`:

### 1. Robust Missing Value Imputation
Of the 3,900 records, exactly **37 entries (0.95%)** in `Review Rating` were missing. Rather than dropping records or imputing a global average, a **category-specific median imputation** strategy was executed to preserve intra-category variance:
```python
df['Review Rating'] = df.groupby('Category')['Review Rating'].transform(
    lambda x: x.fillna(x.median())
)
```

### 2. Schema Standardization (Snake Case)
Column headers were cleaned, lowercased, and converted to `snake_case` to ensure compatibility across PostgreSQL, MySQL, and BigQuery:
```python
df.columns = df.columns.str.lower().str.replace(' ', '_')
df = df.rename(columns={'purchase_amount_(usd)': 'purchase_amount'})
```

### 3. Generational Cohort Binning (`age_group`)
Customer age was segmented into four balanced demographic quartiles using Pandas `qcut`:
```python
labels = ['Young Adult', 'Adult', 'Middle-aged', 'Senior']
df['age_group'] = pd.qcut(df['age'], q=4, labels=labels)
```
* **Young Adult**: 18 – 31 years (26.7% of GMV)
* **Adult**: 32 – 44 years (24.0% of GMV)
* **Middle-aged**: 45 – 57 years (25.4% of GMV)
* **Senior**: 58 – 70 years (23.9% of GMV)

### 4. Purchasing Frequency Quantification (`purchase_frequency_days`)
Qualitative frequency strings were converted to continuous day-based intervals to enable statistical modeling:
```python
frequency_mapping = {
    'Weekly': 7,
    'Bi-Weekly': 14,
    'Fortnightly': 14,
    'Monthly': 30,
    'Every 3 Months': 90,
    'Quarterly': 90,
    'Annually': 365
}
df['purchase_frequency_days'] = df['frequency_of_purchases'].map(frequency_mapping)
```

### 5. Deduplication & Normalization
Cross-tabulation verified that `promo_code_used` was 100% collinear with `discount_applied`:
```python
assert (df['discount_applied'] == df['promo_code_used']).all()
df = df.drop(columns=['promo_code_used'])
```

---

## 🔍 Strategic SQL Analytics & Business Insights

The analytical core (`customer_behavior_sql_queries.sql`) contains 10 business intelligence queries executed on PostgreSQL:

---

### Query 1: Revenue Generation by Customer Gender
* **Business Objective**: Understand sales volume and gross revenue split between male and female customer segments.

```sql
SELECT gender, SUM(purchase_amount) AS revenue
FROM customer
GROUP BY gender;
```

![Revenue by Gender](docs/images/sql_revenue_by_gender.png)

> **Key Finding**: Male shoppers represent **\$157,890 (67.7%)** of gross revenue across 2,652 transactions, while female shoppers generated **\$75,191 (32.3%)** across 1,248 transactions. Average order values remain consistent across genders (\$59.54 for Male vs. \$60.25 for Female).

---

### Query 2: High-Spending Discount Users
* **Business Objective**: Identify customers whose basket size exceeded the platform average (\$59.76) despite applying promotional discounts.

```sql
SELECT customer_id, purchase_amount 
FROM customer 
WHERE discount_applied = 'Yes' 
  AND purchase_amount >= (SELECT AVG(purchase_amount) FROM customer);
```

![High Spending Discount Users](docs/images/sql_high_spending_discount_users.png)

> **Key Finding**: Exactly **839 customers** utilized promotional codes yet maintained above-average ticket sizes. This cohort proves that promotional discounting can be leveraged to drive large basket sizes without diluting customer quality.

---

### Query 3: Top 5 Highest-Rated Products
* **Business Objective**: Determine which catalog items enjoy the highest customer satisfaction to feature in marketing campaigns.

```sql
SELECT item_purchased, 
       ROUND(AVG(review_rating::numeric), 2) AS "Average Product Rating"
FROM customer
GROUP BY item_purchased
ORDER BY AVG(review_rating) DESC
LIMIT 5;
```

![Top Rated Products](docs/images/sql_top_rated_products.png)

| Product | Category | Average Review Rating |
| :--- | :--- | :--- |
| **Gloves** | Accessories | **3.86 / 5.0** |
| **Sandals** | Footwear | **3.84 / 5.0** |
| **Boots** | Footwear | **3.82 / 5.0** |
| **Hat** | Accessories | **3.80 / 5.0** |
| **Skirt** | Clothing | **3.78 / 5.0** |

---

### Query 4: Standard vs. Express Shipping Spend Comparison
* **Business Objective**: Compare average transaction size between standard and express logistics tiers.

```sql
SELECT shipping_type, 
       ROUND(AVG(purchase_amount), 2) AS avg_purchase_amount
FROM customer
WHERE shipping_type IN ('Standard', 'Express')
GROUP BY shipping_type;
```

![Shipping Type Comparison](docs/images/sql_shipping_type_comparison.png)

> **Key Finding**: **Express shipping** customers spend an average of **\$60.48**, compared to **\$58.46** for **Standard shipping**. High-intent shoppers demonstrate lower price sensitivity when fast delivery is available.

---

### Query 5: Subscription Monetization Analysis
* **Business Objective**: Evaluate whether subscribers demonstrate higher spending behavior compared to non-subscribers.

```sql
SELECT subscription_status,
       COUNT(customer_id) AS total_customers,
       ROUND(AVG(purchase_amount), 2) AS avg_spend,
       ROUND(SUM(purchase_amount), 2) AS total_revenue
FROM customer
GROUP BY subscription_status
ORDER BY total_revenue DESC, avg_spend DESC;
```

![Subscribers vs Non-Subscribers](docs/images/sql_subscribers_vs_non_subscribers.png)

| Subscription Status | Customer Count | Percentage | Average Spend | Total Revenue |
| :--- | :--- | :--- | :--- | :--- |
| **Non-Subscribers** | 2,847 | 73.0% | **\$59.87** | **\$170,436.00** |
| **Active Subscribers** | 1,053 | 27.0% | **\$59.49** | **\$62,645.00** |

> **Key Finding**: Average spend between subscribers (\$59.49) and non-subscribers (\$59.87) is statistically equivalent. The subscription tier is currently functioning as an access pass rather than a premium monetization lever.

---

### Query 6: Discount-Dependent Products (Margin Vulnerability)
* **Business Objective**: Detect items with the highest reliance on discounting to prevent margin erosion.

```sql
SELECT item_purchased,
       ROUND(100.0 * SUM(CASE WHEN discount_applied = 'Yes' THEN 1 ELSE 0 END) / COUNT(*), 2) AS discount_rate
FROM customer
GROUP BY item_purchased
ORDER BY discount_rate DESC
LIMIT 5;
```

![Discount Dependent Products](docs/images/sql_discount_dependent_products.png)

> **Key Finding**: **Hats (50.00%)**, **Sneakers (49.66%)**, **Coats (49.07%)**, **Sweaters (48.17%)**, and **Pants (47.37%)** are heavily discounted. Half of all purchases in these categories occur under promotions, signaling potential over-reliance on discounts.

---

### Query 7: Customer Loyalty Segmentation (RFM Analysis)
* **Business Objective**: Segment customer base into New, Returning, and Loyal tiers based on prior transaction counts.

```sql
WITH customer_type AS (
    SELECT customer_id, previous_purchases,
           CASE 
               WHEN previous_purchases = 1 THEN 'New'
               WHEN previous_purchases BETWEEN 2 AND 10 THEN 'Returning'
               ELSE 'Loyal'
           END AS customer_segment
    FROM customer
)
SELECT customer_segment, 
       COUNT(*) AS "Number of Customers"
FROM customer_type
GROUP BY customer_segment
ORDER BY "Number of Customers" DESC;
```

![Customer Segmentation](docs/images/sql_customer_segmentation.png)

| Segment | Historical Purchases | Customer Count | Share (%) | Strategic Mandate |
| :--- | :--- | :--- | :--- | :--- |
| **Loyal** | > 10 purchases | **3,116** | **79.9%** | Retention, VIP access, and premium bundles |
| **Returning**| 2 – 10 purchases | **701** | **18.0%** | Habit formation via personalized triggers |
| **New** | 1 purchase | **83** | **2.1%** | 2nd-purchase conversion onboarding flows |

---

### Query 8: Top 3 Most Purchased Products per Category
* **Business Objective**: Rank leading items in each retail department using SQL analytical window functions (`ROW_NUMBER`).

```sql
WITH item_counts AS (
    SELECT category,
           item_purchased,
           COUNT(customer_id) AS total_orders,
           ROW_NUMBER() OVER (PARTITION BY category ORDER BY COUNT(customer_id) DESC) AS item_rank
    FROM customer
    GROUP BY category, item_purchased
)
SELECT item_rank, category, item_purchased, total_orders
FROM item_counts
WHERE item_rank <= 3;
```

![Top 3 Products per Category](docs/images/sql_top3_products_per_category.png)

| Category | Rank 1 Product (Orders) | Rank 2 Product (Orders) | Rank 3 Product (Orders) |
| :--- | :--- | :--- | :--- |
| **Clothing** | Blouse (171) | Pants (171) | Shirt (169) |
| **Accessories** | Jewelry (171) | Sunglasses (161) | Belt (161) |
| **Footwear** | Sandals (160) | Shoes (150) | Sneakers (145) |
| **Outerwear** | Jacket (163) | Coat (161) | *(Category holds 2 items)* |

---

### Query 9: Repeat Buyers vs. Subscription Propensity
* **Business Objective**: Measure how many repeat shoppers (>5 historical orders) have enrolled in the subscription tier.

```sql
SELECT subscription_status,
       COUNT(customer_id) AS repeat_buyers
FROM customer
WHERE previous_purchases > 5
GROUP BY subscription_status;
```

![Repeat Buyers and Subscriptions](docs/images/sql_repeat_buyers_subscriptions.png)

> **Key Finding**: Among customers with more than 5 historical orders, **2,518 are non-subscribers** while only **958 are subscribers**. Over **72.4%** of repeat customers have not converted to subscribers, representing the single largest growth opportunity in the business.

---

### Query 10: Generational Revenue Contribution
* **Business Objective**: Quantify top-line revenue generated by customer age brackets.

```sql
SELECT age_group,
       SUM(purchase_amount) AS total_revenue
FROM customer
GROUP BY age_group
ORDER BY total_revenue DESC;
```

![Revenue by Age Group](docs/images/sql_revenue_by_age_group.png)

| Age Group | Age Range | Total Revenue | GMV Contribution (%) |
| :--- | :--- | :--- | :--- |
| **Young Adult** | 18 – 31 | **\$62,143.00** | **26.7%** |
| **Middle-aged** | 45 – 57 | **\$59,197.00** | **25.4%** |
| **Adult** | 32 – 44 | **\$55,978.00** | **24.0%** |
| **Senior** | 58 – 70 | **\$55,763.00** | **23.9%** |

---

## 💡 Strategic Business Recommendations

Based on the quantitative findings across Python and SQL analytics:

1. **Monetize the Repeat Buyer Funnel**:
   * **Problem**: 2,518 frequent buyers (>5 purchases) are not enrolled in the subscription tier.
   * **Action**: Launch a targeted in-cart conversion campaign offering a free first month or shipping credits to repeat buyers at checkout.

2. **Restructure Subscription Value Proposition**:
   * **Problem**: Subscribers spend \$59.49 per order compared to \$59.87 for non-subscribers.
   * **Action**: Introduce subscriber-only tiered volume discounts (e.g., 10% off orders over \$75) to increase subscriber basket size beyond non-subscriber levels.

3. **Protect Margins on Discount-Sensitive Core Items**:
   * **Problem**: 50% of hats and sneakers are purchased under promotional discounts.
   * **Action**: Replace standalone item discounts with cross-category bundling (e.g., "Buy a Jacket, get a Hat for 30% off") to safeguard baseline margins.

4. **Capitalize on Express Shipping Propensity**:
   * **Problem**: Express delivery customers generate higher order values (\$60.48).
   * **Action**: Offer free Express Shipping thresholds at \$75+ to incentivize basket building.

---

## 🛠️ Installation & Setup Guide

### 1. Prerequisites
Ensure you have the following installed:
* [Python 3.10+](https://www.python.org/downloads/)
* [PostgreSQL 14+](https://www.postgresql.org/download/) / pgAdmin 4
* [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Windows)
* Git

### 2. Clone the Repository
```bash
git clone https://github.com/sohans8/Customer-Shopping-Behavior-Analytics.git
cd Customer-Shopping-Behavior-Analytics
```

### 3. Setup Python Virtual Environment
```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
```

### 4. Install Dependencies
```bash
pip install pandas numpy sqlalchemy psycopg2-binary jupyter
```

---

## 🗄️ Database Ingestion Guide

The Jupyter Notebook supports automated table creation and data streaming to multiple relational database engines:

### Option A: PostgreSQL (Default)
1. Open pgAdmin 4 and execute:
   ```sql
   CREATE DATABASE customer_behavior;
   ```
2. In `Customer_Shopping_Behavior_Analysis.ipynb`, configure your credentials:
   ```python
   from sqlalchemy import create_engine

   username = "postgres"
   password = "your_password"
   host = "localhost"
   port = "5432"
   database = "customer_behavior"

   engine = create_engine(f"postgresql+psycopg2://{username}:{password}@{host}:{port}/{database}")
   df.to_sql("customer", engine, if_exists="replace", index=False)
   ```

### Option B: MySQL
```bash
pip install pymysql
```
```python
from sqlalchemy import create_engine
engine = create_engine("mysql+pymysql://root:your_password@localhost:3306/customer_behavior")
df.to_sql("customer", engine, if_exists="replace", index=False)
```

### Option C: Microsoft SQL Server
```bash
pip install pyodbc
```
```python
from sqlalchemy import create_engine
from urllib.parse import quote_plus

driver = quote_plus("ODBC Driver 17 for SQL Server")
engine = create_engine(f"mssql+pyodbc://sa:your_password@localhost:1433/customer_behavior?driver={driver}")
df.to_sql("customer", engine, if_exists="replace", index=False)
```

---

## 📈 Power BI Dashboard Setup

1. Launch **Microsoft Power BI Desktop**.
2. Open `customer_behavior_dashboard.pbix`.
3. If connecting to your local PostgreSQL instance:
   * Navigate to **Transform Data** > **Data Source Settings**.
   * Update the Server to `localhost:5432` and Database to `customer_behavior`.
   * Click **Apply Changes** to refresh visuals with live data.

---

## 👤 Author & Connect

**Sohan Shetty**
* **GitHub**: [@sohans8](https://github.com/sohans8)
* **Project Repository**: [Customer-Shopping-Behavior-Analytics](https://github.com/sohans8/Customer-Shopping-Behavior-Analytics)

---

## 📄 License
This project is open-source and licensed under the [MIT License](LICENSE).
