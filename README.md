# 📊 Marketing Performance Analytics Dashboard — Power BI

> **Transforming 204,728 marketing records into 5 interactive dashboards that deliver $8.87M in revenue insights, validated A/B test results, and actionable growth intelligence.**

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=flat&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Excel](https://img.shields.io/badge/Microsoft-Excel-217346?style=flat&logo=microsoftexcel&logoColor=white)](https://microsoft.com/excel)
[![DAX](https://img.shields.io/badge/DAX-90%2B%20Measures-0078D4?style=flat)](https://learn.microsoft.com/en-us/dax/)
[![Records](https://img.shields.io/badge/Records-204%2C728-blueviolet?style=flat)](/)
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)](/)

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem Statement](#-business-problem-statement)
- [Project Objectives](#-project-objectives)
- [Dataset Description](#-dataset-description)
- [Tools & Technologies](#-tools--technologies)
- [Data Cleaning & Preprocessing](#-data-cleaning--preprocessing)
- [Exploratory Data Analysis](#-exploratory-data-analysis)
- [Key Insights](#-key-insights)
- [Business Recommendations](#-business-recommendations)
- [Dashboard Explanation](#-dashboard-explanation)
- [How to Run / Reproduce](#-how-to-run--reproduce)
- [Folder Structure](#-folder-structure)
- [Future Improvements](#-future-improvements)

---

## 🔍 Project Overview

This end-to-end analytics project transforms raw, multi-source marketing data into a fully interactive Power BI dashboard suite. The solution integrates six data tables spanning transactions, customer demographics, product catalog, campaign metadata, and behavioral event logs — all unified through a star schema data model.

The project delivers five purpose-built dashboards covering executive KPIs, customer segmentation, product performance, campaign ROI, and A/B experiment validation. All dashboards are powered by 90+ custom DAX measures and enriched with pre-calculated month-over-month (MoM) and year-over-year (YoY) growth metrics.

**Project Timeline:** January–February 2026  
**Analyst:** Akileshwaran S  
**Domain:** Marketing Analytics / E-commerce

---

## 💼 Business Problem Statement

A marketing organization operating across multiple geographies and channels lacked a centralized analytics capability. Key business challenges included:

- **No unified view** of revenue, customers, and campaign performance across channels
- **Inability to measure** campaign ROI or channel attribution effectively
- **No systematic approach** to A/B testing and conversion rate optimization
- **Manual reporting** limiting the ability to identify trends or growth drivers in real time
- **Fragmented data** across transactions, customer profiles, product listings, and event logs

The business needed a scalable analytics solution that could consolidate these data sources, surface actionable insights, and support evidence-based decision-making.

---

## 🎯 Project Objectives

1. **Data Integration** — Consolidate six disparate data sources into a unified star schema model
2. **Dashboard Development** — Build five interactive, executive-ready dashboards in Power BI
3. **Growth Tracking** — Implement MoM% and YoY% metrics across all KPIs with visual indicators
4. **Customer Intelligence** — Segment customers by demographics, loyalty tier, and lifetime value
5. **Campaign Analytics** — Measure channel-level revenue attribution and conversion performance
6. **A/B Test Validation** — Statistically evaluate website optimization experiments

---

## 📁 Dataset Description

The dataset spans **three years (2021–2023)** and contains **204,728 records** across six tables:

| Table | Records | Columns | Description |
|---|---|---|---|
| `MasterTransactions` | 92,678 | 27 | Complete transaction history with customer, product, and revenue data |
| `Customers` | 100,000 | 8 | Demographics, loyalty tier, and acquisition channel |
| `Products` | 2,000 | 8 | Product catalog with pricing, category, and brand |
| `Campaigns` | 50 | 10 | Marketing campaigns with channel, objective, and duration |
| `MasterEvents` | 10,000 | 24 | Website behavioral events and A/B testing experiment data |
| `Calendar` | 1,096 | 11 | Date dimension table (2021–2023) |

### Key Fields

**MasterTransactions:** `transaction_id`, `customer_id`, `product_id`, `gross_revenue`, `discount_applied`, `campaign_id`, `refund_flag`, `transaction_year`, `transaction_month`

**Customers:** `customer_id`, `loyalty_tier` (Platinum/Gold/Silver/Bronze), `acquisition_channel`, `country`, `age`, `is_premium`

**Campaigns:** `campaign_id`, `channel`, `objective`, `target_segment`, `expected_uplift`, `campaign_duration_days`

**MasterEvents:** `event_id`, `experiment_group` (Control/Variant_A/Variant_B), `event_type`, `session_duration_sec`, `engagement_level`, `is_conversion`

---

## 🛠 Tools & Technologies

| Category | Tool / Technology |
|---|---|
| **BI & Visualization** | Power BI Desktop |
| **Data Transformation** | Power Query (M Language) |
| **Analytics Formulas** | DAX (Data Analysis Expressions) |
| **Data Preparation** | Microsoft Excel |
| **Data Modeling** | Star Schema (Fact + Dimension tables) |
| **Growth Metrics** | Pre-calculated CSV (MoM% / YoY%) |
| **Statistical Analysis** | A/B Test Lift Calculation (DAX) |

---

## 🧹 Data Cleaning & Preprocessing

All transformations were performed in **Power Query** before loading data into the model.

### MasterTransactions (92,678 rows × 27 columns)
- Converted all date columns to proper `DateTime` format
- Standardized `refund_flag` from Yes/No text to binary values
- Added calculated columns: `transaction_year`, `transaction_month`, `transaction_quarter`
- Validated revenue formula: `gross_revenue = base_price × quantity − discount_applied`
- Removed duplicate and null records

### MasterEvents (10,000 rows × 24 columns)
- Created `session_duration_minutes` from raw seconds
- Added `engagement_level` categories (Low / Medium / High) based on duration thresholds
- Linked to Campaign and Customer dimension tables via foreign keys

### Customers (100,000 rows × 8 columns)
- Created age category bins: `18–25`, `26–35`, `36–45`, `46–55`, `56+`
- Validated loyalty tier assignments and cleaned inconsistent labels
- Standardized acquisition channel naming conventions

### Products (2,000 rows × 8 columns)
- Categorized across 6 product categories
- Standardized brand names across 100 brands
- Flagged premium vs. standard products

### Performance Optimizations
- Enabled query folding wherever supported
- Optimized data types (integer over decimal where applicable)
- Removed unused columns to reduce model size and improve query speed (< 2 seconds for complex visuals)

---

## 📈 Exploratory Data Analysis

### Revenue Trends (2021–2023)
- Total 3-year revenue: **~$8.87M** across 92,678 transactions
- 2023 revenue: **$2.94M**, showing relative stability with seasonal spikes
- **November consistently peaks** across all three years (~24–25% MoM growth), indicating a strong seasonal sales cycle

### Customer Behavior
- **100,000 total customers** with a **41.2% repeat purchase rate**
- Premium customers generate **233% higher Average Order Value** ($147 vs. $44)
- Platinum tier customers exhibit the highest Customer Lifetime Value (CLV)
- Customer acquisition spread across: Social, Email, Organic, Paid, and Referral channels

### Product Performance
- **100% sell-through rate** — all 2,000 products recorded at least one sale
- **Electronics dominates** at 41% of total revenue
- Premium products represent **77% of revenue** despite lower unit volume
- Average discount rate: **4.13%** — minimal price erosion

### Campaign Performance
- 50 campaigns executed, reaching **86.9% of the customer base**
- **Affiliate channel** led with $1,697,655 in attributable revenue
- **Reactivation campaigns** delivered the highest revenue by objective ($2,078,613)
- Campaign conversion rate: **79.7%**

### A/B Testing
- Experiment conducted across **9,912 sessions**
- Control baseline purchase rate: **4.68%**
- Variant A lift: **+16.4%** (5.44% purchase rate)
- Variant B lift: **+21.1%** (5.66% purchase rate) ✅

---

## 💡 Key Insights

| # | Insight | Impact |
|---|---|---|
| 1 | **November revenue spike (+24.4% MoM in 2023)** is a consistent seasonal pattern across all 3 years | High — enables proactive inventory and campaign planning |
| 2 | **Premium customers drive 77% of revenue** from ~23% of the product catalog | High — justify upsell and loyalty investment |
| 3 | **Affiliate channel outperforms all others** in revenue attribution ($1.7M) | High — supports budget reallocation |
| 4 | **Reactivation campaigns yield highest ROI** among all campaign objectives | Medium — optimize campaign mix |
| 5 | **Variant B wins the A/B test** with +21.1% lift and statistical significance | High — immediate deployment opportunity |
| 6 | **41.2% repeat purchase rate** indicates strong organic retention | Medium — retention is working; test expansion levers |
| 7 | **September is a consistent low point** across multiple years (MoM declines) | Medium — targeted promotions could offset seasonal dip |

---

## 📌 Business Recommendations

1. **Deploy Variant B immediately** — The A/B experiment confirms a +21.1% improvement in purchase rate. Expected uplift: ~98 additional purchases per 10,000 sessions.

2. **Double down on Affiliate marketing** — Affiliate outperforms all other channels in revenue attribution. Reallocate budget from underperforming channels.

3. **Launch a November campaign calendar** — Given consistent ~25% revenue spikes in November (all 3 years), prepare campaigns 6–8 weeks in advance to capitalize on peak demand.

4. **Invest in Premium product cross-sell** — With 233% higher AOV, even minor conversion improvements among standard customers represent significant revenue upside.

5. **Prioritize Reactivation campaigns** — At $2.07M attributable revenue, reactivation outperforms acquisition and cross-sell objectives. Allocate more campaigns toward lapsed customers.

6. **Monitor September proactively** — Implement counter-seasonal promotions or engagement campaigns in August–September to flatten the recurring revenue dip.

7. **Develop a Platinum loyalty fast-track program** — Platinum tier drives the highest CLV. Lowering the barrier to reach Platinum status could increase overall customer value.

---

## 📊 Dashboard Explanation

The solution comprises **five interconnected dashboards**, each serving a distinct business function:

### Dashboard 1: Executive Summary
Provides a top-level view of organizational performance with KPI cards for Total Revenue ($2.94M), Total Transactions (30,547), Total Customers (100,000), and Average Order Value ($96.20). Includes time-series revenue trends and MoM/YoY growth indicators across all major metrics.

### Dashboard 2: Customer Analytics
Segments customers by demographics (age, gender, country), loyalty tier, and premium status. Highlights the 41.2% repeat purchase rate, CLV by segment, and acquisition channel effectiveness. Key visual: Premium vs. Standard AOV comparison ($147 vs. $44).

### Dashboard 3: Product Performance
Analyzes the 2,000-product catalog by category, brand, and premium status. Reveals Electronics dominance (41% of revenue) and the 77% revenue contribution from premium products. Includes discount impact analysis showing minimal (4.13%) price erosion.

### Dashboard 4: Campaign Performance
Tracks 50 campaigns across 5 channels and multiple objectives. Surfaces the Affiliate channel as the top performer ($1.7M) and Reactivation as the highest-ROI objective ($2.07M). Includes refund quality metrics and conversion rate trends by quarter.

### Dashboard 5: A/B Testing Experiment
Validates website optimization experiments across 9,912 sessions. Uses a waterfall chart for lift visualization, 100% stacked columns for device distribution (randomization check), and a statistical significance table. Recommends **Variant B** implementation with +21.1% lift.

---

## ▶️ How to Run / Reproduce

### Prerequisites
- **Power BI Desktop** (latest version recommended) — [Download here](https://powerbi.microsoft.com/desktop/)
- **Microsoft Excel** (for source data review)

### Steps

1. **Clone this repository**
   ```bash
   git clone https://github.com/yourusername/marketing-performance-analytics.git
   cd marketing-performance-analytics
   ```

2. **Open the Power BI file**
   - Launch Power BI Desktop
   - Open `dashboard/marketing_dashboard.pbix`

3. **Verify data source paths**
   - Go to `Home → Transform Data → Data Source Settings`
   - Update file paths to point to your local `/data/` folder if prompted

4. **Refresh the data**
   - Click `Home → Refresh` to reload all tables
   - Confirm all 6 tables load without errors

5. **Explore the dashboards**
   - Navigate between the 5 dashboard pages using the tab bar
   - Use slicers for Year, Quarter, Channel, and Loyalty Tier filtering

### Data Files Required
| File | Location | Description |
|---|---|---|
| `PowerBI_Master_Data.xlsx` | `/data/raw/` | Main dataset (6 sheets) |
| `YoY_MoM_Growth_Metrics.csv` | `/data/processed/` | Pre-calculated growth metrics (36 months) |
| `marketing_dashboard.pbix` | `/dashboard/` | Power BI report file |

---

## 📂 Folder Structure

```
marketing-performance-analytics/
│
├── README.md                          # Project documentation (this file)
│
├── data/
│   ├── raw/
│   │   └── PowerBI_Master_Data.xlsx   # Source dataset (6 tables)
│   └── processed/
│       └── YoY_MoM_Growth_Metrics.csv # Pre-calculated MoM & YoY metrics
│
├── dashboard/
│   └── marketing_dashboard.pbix       # Power BI dashboard file
│
├── docs/
│   └── Final_Project_Report.docx      # Full project report
│
├── screenshots/
│   ├── 01_executive_summary.png
│   ├── 02_customer_analytics.png
│   ├── 03_product_performance.png
│   ├── 04_campaign_performance.png
│   ├── 05_ab_testing.png
│   └── data_model_schema.png
│
└── assets/
    └── data_dictionary.md             # Column-level data documentation
```

---

## 🖼 Suggested Screenshots for Repository

Include the following images in the `/screenshots/` folder to showcase your work:

| File Name | What to Capture |
|---|---|
| `01_executive_summary.png` | Full Executive Summary dashboard with all KPI cards and revenue trend chart |
| `02_customer_analytics.png` | Customer dashboard with loyalty segmentation and AOV comparison |
| `03_product_performance.png` | Product dashboard showing Electronics dominance and premium/standard split |
| `04_campaign_performance.png` | Campaign dashboard with Affiliate channel bar chart and conversion trend |
| `05_ab_testing.png` | A/B Testing dashboard with waterfall lift chart and significance table |
| `data_model_schema.png` | Power BI data model view showing star schema relationships |
| `dax_measures.png` | Screenshot of the DAX measure panel showing key formula examples |

> **Tip:** Export screenshots at full resolution (1920×1080 minimum) and embed them in this README under each dashboard section for maximum visual impact.

---

## 🔮 Future Improvements

- [ ] **Predictive Revenue Forecasting** — Integrate a time-series forecasting model (ARIMA or Prophet) to project monthly revenue 3–6 months forward
- [ ] **Customer Churn Prediction** — Build a logistic regression or gradient boosting model to identify at-risk customers before they lapse
- [ ] **Real-Time Data Pipeline** — Replace static Excel source with a live SQL or API connection for automated daily refresh
- [ ] **Power BI Service Deployment** — Publish dashboards to Power BI Service with scheduled refresh and role-level security (RLS)
- [ ] **Attribution Modeling** — Implement multi-touch attribution to more accurately credit customer journeys spanning multiple campaigns
- [ ] **Python Integration** — Add Python visuals within Power BI for advanced statistical plots (correlation heatmaps, distribution charts)
- [ ] **Natural Language Q&A** — Enable Power BI Q&A feature with custom synonyms for non-technical stakeholder self-service

---

## 👤 Author

**Akileshwaran S**  
Data Analyst | Power BI | SQL | Python | Excel  
📧 [your.email@example.com]  
🔗 [LinkedIn Profile URL]  
🌐 [Portfolio URL]

---

*This project was developed as a portfolio demonstration of end-to-end data analytics capabilities using Power BI, Power Query, and DAX.*
