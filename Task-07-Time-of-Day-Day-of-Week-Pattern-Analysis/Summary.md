# CadetX Virtual Work Experience — Task 07: Time-of-Day & Day-of-Week Pattern Analysis

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas (Google Colab) + Power BI Desktop

## Objective
Identify peak hours, weekend vs weekday differences, and seasonal trends to optimise pricing, staffing, and supply.

## Dataset
`sessions_df` and `chargers_df` from `ev_charging_dataset.xlsx` (294,024 sessions, 199 chargers).

## 1. Hourly and Weekly Demand (reused from Task 01)
Demand peaks between 9am–2pm (~24,000 sessions), lowest overnight (12am–5am, ~2,600 sessions). Weekdays average ~45,000–46,000 sessions each; weekends drop to ~33,300 — a 27% decline.

## 2. Seasonal Trend Analysis
Monthly session counts show **no significant seasonal pattern** — all 12 months fall within a tight range of 23,156 to 25,128 sessions (under 9% spread). This indicates EV charging demand is driven by consistent, routine usage (e.g., commuting) rather than seasonal or leisure factors, unlike the strong hourly/weekly patterns identified above.

## 3. Behaviour by Region
Session count by region ranges from North West (65,789, highest) to Wales (10,159, lowest) — this closely tracks station count per region (established in Task 16) rather than indicating a distinct regional behavioural difference.

## 4. Behaviour by Charger Type
Raw session totals show DC_50kW chargers account for the most sessions (136,821, 47% of total) — but this is because DC_50kW is also the most common charger type (95 units). **Normalising by charger count reveals the opposite pattern**: DC_300kW (fast chargers) shows the highest utilisation intensity at **~1,721 sessions/charger**, roughly 19–22% higher than DC_50kW (1,440/charger) and DC_150kW (1,406/charger) — despite being the least common type (only 35 units).

## 5. Operational Recommendations
1. **Prioritise time-of-day and day-of-week planning over seasonal adjustments** — capacity and staffing should flex by hour and weekday/weekend, not by month, given the flat seasonal pattern.
2. **Prioritise DC_300kW (fast charger) installations in future network expansion** — existing fast chargers are utilised more intensively per unit than slower chargers, indicating unmet demand that raw totals alone would have masked.
3. **Continue treating 9am–2pm as the core operational peak window** for staffing, maintenance scheduling, and grid capacity planning, consistent with findings across Tasks 01 and 16.

## Files in this repository
- `Task7_Time_Of_Day&Day_Of_Week_Pattern_Analysis.ipynb` — full code and outputs
- `monthly_demand.csv` — seasonal (monthly) session counts
- `region_pattern.csv` — session counts by region
- `charger_type_analysis.csv` — sessions per charger by type
- `Task7.pbix` — Power BI dashboard
- `SUMMARY.md` — this file

## Conclusion
This analysis confirmed strong, actionable hourly and weekly demand patterns, but found no meaningful seasonal trend. The most valuable finding was uncovered by normalising charger-type usage: fast chargers (DC_300kW) are used more intensively per unit than slower types, despite representing the smallest share of installed chargers — directly informing a clear, evidence-based recommendation for future charger type prioritisation.
