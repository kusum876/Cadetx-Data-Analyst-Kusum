# CadetX Virtual Work Experience — Task 01: EV Charging Demand Forecasting

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas, matplotlib, Prophet, scikit-learn (Google Colab)

## Objective
Predict future EV charging demand from historical session patterns to support capacity planning, staffing, and energy procurement decisions.

## Dataset
Provided as `ev_charging_dataset.xlsx`, containing 3 related sheets:
- **stations** (33 records): station_id, station_name, region, activation_year, n_chargers
- **chargers** (199 records): charger_id, station_id, charger_type, max_power_kW, installation_date
- **sessions** (294,024 records): individual charging session logs including timestamps, duration, energy usage, cost, and customer details

## 1. Data Cleaning
- Loaded and verified all three sheets using pandas.
- Checked for missing values across all 294,024 session records — **none found**.
- Checked for duplicate rows — **none found**.
- Verified data types — timestamps were correctly recognized as datetime, all numeric columns properly typed.
- Validated value ranges (session duration, energy usage, cost) — all realistic, no anomalies.
- **Conclusion:** dataset required no corrective cleaning; verification confirmed high data quality.

## 2. Cleaned Time-Series Dataset
Aggregated the 294,024 raw sessions into:
- **Daily demand** — 1,096 rows (one per day, Jan 1, 2022 – Dec 31, 2024), showing total sessions per day.
- **Hourly demand** — 24 rows, showing total sessions accumulated per hour-of-day across the full 3-year period.
- **Weekly demand** — 7 rows, showing total sessions per day-of-week across the full 3-year period.

## 3. Insights on Seasonal and Weekly Patterns

**Hourly Pattern:** Demand is lowest overnight (12am–5am, ~2,600–2,750 sessions total) and rises sharply from 6am, peaking between **9am–2pm** (~24,000 sessions), before declining through the evening. This indicates usage is concentrated during standard business hours rather than overnight home charging.

**Weekly Pattern:** Weekdays show consistent demand (~45,000–46,000 sessions each), while weekends drop to ~33,300 sessions — a **27% decline**. This points to commuter-driven, workday-focused usage rather than leisure travel.

**Yearly Growth Pattern:** Daily demand shows two distinct step-changes (early 2023, early 2024) rather than gradual growth. Cross-referencing with station data confirms this aligns with network expansion: stations grew from 8 (2022) → 17 (2023) → 33 (2024), roughly doubling each year. Demand scaled proportionally, indicating the network is currently **supply-driven** — new stations are quickly utilized, suggesting continued expansion would likely be met with sustained usage.

**Planning Implication:** Capacity and staffing should be prioritized around weekday business hours (9am–2pm), with reduced resources needed on weekends and overnight. Continued station investment is likely to be matched by demand rather than sitting idle.

## 4. Forecasting Model
Built a time-series forecasting model using **Facebook Prophet**, trained on the full 3-year daily demand dataset.

- Generated a 365-day forward forecast, which inherently includes 30-day and 90-day windows within it.
- The forecast projects continued growth into 2025, extrapolating the historical station-expansion-driven trend.

**Limitation noted:** Since Prophet has no direct knowledge of *planned* future station additions, this forecast represents "expected demand if similar network expansion continues," not a guaranteed outcome. A few early-dataset predictions (Jan 2022) also produced unrealistic negative values, a known limitation of Prophet's default settings.

## 5. Accuracy Metrics
Evaluated model performance by comparing predicted vs. actual values across the full historical period:

- **MAPE (Mean Absolute Percentage Error): 11.19%** — predictions were, on average, within ~11% of actual values, indicating good reliability for planning purposes.
- **RMSE (Root Mean Squared Error): 27.57** — predictions were, on average, off by about 28 sessions/day, relatively small compared to the dataset's typical daily range (100–700+ sessions).

## Files in this repository
- `Task1_EV_Charging_Demand_Forecasting.ipynb` — full code, outputs, and charts
- `daily_demand.csv` — cleaned daily time-series dataset
- `hourly_demand_pattern.csv` — hourly aggregation
- `weekly_demand_pattern.csv` — weekly aggregation
- `SUMMARY.md` — this file

## Conclusion
This analysis transformed 294,024 raw charging session records into a clean, actionable time-series dataset, identified clear hourly, weekly, and yearly demand patterns, and built a forecasting model with a MAPE of 11.19% — a reliable basis for near-term capacity, staffing, and energy procurement planning.
