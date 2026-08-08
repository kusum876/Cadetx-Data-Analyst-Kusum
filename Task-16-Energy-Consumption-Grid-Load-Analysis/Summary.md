
# CadetX Virtual Work Experience — Task 16: Energy Consumption & Grid Load Analysis

**Intern:** Kusum Chhetri (Data Analyst Trainee)
**Cohort:** CX-2026-ECDS-02
**Tools Used:** Python, pandas, Prophet (Google Colab) + Power BI Desktop

## Objective
Analyse total kWh delivered, peak load times, and regional energy demand to support grid planning and sustainability.

## Dataset
`sessions_df` from `ev_charging_dataset.xlsx` (294,024 sessions), using the `energy_kwh` column, aggregated by station, region, and hour.

## 1. Total Energy Delivered per Station/Region
Calculated total kWh delivered per station (33 stations) and per region (9 UK regions). Built visualisations in Power BI to present both breakdowns.

**Top region by total energy:** North West (3,005,135 kWh)
**Lowest region by total energy:** Wales (335,024 kWh)

## 2. Peak Load Analysis
Aggregated energy delivery by hour of day across the full dataset. Grid load follows the same pattern as session demand (Task 01): low overnight (~125,000 kWh at 12am-4am), rising sharply from 5am, and **peaking between 10am and 2pm** at approximately **1.12–1.13 million kWh per hour** — roughly 9x the overnight low.

## 3. Grid Stress Indicators
Normalising total energy by station count revealed a different picture than raw totals suggest. While North West has the highest *total* energy (due to having the most stations, 7), it ranks only 5th in energy delivered *per station*. The regions with the highest per-station load — indicating greater localised grid stress relative to infrastructure size — are:

| Region | Stations | Avg kWh/Station |
|---|---|---|
| South West | 3 | 526,832 |
| Midlands | 5 | 515,342 |
| North East | 3 | 466,017 |

This suggests grid capacity planning should prioritise these regions' per-connection load capacity, not just regions with the highest total volume.

## 4. Energy Forecasting Model
Built a Prophet forecasting model on daily total energy delivered (kWh), trained on the full 3-year dataset. The model forecasts continued growth, projecting daily energy delivery of approximately **29,500 kWh** by late March 2025 (compared to ~5,000-6,000 kWh/day in early 2022) — a roughly 5x increase, consistent with the network growth pattern identified in Task 12.

## 5. Sustainability and Grid-Impact Report
Total energy delivery has grown roughly 5x since 2022, driven by both network expansion (Task 01) and increasing usage intensity per customer (Task 12). Daily peak grid load consistently occurs between 10am and 2pm, with direct implications for local grid capacity during business hours. Regionally, South West, Midlands, and North East show the highest energy demand per individual station, indicating potential localised grid stress despite having fewer total stations than regions like North West. As the network continues to grow, proactive grid capacity planning — particularly during peak windows and in high-per-station-load regions — will be necessary. Demand-response strategies, such as off-peak charging incentives, could help flatten peak load and improve overall grid sustainability.

## Files in this repository
- `Task16_Energy_Consumption_&_Grid_Load_Analysis.ipynb` — full code and outputs
- `station_energy.csv` — total kWh per station
- `region_energy_per_station.csv` — regional energy, normalised per station
- `hourly_energy.csv` — hourly energy load pattern
- `Task16.pbix` — Power BI dashboard
- `SUMMARY.md` — this file

## Conclusion
This analysis found that grid load peaks sharply between 10am-2pm, and that true regional grid stress (measured per-station) differs meaningfully from raw regional totals — South West, Midlands, and North East face the greatest localised demand intensity, not North West despite its highest total volume. With energy demand forecast to continue growing roughly 5x its 2022 levels, proactive grid capacity planning in these specific regions and time windows is recommended.
