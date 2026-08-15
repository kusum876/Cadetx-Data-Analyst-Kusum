# CadetX Virtual Work Experience — Task 13: Station Performance Ranking System

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas (Google Colab) + Power BI Desktop

## Objective
Score stations on utilisation, revenue, retention, and energy delivered to identify top and underperforming sites.

## Dataset
`sessions_df` and `stations_df` from `ev_charging_dataset.xlsx`, aggregated by `station_id` across all 33 stations.

## 1. Performance Scoring Model
Calculated four raw metrics per station: total sessions (utilisation), total revenue, sessions-per-customer (retention), and total kWh delivered (energy). Each metric was normalized to a 0–100 scale using min-max normalization, then averaged into a single `overall_score` per station.

## 2. Station Ranking Table
Built in Power BI with conditional (background color) formatting, sorted by `overall_score` from highest to lowest.

**Top performer:** STN_002 (score: 99.67) — strong across all four metrics.
**Lowest performers:** All 16 stations scoring under 15 were activated in **2024**.

## 3. KPI Comparison Charts
Built a column chart in Power BI comparing `overall_score` across all 33 stations, visually highlighting the performance gap between established and newly activated stations.

## 4. Underperforming Station Analysis
Cross-referencing the lowest-ranked stations against `stations_df` confirmed that **all 16 stations scoring under 15 were activated in 2024** — the same activation-year bias identified in Task 03's utilisation analysis. Raw cumulative totals unfairly disadvantage newer stations that have had less time to accumulate sessions, revenue, and customers. Among established (2022–2023) stations, **STN_001** (score: 78.90) is notably the weakest performer in its cohort, despite similar operating history to top performer STN_002 — this cannot be explained by station age and warrants further investigation.

## 5. Improvement Action Plan
1. **Do not treat 2024-activated stations as genuinely underperforming** — re-evaluate their ranking after a full 12-month operating period using an age-normalized comparison.
2. **Investigate STN_001 specifically** — as an established station with a below-cohort score, potential causes (location, accessibility, equipment condition) should be reviewed.
3. **Study STN_002 as a benchmark** — understanding what drives its consistently top performance across all four metrics could inform improvements at underperforming established stations.
4. **Future methodology improvement:** normalize each metric by days-operational before scoring, to enable a fair comparison across stations regardless of activation date.

## Files in this repository
- `Task13_Station_Performance_Ranking_System.ipynb` — full code and outputs
- `station_performance_ranking.csv` — final scored and ranked dataset
- `Task13.pbix` — Power BI dashboard
- `SUMMARY.md` — this file

## Conclusion
This analysis produced a combined performance score for all 33 stations, correctly identifying STN_002 as the top performer and STN_001 as an underperformer worth investigating within its cohort. Critically, the analysis also identified and explained an activation-year bias affecting the ranking — avoiding a misleading conclusion that all 2024 stations are "failing," when the data instead shows they simply haven't had time to accumulate activity yet.
