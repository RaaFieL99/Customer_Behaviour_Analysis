# 🛍️ Customer Shopping Behavior Analysis

An end-to-end data analytics project exploring customer shopping patterns using transactional data from **3,900 purchases**. The project combines **Python (Pandas)** for data cleaning and feature engineering, **PostgreSQL** for structured business-question analysis, and **Power BI** for interactive visualization — culminating in actionable business recommendations.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset Summary](#-dataset-summary)
- [Tech Stack](#-tech-stack)
- [Project Workflow](#-project-workflow)
- [Data Cleaning & Feature Engineering](#-data-cleaning--feature-engineering-python)
- [SQL Analysis](#-sql-analysis-postgresql)
- [Power BI Dashboard](#-power-bi-dashboard)
- [Key Insights](#-key-insights)
- [Business Recommendations](#-business-recommendations)
- [Repository Structure](#-repository-structure)
- [How to Reproduce](#-how-to-reproduce)
- [Contact](#-contact)

---

## 📖 Project Overview

This project analyzes customer shopping behavior to uncover insights into **spending patterns, customer segments, product preferences, and subscription behavior**, with the goal of guiding strategic business decisions such as marketing targeting, discount policy, and customer retention strategy.

The analysis moves through three stages:
1. **Data preparation & feature engineering** in Python
2. **Business-question-driven analysis** in SQL (PostgreSQL)
3. **Visual storytelling** via an interactive Power BI dashboard

---

## 📊 Dataset Summary

| Attribute | Details |
|---|---|
| Rows | 3,900 |
| Columns | 18 |
| Missing Data | 37 values in `Review Rating` |

**Key feature groups:**
- **Customer demographics:** Age, Gender, Location, Subscription Status
- **Purchase details:** Item Purchased, Category, Purchase Amount, Season, Size, Color
- **Shopping behavior:** Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type

---

## 🧰 Tech Stack

| Purpose | Tool |
|---|---|
| Data Cleaning & Feature Engineering | Python (Pandas) |
| Structured Business Analysis | PostgreSQL (SQL) |
| Data Visualization | Power BI |
| Environment | Jupyter Notebook |

---

## 🔄 Project Workflow

```
Raw Data (CSV)
      │
      ▼
Python: Cleaning, Imputation, Feature Engineering
      │
      ▼
PostgreSQL: Loaded cleaned data → ran business-question SQL queries
      │
      ▼
Power BI: Built interactive dashboard on top of query outputs
      │
      ▼
Business Recommendations
```

---

## 🧹 Data Cleaning & Feature Engineering (Python)

- **Data Loading:** Imported the dataset using `pandas`.
- **Initial Exploration:** Used `df.info()` and `.describe()` to check structure and summary statistics.
- **Missing Data Handling:** Imputed missing values in `Review Rating` using the **median rating of each product category**.
- **Column Standardization:** Renamed columns to `snake_case` for readability and consistency.
- **Feature Engineering:**
  - Created `age_group` column by binning customer ages (Young Adult, Adult, Middle-aged, Senior).
  - Created `purchase_frequency_days` column from purchase frequency data.
- **Data Consistency Check:** Verified redundancy between `discount_applied` and `promo_code_used`; dropped `promo_code_used`.
- **Database Integration:** Connected the Python script to PostgreSQL and loaded the cleaned DataFrame for SQL-based analysis.

---

## 🗄️ SQL Analysis (PostgreSQL)

Ten structured business questions were answered using SQL:

| # | Question | Key Finding |
|---|---|---|
| 1 | Revenue by Gender | Male customers generated **$157,890** vs. Female **$75,191** |
| 2 | High-Spending Discount Users | 839 customers used discounts while spending above the average purchase amount |
| 3 | Top 5 Products by Rating | Gloves (3.86), Sandals (3.84), Boots (3.82), Hat (3.80), Skirt (3.78) |
| 4 | Shipping Type Comparison | Express shipping avg. spend ($60.48) slightly higher than Standard ($58.46) |
| 5 | Subscribers vs. Non-Subscribers | Non-subscribers drove **$170,436** in revenue vs. **$62,645** from subscribers |
| 6 | Discount-Dependent Products | Hat (50%), Sneakers (49.7%), Coat (49.1%), Sweater (48.2%), Pants (47.4%) discount rates |
| 7 | Customer Segmentation | Loyal: 3,116 · Returning: 701 · New: 83 |
| 8 | Top 3 Products per Category | e.g., Jewelry (Accessories), Blouse (Clothing), Sandals (Footwear), Jacket (Outerwear) |
| 9 | Repeat Buyers & Subscriptions | 2,518 non-subscribers vs. 958 subscribers among repeat buyers (>5 purchases) |
| 10 | Revenue by Age Group | Young Adult ($62,143) led all age groups |

> Full SQL query scripts are available in [`/sql`](./sql).

---

## 📈 Power BI Dashboard

An interactive dashboard was built in Power BI featuring:
- Number of customers, average purchase amount, and average review rating (KPI cards)
- Subscription status breakdown (donut chart)
- Revenue and sales by category
- Revenue and sales by age group
- Slicers for Subscription Status, Gender, Category, and Shipping Type

**📸 Dashboard Screenshot:**

<!-- Add your dashboard image below. Recommended: save the image as `assets/dashboard.png` in this repo, then keep the line below as is. -->
![Customer Behavior Dashboard](assets/dashboard.png)

---

## 💡 Key Insights

- **Male customers outspend female customers** by roughly 2x in total revenue.
- **Non-subscribers contribute far more revenue** than subscribers, despite similar average spend per customer — suggesting subscription conversion is a growth lever, not a revenue driver yet.
- **Discount-dependent categories** (Hat, Sneakers, Coats) may be over-reliant on promotions to drive sales, raising margin concerns.
- **Young Adults** are the highest revenue-generating age group, closely followed by Middle-aged customers.
- **Customer base skews heavily "Loyal"** (3,116 of 3,900), indicating strong retention but a relatively small "New" acquisition funnel (83 customers).
- **Express shipping users spend marginally more** than Standard shipping users, hinting at a premium-intent customer segment.

---

## ✅ Business Recommendations

- **Boost Subscriptions** – Promote exclusive benefits for subscribers to convert high-value non-subscribers.
- **Customer Loyalty Programs** – Reward repeat buyers to move them further into the "Loyal" segment.
- **Review Discount Policy** – Balance sales boosts with margin control on discount-dependent products.
- **Product Positioning** – Highlight top-rated and best-selling products in marketing campaigns.
- **Targeted Marketing** – Focus efforts on high-revenue age groups (Young Adults, Middle-aged) and express-shipping users.

---

## 📁 Repository Structure

```
customer-shopping-behavior-analysis/
│
├── assets/
│   └── dashboard.png              # Power BI dashboard screenshot (add here)
│
├── data/
│   └── shopping_behavior.csv      # Raw dataset (or link if not uploaded)
│
├── notebooks/
│   └── data_cleaning_eda.ipynb    # Python data cleaning & feature engineering
│
├── sql/
│   └── business_questions.sql     # All 10 SQL business analysis queries
│
├── dashboard/
│   └── customer_behavior_dashboard.pbix   # Power BI file
│
└── README.md
```

---

## ⚙️ How to Reproduce

1. Clone the repository
   ```bash
   git clone https://github.com/<your-username>/customer-shopping-behavior-analysis.git
   ```
2. Set up a Python environment and install dependencies
   ```bash
   pip install pandas numpy sqlalchemy psycopg2
   ```
3. Run the cleaning/feature engineering notebook in `/notebooks`
4. Load the cleaned data into PostgreSQL and run the queries in `/sql`
5. Open the `.pbix` file in Power BI Desktop to explore the dashboard

---

## 📬 Contact

**[Rishab Chakraborty]**
📍 Dibrugarh, India
🔗 [LinkedIn](#) · [Portfolio](#) · [Email](#)

---

⭐ If you found this project useful or interesting, consider giving it a star!
