# CadetX Virtual Work Experience — Task 03: Charger Utilisation & Efficiency Analysis

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas (Google Colab) + Power BI Desktop

## Objective
Measure usage, idle time, and bottleneck stations to optimise infrastructure and reduce congestion.

## Dataset
Same source as Task 01: `ev_charging_dataset.xlsx` (stations, chargers, sessions sheets). This task focuses on the `chargers` sheet (199 chargers across 33 stations) joined with session-level usage data.

## 1. Utilisation & Idle-Time Calculation
- Calculated total minutes used per charger by summing `session_duration_minutes` grouped by `charger_id`.
- Calculated total available minutes across the full 3-year dataset period (1,095 days × 24 hours × 60 minutes = 1,576,800 minutes).
- Derived **utilisation %** (minutes used ÷ minutes available × 100) and **idle %** (100 − utilisation %) for every charger.

## 2. Utilisation Heatmap
Built in Power BI using a Matrix visual with conditional (background color) formatting:
- Rows: `station_id` → nested `charger_id`
- Values: Average of `utilisation_pct`
- Color scale automatically highlights high-usage chargers (darker) vs low-usage chargers (lighter), making bottlenecks and underused equipment immediately visible.

## 3. Peak-Load Analysis
Built a bar chart in Power BI (hour-of-day vs total session count), reusing the hourly demand pattern established in Task 01. Confirms the same finding: demand — and therefore charger load — peaks between **9am and 1pm**, with the lowest load overnight (12am–5am).

## 4. Ranking of High/Low-Performing Chargers

**Top 5 most-used chargers (potential bottlenecks):**
| Charger | Station | Utilisation % |
|---|---|---|
| STN_001_CH_04 | STN_001 | 12.07% |
| STN_007_CH_02 | STN_007 | 12.01% |
| STN_007_CH_04 | STN_007 | 11.99% |
| STN_001_CH_01 | STN_001 | 11.72% |
| STN_007_CH_03 | STN_007 | 11.59% |

**Bottom 5 least-used chargers (underperforming):**
| Charger | Station | Utilisation % |
|---|---|---|
| STN_025_CH_02 | STN_025 | 0.73% |
| STN_027_CH_04 | STN_027 | 0.73% |
| STN_023_CH_01 | STN_023 | 0.77% |
| STN_025_CH_03 | STN_025 | 0.78% |
| STN_027_CH_06 | STN_027 | 0.81% |

**Important finding:** Cross-referencing the bottom performers against station activation data revealed that STN_023, STN_025, and STN_027 were all activated in **2024** — the most recent expansion batch. Their apparently low utilisation is therefore partly an artifact of comparing them against the full 3-year window rather than genuine underperformance. A fairer comparison would measure utilisation from each station's actual activation date.

## 5. Capacity Optimisation Recommendations
- **STN_001 and STN_007** show consistently high utilisation across multiple chargers and are strong candidates for **additional charger capacity** to reduce potential congestion and wait times.
- **STN_023, STN_025, STN_027** should not be treated as underperforming yet — their low usage is likely a function of recency (activated in 2024). Recommend re-evaluating their performance after a full 12-month operating period.
- **STN_002** shows genuinely low, consistent utilisation despite being an older station, and may warrant investigation into location factors (e.g., low regional demand, poor visibility/access) rather than simply adding more capacity there.
- Overall, capacity investment should be **prioritised at high-usage, established stations** rather than spread evenly, since demand is clearly uneven across the network.

## Files in this repository
- `Task3_Charger_Utilisation_Notebook.ipynb` — Python code (usage/idle calculations, rankings)
- `charger_usage.csv` — final calculated dataset (utilisation %, idle %, per charger)
- `Task3_Charger_Utilisation.pbix` — Power BI dashboard (heatmap + peak-load chart)
- `SUMMARY.md` — this file

## Conclusion
This analysis identified significant unevenness in charger utilisation across the network, ranging from under 1% to over 12%. By combining Python-based calculation with Power BI visualisation, the analysis produced an actionable heatmap and ranking system, while also surfacing an important caveat (activation-date bias) that prevents a misleading recommendation. Capacity investment should prioritise established high-usage stations (001, 007) over newly activated ones still building their user base.
