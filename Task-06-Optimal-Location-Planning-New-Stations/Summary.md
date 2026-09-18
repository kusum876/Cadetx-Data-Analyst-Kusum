
# CadetX Virtual Work Experience — Task 06: Optimal Location Planning for New Stations

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas (Google Colab) + Power BI Desktop

## Objective
Analyse regional demand, utilisation, and customer density to recommend where new stations should be built.

## Dataset
`sessions_df` and `stations_df` from `ev_charging_dataset.xlsx`, aggregated by UK region (9 regions, 33 stations).

## 1. Regional Demand vs Supply (Gap Analysis)
Calculated sessions-per-station and customers-per-station for each region, normalising demand against existing supply rather than relying on raw totals alone.

| Region | Sessions/Station | Customers/Station |
|---|---|---|
| Yorkshire & Humber | 10,234 | 2,438 |
| Wales | 10,159 | 3,721 |
| North East | 10,146 | 1,882 |
| South West | 10,134 | 1,892 |
| Midlands | 10,120 | 1,274 |
| North West | 9,398 | 952 |
| London | 8,152 | 1,188 |
| Scotland | 6,747 | 1,630 |
| South East | 6,292 | 1,290 |

**Key finding:** Wales, despite having only 1 station, shows the highest customer load per station (3,721 unique customers) — nearly 4x the rate seen in North West (952). This indicates significant unmet demand relative to available infrastructure.

## 2. Location Scoring Model
Combined sessions-per-station and customers-per-station into a normalised (0–100) **expansion priority score** per region.

| Region | Expansion Priority Score |
|---|---|
| **Wales** | **99.05** |
| Yorkshire & Humber | 76.82 |
| South West | 65.69 |
| North East | 65.68 |
| Midlands | 54.35 |
| North West | 39.40 |
| London | 27.84 |
| Scotland | 18.02 |
| South East | 6.10 |

## 3. Map-Based Visualisation
A geographic map visualisation was attempted in Power BI but encountered technical limitations with automatic location-matching for UK regional names. A ranked bar chart of the expansion priority score by region is provided instead, conveying the same prioritisation findings clearly.

## 4. Expansion Strategy Report
Wales is the single highest-priority region for expansion (priority score: 99.05), driven by exceptionally high demand relative to its minimal existing infrastructure — its one station serves nearly 4x the customer load of stations in better-served regions like North West. Yorkshire & Humber (76.82) and South West (65.69) follow as strong secondary priorities. In contrast, South East (6.10) and Scotland (18.02) show comparatively low demand intensity relative to their existing station count, indicating these regions are currently adequately served and should not be prioritised for near-term expansion.

**Recommendation:** Allocate new station investment primarily to Wales and Yorkshire & Humber, where existing infrastructure is most strained relative to demonstrated customer demand, rather than continuing to expand in already well-served regions like North West or London.

## Files in this repository
- `Task_6_Optimal_Location_Planning_for_New_Stations.ipynb` — full code and outputs
- `gap_analysis.csv` — regional demand/supply gap and priority scores
- `Task 6.pbix` — Power BI dashboard (bar chart)
- `SUMMARY.md` — this file

## Conclusion
This analysis identified Wales as a clear, evidence-backed priority for new station investment — a finding that raw total figures alone (used in earlier tasks) would have obscured, since Wales appears "small" by total volume but is in fact the most under-served region relative to its demand. This demonstrates the value of per-unit normalisation over raw totals for infrastructure planning decisions.
