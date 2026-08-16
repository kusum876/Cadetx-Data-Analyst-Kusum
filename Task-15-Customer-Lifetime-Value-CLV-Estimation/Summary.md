
# CadetX Virtual Work Experience — Task 15: Customer Lifetime Value (CLV) Estimation

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas (Google Colab) + Power BI Desktop

## Objective
Estimate long-term value of customer segments (fleet, taxi, public, delivery) from repeat-customer behaviour.

## Dataset
`sessions_df` from `ev_charging_dataset.xlsx`, grouped by `customer_id` and `user_type` (25,847 unique customer-segment combinations).

## 1. CLV Model
Calculated CLV using the formula: **frequency × average spend per session**. This was computed at the individual customer level, then aggregated by user segment.

## 2. Segment-Wise CLV Distribution

| User Type | Avg CLV | Median CLV | Total CLV | Customers |
|---|---|---|---|---|
| Fleet | $318.73 | $155.52 | $2,051,679 | 6,437 |
| Public | $317.83 | $153.80 | $2,050,618 | 6,452 |
| Delivery | $314.20 | $153.72 | $2,036,007 | 6,480 |
| Taxi | $313.80 | $153.01 | $2,032,796 | 6,478 |

CLV is nearly identical across all four segments (within 2% of each other), consistent with the behavioural finding from Task 09 that user type does not meaningfully predict usage patterns.

## 3. High-Value Customer Identification
The average CLV (~$315) is roughly **double** the median CLV (~$154) across every segment, indicating a **right-skewed distribution** — most customers contribute moderate value, while a smaller group of high-frequency customers drives disproportionate value. The top 10 customers by CLV (spanning all four user types, ranging $2,370–$2,540) are worth approximately **8x the average customer**.

## 4. Retention Strategy Recommendations
Since CLV does not differ meaningfully by segment, retention strategy should be **frequency-based rather than segment-based**:
1. Identify and specifically reward the top ~10% of customers by session frequency, regardless of their user_type category, through loyalty incentives.
2. Investigate the gap between median and average customers — understanding what drives a subset of customers toward significantly higher engagement could reveal opportunities to shift more of the customer base toward that behaviour.
3. Since fleet, public, taxi, and delivery segments are behaviourally indistinguishable, marketing and retention resources should not be disproportionately allocated to any single segment based on assumed value differences.

## 5. CLV Dashboard
Built in Power BI: a column chart comparing average CLV across the four user segments, and a table listing the top 10 highest-value customers with their frequency and CLV scores.

## Files in this repository
- `Task_15_Customer_Lifetime_Value_CLV_Estimation.ipynb` — full code and outputs
- `segment_clv.csv` — segment-level CLV summary
- `top_customers_clv.csv` — top 10 high-value customers
- `Task 15.pbix` — Power BI dashboard
- `SUMMARY.md` — this file

## Conclusion
This analysis found that customer lifetime value is remarkably consistent across all user segments, reinforcing the Task 09 finding that fleet, public, taxi, and delivery users behave similarly overall. The more actionable insight is the right-skewed distribution within each segment — a small group of high-frequency customers drives disproportionate value, and retention efforts should target this behavioural pattern directly rather than assuming any customer category is inherently more valuable.
