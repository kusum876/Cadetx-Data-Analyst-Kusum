# CadetX Virtual Work Experience — Task 02: Revenue Forecasting & Price Sensitivity

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas, Prophet (Google Colab)

## Objective
Model how revenue changes with demand, pricing, and seasonality, and how price adjustments affect behaviour and income.

## Dataset
`sessions_df` from `ev_charging_dataset.xlsx` (294,024 sessions), using `total_cost`, `price_per_kwh`, and `energy_kwh` columns.

## 1. Revenue Time-Series Dataset
Aggregated total daily revenue across the 3-year dataset (1,096 days), forming the basis for forecasting and trend analysis.

## 2. Price Elasticity Analysis
Price in this dataset ranges from $0.45 to $0.80/kWh (mean: $0.59). Grouping sessions by price level revealed that **average energy consumption per session remains stable (44.6–49.8 kWh) across the entire price range**, with no meaningful downward trend as price increases. While session *count* varies by price bucket, this closely reflects how frequently each price point naturally occurs in the data, rather than clear evidence that customers reduce usage at higher prices. **Conclusion: relatively low price elasticity of demand** — existing customers do not appear to meaningfully change how much they charge based on price within the observed range.

## 3. Monthly Revenue Forecast Model
Built a Prophet forecasting model on daily total revenue, trained on the full 3-year dataset. The model projects continued growth, forecasting daily revenue of approximately **$17,600 on weekdays** and **$15,400–15,500 on weekends** by mid-2025, consistent with the weekday/weekend demand pattern identified in Task 01.

## 4. Scenario Simulations

| Scenario | Total Revenue | Change |
|---|---|---|
| Current | $8,171,100.12 | — |
| Price +5% | $8,579,655.13 | +$408,555 |
| Price −10% | $7,353,990.11 | −$817,110 |

Simulations assume usage volume remains constant, based on the low elasticity finding — revenue is modelled as scaling proportionally with price.

## 5. Executive Summary on Pricing Impact
Analysis found no meaningful relationship between price level and energy consumption per session, indicating relatively low price elasticity of demand within the observed $0.45–$0.80/kWh range. This suggests the network could reasonably increase prices without significantly reducing existing customer usage. A simulated 5% price increase would raise total revenue by approximately $408,555, while a 10% decrease would reduce revenue by approximately $817,110. **Recommendation:** given low observed price sensitivity, a moderate price increase (e.g., 5%) represents a low-risk opportunity to boost revenue without materially impacting usage volume — though this should be validated with a controlled pilot test before full rollout, since historical elasticity within the observed range cannot fully predict customer response to prices outside it.

## Files in this repository
- `Task2_Revenue_Forecasting_Price_Sensitivity.ipynb` — full code and outputs
- `daily_revenue.csv` — revenue time-series dataset
- `price_elasticity.csv` — session count and energy usage by price bucket
- `SUMMARY.md` — this file

## Conclusion
This analysis found low price elasticity of demand across the observed pricing range, supporting a data-backed recommendation for a moderate price increase as a low-risk revenue growth lever. Combined with a Prophet-based revenue forecast and quantified scenario simulations, this provides a clear, actionable basis for pricing strategy decisions.
