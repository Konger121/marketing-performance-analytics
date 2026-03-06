# 📖 Data Dictionary

## Marketing Performance Analytics Dashboard

---

## MasterTransactions Table — 92,678 rows × 27 columns

| Column | Type | Description |
|---|---|---|
| `transaction_id` | Integer | Unique transaction identifier (Primary Key) |
| `timestamp` | DateTime | Exact timestamp of transaction |
| `customer_id` | Integer | Foreign key → Customers table |
| `product_id` | Integer | Foreign key → Products table |
| `quantity` | Integer | Units purchased per transaction |
| `base_price` | Decimal | Unit price before discount |
| `discount_applied` | Decimal | Discount percentage (0.0–1.0) |
| `gross_revenue` | Decimal | Final revenue: `base_price × quantity − discount` |
| `campaign_id` | Integer | Foreign key → Campaigns table (0 = no campaign) |
| `refund_flag` | Text | Refund status: Yes / No |
| `transaction_date` | Date | Transaction date (truncated to month-start) |
| `transaction_month` | Integer | Month number (1–12) |
| `transaction_year` | Integer | Year (2021–2023) |
| `MRP` | Decimal | Maximum Retail Price |
| `Revenue at MRP` | Decimal | Revenue calculated at full MRP |
| `country` | Text | Customer country code (ISO 2-letter) |
| `age` | Integer | Customer age at transaction time |
| `gender` | Text | M / Female |
| `loyalty_tier` | Text | Platinum / Gold / Silver / Bronze |
| `acquisition_channel` | Text | Social / Email / Organic / Paid / Referral |
| `Age Category` | Text | Binned age group (18-25, 26-35, etc.) |
| `category` | Text | Product category |
| `brand` | Text | Product brand name |
| `is_premium` | Text | Premium / Standard |
| `campaign_channel` | Text | Marketing channel for attributed campaign |
| `campaign_objective` | Text | Campaign goal (Acquisition, Reactivation, etc.) |
| `campaign_target_segment` | Text | Target customer segment |

---

## Customers Table — 100,000 rows × 8 columns

| Column | Type | Description |
|---|---|---|
| `customer_id` | Integer | Unique customer identifier (Primary Key) |
| `signup_date` | DateTime | Customer registration date |
| `country` | Text | Country of residence (ISO 2-letter code) |
| `age` | Integer | Customer age |
| `gender` | Text | Male / Female |
| `loyalty_tier` | Text | Platinum / Gold / Silver / Bronze |
| `acquisition_channel` | Text | Channel through which customer was acquired |
| `Age Category` | Text | Binned: 18-25 / 26-35 / 36-45 / 46-55 / 56+ |

---

## Products Table — 2,000 rows × 8 columns

| Column | Type | Description |
|---|---|---|
| `product_id` | Integer | Unique product identifier (Primary Key) |
| `category` | Text | Product category (Electronics, Grocery, etc.) |
| `brand` | Text | Brand name (100 unique brands) |
| `base_price` | Decimal | Standard selling price |
| `launch_date` | Date | Product launch date |
| `is_premium` | Text | Premium / Standard classification |
| `product_age_days` | Integer | Days since product launch |
| `is_new_product` | Text | New / Established classification |

---

## Campaigns Table — 50 rows × 10 columns

| Column | Type | Description |
|---|---|---|
| `campaign_id` | Integer | Unique campaign identifier (Primary Key) |
| `channel` | Text | Marketing channel (Affiliate, Paid Search, Email, etc.) |
| `objective` | Text | Campaign goal (Acquisition, Reactivation, Cross-sell, etc.) |
| `start_date` | Date | Campaign start date |
| `end_date` | Date | Campaign end date |
| `target_segment` | Text | Target customer group |
| `expected_uplift` | Decimal | Projected revenue lift (%) |
| `Campaign_duration_days` | Integer | Length of campaign in days |
| `Campaign_quarter` | Text | Quarter label (e.g., Q4-2021) |
| `Campaign_year` | Integer | Campaign year |

---

## MasterEvents Table — 10,000 rows × 24 columns

| Column | Type | Description |
|---|---|---|
| `event_id` | Integer | Unique event identifier (Primary Key) |
| `timestamp` | DateTime | Event timestamp |
| `customer_id` | Integer | Foreign key → Customers |
| `session_id` | Integer | Session grouping identifier |
| `event_type` | Text | view / click / add_to_cart / purchase |
| `product_id` | Integer | Foreign key → Products |
| `device_type` | Text | Desktop / Mobile / Tablet |
| `traffic_source` | Text | Organic / Paid / Email / Social / Referral |
| `campaign_id` | Integer | Attributed campaign (0 = none) |
| `page_category` | Text | Page type (PLP / PDP / Cart / Checkout) |
| `session_duration_sec` | Integer | Session length in seconds |
| `experiment_group` | Text | Control / Variant_A / Variant_B |
| `session_duration_minutes` | Decimal | Calculated field: `session_duration_sec / 60` |
| `engagement_level` | Text | Low / Medium / High (binned from duration) |
| `event_date` | Date | Event date |
| `is_conversion` | Integer | 1 = purchase event, 0 = otherwise |
| `country` | Text | User country |
| `age` | Integer | User age |
| `gender` | Text | Male / Female |
| `loyalty_tier` | Text | Platinum / Gold / Silver / Bronze |
| `Age Category` | Text | Age bin |
| `campaign_channel` | Text | Attributed campaign channel |
| `campaign_objective` | Text | Attributed campaign objective |
| `campaign_target_segment` | Text | Attributed campaign segment |

---

## YoY_MoM_Growth_Metrics CSV — 36 rows × 29 columns

Pre-calculated monthly growth metrics table covering January 2021 – December 2023.

| Column | Description |
|---|---|
| `Year`, `Month`, `Month_Name`, `Quarter`, `YearMonth` | Date dimensions |
| `Revenue` | Monthly gross revenue |
| `Revenue_MoM%` | Revenue change vs. prior month |
| `Revenue_YoY%` | Revenue change vs. same month prior year |
| `Revenue_MoM_Indicator` | Emoji indicator (📈 / 📉) |
| `Revenue_MoM_Status` | Growth / Decline text label |
| `Transactions`, `AOV`, `Customers`, `Units_Sold`, `Refund_Amount` | Additional KPI metrics with corresponding MoM% and YoY% columns |

---

*Data Dictionary v1.0 — February 2026*
