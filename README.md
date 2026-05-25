# olist_ecommerce_analytics

# Sports & Leisure Revenue Decline Analysis (Olist E-Commerce)

An end-to-end data analytics project focused on diagnosing a severe revenue drop within the **Sports & Leisure** category on the Olist e-commerce platform (Brazil). This project spans from raw data preparation and star-schema star modeling to Python-based advanced metric aggregation and Power BI visualization.

## 📊 Core Business Key Findings

### Finding 1 — Early Revenue Drop Was Not Driven by Order Volume
Revenue began a steady decline starting in week **2018-07**, whereas order volumes remained highly stable. A steep drop in actual transaction numbers only materialized later, from week **2018-14** onwards.
* **Insight:** The initial issue was not a lack of customer traffic or demand volume. Buyers were still purchasing at the same rate but spending less per transaction.

![alt text](99_key_findings/images/Early_Revenue_Drop_Was_Not_Driven_by_Orders_Drop.png)



### High-Price Products Collapsed First
The high-price tier (>R$110) experienced an immediate downslide from week **2018-07**, ultimately losing **57% of its weekly volume** by **2018-26**. Conversely, the low and mid-price tiers remained completely resilient or experienced slight growth up until week **2018-14**.
* **Insight:** This explicitly explains the AOV contraction. The platform suffered a critical contraction in high-ticket transactions, which could not be offset by low-value sales.

![alt text](99_key_findings/images/sports_leisure_cheap_products_held_best.png)
---

# Getting Started: Project Setup & Execution Guide

This guide provides step-by-step instructions on how to set up, execute, and replicate the analytics pipeline for the Sports & Leisure revenue decline analysis.

---

## 📋 Prerequisites

Before running the project, ensure you have the following installed on your local machine:
* **Python 3.8 or higher**
* **Power BI Desktop** (for viewing the interactive dashboard)
* **Git** (for version control and repository cloning)

---

## 🛠️ Step 1: Environment Setup

1. **Clone the Repository**
   Open your Git terminal (`MINGW64` / Git Bash) and run:
   ```bash
   git clone [https://github.com/jonas-butkevicius/olist_ecommerce_analytics.git](https://github.com/YOUR_USERNAME/olist_ecommerce_analytics.git)
   cd olist_ecommerce_analytics

# Create venv
python -m venv venv

# Activate venv (Windows Git Bash / MINGW64)
source venv/Scripts/activate

# Activate venv (Windows Command Prompt)
# venv\Scripts\activate.bat

# 🛠️ Project Architecture & Technical Stack

```text
├── 01_data_preparation/   # Star schema relational architecture diagrams
├── 99_key_findings/       # Generated analysis images and reports
├── python/                # Advanced Pandas data pipelines and aggregations
├── power_bi/              # Interactive tracking dashboards (.pbix)
├── olist_dataset_clean.xlsx # Master workbook containing data schemas and exploratory views
└── README.md
```

## 📂 File & Folder Descriptions

### 🟢 `olist_dataset_clean.xlsx` (Core Data & Exploratory Analysis)
Central master workbook housing the cleaned relational data and initial exploratory sheets used to validate early project hypotheses:
* **`pivots`** — Aggregated summaries testing early assumptions on weekly order volumes, categories, revenues, and seller cohorts.
* **`reference`** — Mapping tables, structural lookup variables, and core dataset definitions.
* **`dissatisfaction rate charts`** — Early trend visualizations analyzing low review scores, delivery delays, and logistics friction.

### 📁 Data Engineering & Modeling (`/01_data_preparation`)
Contains the relational architecture designs. The project implements a standard **Star Schema** data warehouse structure, linking localized order items (`fact_order_items`) out to dedicated dimension tables:
* `tbl_products`
* `tbl_sellers`
* `tbl_customers`
* `tbl_reviews`
* `dim_date`

### 📁 Advanced Analytics Pipeline (`/python`)
Contains the production Python scripts. Built on a Pandas data pipeline that automates:
* Data cleaning and formatting.
* Historical window partitioning using `.rolling(window=6, min_periods=1).mean()` to generate 6-week moving averages for smoothing cyclical volatility.
* Dynamic quantile distribution boundaries using `.quantile([0.33, 0.66])` for objective product price categorization.

### 📁 Data Visualization (`/power_bi`)
Houses the interactive `.pbix` tracking dashboards. The visual layer ingests the final Python-engineered datasets and utilizes optimized custom datetime indexing, dual-axis multi-metric trends.