# CadetX Virtual Work Experience — Task 08: Dynamic Pricing Recommendation System

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas (Google Colab) + Power BI Desktop

## Objective
Suggest optimal prices by demand, time, region, and charger type to maximise revenue while keeping fairness.

## Dataset
`sessions_df` from `ev_charging_dataset.xlsx` (294,024 sessions), analysing `price_per_kwh`, `total_cost`, and session timing by hour.

## 1. Demand-Based Pricing Model
Analysed current pricing against actual hourly demand. Found that the network already applies a pricing premium (~$0.637 vs ~$0.579 baseline, a ~10% increase) during hours 16:00–20:00. However, this premium window does **not** align with the network's true peak demand: session volume during 16:00–20:00 (7,959–18,750 sessions) is already lower than the genuine peak period, 10:00–14:00 (23,945–24,214 sessions), which is currently priced at the standard baseline rate.

## 2. Price Optimisation Engine
Built a simulation shifting the existing 10% premium from the misaligned 16:00–20:00 window to the true peak window (10:00–14:00), while returning 16:00–20:00 to baseline pricing — without introducing any new pricing complexity, simply correcting the timing.

## 3. Revenue Uplift Simulation

| Scenario | Total Revenue |
|---|---|
| Current pricing | $8,171,100.12 |
| Repriced (premium shifted to true peak) | $8,316,719.93 |
| **Net uplift** | **+$145,619.81 (+1.78%)** |

## 4. Peak/Off-Peak Pricing Strategy
**Recommendation:** Apply the premium price (~10% above baseline) to hours 10:00–14:00 instead of 16:00–20:00. Return 16:00–20:00 to standard baseline pricing, since demand during this window has already declined from the true peak. This single timing correction — without any new pricing model complexity — is projected to generate an additional $145,620 in revenue (+1.78%).

## 5. Pricing Dashboard
Built in Power BI: a comparison column chart showing current vs. simulated revenue by hour, and a chart showing the current price structure by hour, visually highlighting the premium-pricing misalignment.

## Files in this repository
- `Task_8_Dynamic_Pricing_Recommendation_System.ipynb` — full code and outputs
- `pricing_simulation.csv` — hourly demand, current price, and revenue simulation
- `Task8.pbix` — Power BI dashboard
- `SUMMARY.md` — this file

## Conclusion
This analysis identified a clear misalignment between the network's existing pricing premium and its actual peak demand hours. By simulating a correction — shifting the premium from a declining-demand window (16:00–20:00) to the true peak window (10:00–14:00) — the model projects a $145,620 (1.78%) revenue uplift with no change to overall pricing complexity, representing a low-risk, high-confidence recommendation grounded directly in observed demand data.
