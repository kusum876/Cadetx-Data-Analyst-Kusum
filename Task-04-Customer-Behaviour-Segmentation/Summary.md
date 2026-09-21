# CadetX Virtual Work Experience — Task 04: Customer Behaviour Segmentation

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas, scikit-learn (Google Colab) + Power BI Desktop

## Objective
Cluster customers (high-frequency, commuters, public, one-time) by usage, energy consumption, and station preferences.

## Dataset
`sessions_df` from `ev_charging_dataset.xlsx`, aggregated to customer-level features (frequency, average spend, average energy usage) across ~8,000 unique customers.

## 1. Feature-Engineered Customer Dataset
Built a per-customer feature table: session frequency, average spend per session, and average energy consumption per session. Features were standardised (scaled to comparable ranges) using `StandardScaler` prior to clustering.

## 2. Clustering Model (K-Means)
Applied K-Means clustering (k=3) on the standardised features, segmenting the customer base into three distinct behavioural groups.

## 3. Customer Personas

| Persona | Cluster | Customers | Avg Frequency | Avg Spend | Avg Energy |
|---|---|---|---|---|---|
| **Power Users** | 2 | 400 (1.5%) | 257.5 sessions | $27.82 | 47.01 kWh |
| **Regular Users** | 0 | 6,237 (74%) | 29.4 sessions | $28.77 | 49.95 kWh |
| **Occasional Users** | 1 | 1,363 (16%) | 5.7 sessions | $19.62 | 36.79 kWh |

**Power Users** — a small group of extremely high-frequency customers (likely fleet operators or daily commuters), averaging 9x more sessions than Regular Users. **Occasional Users** show both the lowest frequency and notably lower spend/energy per session, suggesting lighter, possibly one-time usage patterns.

## 4. Segment-Wise Revenue and Usage Patterns

| Segment | Customers | Total Revenue | Revenue per Customer |
|---|---|---|---|
| Power Users | 400 | $2,865,133 | ~$7,163 |
| Regular Users | 6,237 | $5,271,242 | ~$845 |
| Occasional Users | 1,363 | $153,029 | ~$112 |

Despite representing only 1.5% of the customer base, **Power Users generate nearly as much revenue as the entire Regular Users segment**, and are worth approximately **64x more per customer** than Occasional Users.

## 5. Visual Segmentation Dashboard
Built in Power BI: customer count and revenue by segment (column charts), and a scatter plot of frequency vs. average spend, colour-coded by cluster, visually confirming the three distinct behavioural groups.

## 6. Retention Strategy Recommendations
1. **Prioritise Power User retention** — losing even a handful of these 400 customers would have significant revenue impact; dedicated account support or loyalty incentives are warranted.
2. **Target Occasional Users for re-engagement** — converting even a portion of this 1,363-customer segment toward Regular User behaviour represents meaningful untapped growth potential.
3. **Segment marketing by behaviour, not by user_type category** — since Task 09 found no meaningful difference across fleet/public/taxi/delivery categories, frequency-based segmentation (as done here) is a more actionable lens for retention strategy than the original user_type field.

## Files in this repository
- `Task4_Customer_Behaviour_Segmentation.ipynb` — full code and outputs
- `customer_segments.csv` — customer-level features and cluster assignments
- `cluster_summary.csv` — segment-level summary statistics
- `Task_4.pbix` — Power BI dashboard
- `SUMMARY.md` — this file

## Conclusion
K-Means clustering revealed a small but disproportionately valuable "Power User" segment, generating nearly as much revenue as the much larger Regular User base despite representing just 1.5% of customers. This finding directly informs retention priority and complements the CLV analysis from Task 15, reinforcing that customer value in this network is driven by usage frequency rather than customer category.
