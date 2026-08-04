# CadetX Virtual Work Experience — Task 12: Year-over-Year Growth Analytics

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas (Google Colab) + Power BI Desktop

## Objective
Track network growth from 2022 to 2024 across stations, sessions, revenue, and customer base — for business storytelling and strategic planning.

## Dataset
`sessions_df` from `ev_charging_dataset.xlsx` (294,024 sessions), aggregated by `year`.

## 1. Growth KPIs

| Year | Total Sessions | Total Revenue | Unique Customers | Sessions per Customer |
|---|---|---|---|---|
| 2022 | 40,640 | $1,028,772 | 7,669 | ~5.3 |
| 2023 | 86,132 | $2,587,774 | 5,977 | ~14.4 |
| 2024 | 167,252 | $4,554,554 | 6,000 | ~27.9 |

## 2. YoY Comparison Dashboard
Built in Power BI, four column charts (Total Revenue, Total Sessions, Unique Customers, Sessions per Customer) arranged side by side to visually contrast growth patterns across metrics.

## 3. Trend Analysis
Sessions and revenue both **more than doubled every year**, closely tracking the station network's expansion (8 → 17 → 33 stations, established in Task 01). However, the **unique customer count remained flat — even declining slightly** (7,669 → 5,977 → 6,000), despite sessions and revenue growing more than 4x over the same period.

## 4. Growth Drivers and Inhibitors

**Primary growth driver:** Increasing usage frequency among existing customers. Average sessions per customer grew nearly **5.3x** (from ~5.3 to ~27.9) between 2022 and 2024 — this, not customer acquisition, explains almost all of the network's growth.

**Potential inhibitor / risk:** The customer base itself has not grown. Continued reliance on deepening usage among a static ~6,000-customer base represents a **growth ceiling risk** — this pattern cannot continue indefinitely, since there is a practical limit to how often any individual customer can realistically charge.

## 5. Strategic Recommendations
1. **Invest in customer acquisition** — the current growth model relies almost entirely on existing customers using the service more often; without new customers, growth will eventually plateau.
2. **Continue station network expansion** — it has proven directly effective at driving usage intensity and should remain a priority.
3. **Monitor 2025 sessions-per-customer trend closely** — if this metric plateaus or declines, it will signal that the current growth model is reaching its natural limit, and customer acquisition should become the top priority.

## Files in this repository
- `Task12_Year_over_Year_Growth_Analytics.ipynb` — full code and outputs
- `yearly_kpis.csv` — calculated growth KPIs by year
- `Task12.pbix` — Power BI dashboard
- `SUMMARY.md` — this file

## Conclusion
The network experienced strong, sustained YoY growth in sessions and revenue (both more than doubling annually), but this growth was driven almost entirely by increasing usage frequency among a static customer base rather than customer acquisition. This is both a strength (high customer loyalty and engagement) and a strategic risk (a ceiling on growth without expanding the customer base), and should inform future business strategy accordingly.
