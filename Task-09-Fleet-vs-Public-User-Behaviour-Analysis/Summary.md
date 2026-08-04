# CadetX Virtual Work Experience — Task 09: Fleet vs Public User Behaviour Analysis

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas, matplotlib (Google Colab)

## Objective
Compare charging habits of taxis, fleets, delivery vehicles, and public users, and identify which groups drive revenue and demand.

## Dataset
`sessions_df` from `ev_charging_dataset.xlsx` (294,024 sessions), segmented by the `user_type` column (delivery, fleet, public, taxi).

## 1. Segmented Usage Dataset
Grouped all sessions by `user_type` and calculated key metrics per segment: total sessions, average energy consumption (kWh), average cost per session, and total revenue.

| User Type | Total Sessions | Avg Energy (kWh) | Avg Cost ($) | Total Revenue |
|---|---|---|---|---|
| Fleet | 73,696 | 47.04 | 27.84 | $2,051,679 |
| Public | 73,754 | 46.96 | 27.80 | $2,050,618 |
| Delivery | 73,339 | 46.94 | 27.76 | $2,036,007 |
| Taxi | 73,235 | 46.92 | 27.76 | $2,032,796 |

## 2. Comparison Charts
Built bar charts comparing total sessions, average energy usage, and average cost across all four user types (see notebook for visuals).

## 3. Behavioural Insights
Contrary to initial expectations, the analysis found **no meaningful behavioural difference** between fleet, public, taxi, and delivery users. All four segments show nearly identical session frequency (within 0.7% of each other), average energy consumption (within 0.3 kWh), average cost per session (within $0.08), and total revenue contribution (within ~1% of each other, all around $2.03–2.05M).

## 4. Revenue Contribution
Revenue is distributed almost evenly across all four segments, with no single user type dominating. Fleet contributes marginally the most ($2,051,679), and taxi marginally the least ($2,032,796) — a difference of less than 1%, not practically significant.

## 5. Fleet Partnership Recommendations
Since fleet users do not show meaningfully higher usage, energy consumption, or spend compared to public users, there is **no strong evidence-based case for prioritising fleet-specific partnerships** based on usage/revenue data alone. Any fleet partnership strategy should be evaluated on other strategic factors (e.g., contract stability, predictable demand scheduling, off-peak charging potential) rather than an assumption that fleets are inherently higher-value customers.

## Files in this repository
- `Task9_Fleet_vs_Public_User_Behaviour_Analysis.ipynb` — full code and outputs
- `user_type_comparison.csv` — segmented usage dataset
- `SUMMARY.md` — this file

## Conclusion
This analysis found that all four user segments (fleet, public, taxi, delivery) behave nearly identically across frequency, energy use, and spend. This is a valid and useful finding: it indicates the charging network currently serves all user types uniformly, and that fleet partnerships should not be prioritised over other segments without additional strategic justification beyond usage data.
