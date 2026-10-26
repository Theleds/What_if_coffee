# What_if_coffee
# Agroclimatic Analysis: Impact of Climate Variability and Water Excess on Coffee Yield
### Case Study: Ciudad Bolívar, Antioquia, Colombia (2015–2024)

[![Tableau Public](https://img.shields.io/badge/Tableau-Interactive%20Dashboard-E97627?logo=tableau&logoColor=white)](https://public.tableau.com/app/profile/juan.arosa.orjuela/viz/Redimientodelcafefrentealatemperatura/Dashboard1)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Executive Summary

While water availability is essential for crop development, excessive precipitation in high-altitude Andean coffee ecosystems can trigger severe agronomic setbacks. This project investigates the quantitative relationship between multi-source hydrometeorological indicators and annual Arabica coffee productivity in **Ciudad Bolívar, Antioquia**—one of Colombia’s premier coffee-producing municipalities.

By consolidating 10 years of monthly climatological records from **IDEAM** (station: *La Mansa [11025010]*) with official municipal agricultural evaluations (**EVA / UPRA**), this analysis demonstrates a **statistically significant negative correlation ($r = -0.647$, $p = 0.043$)** between annual rainfall and coffee yield, driven by water saturation, root asphyxia, reduced flowering, and heightened fungal pressure during La Niña events.

---

## Key Statistical Findings

| Metric | Value | Interpretation |
|---|---|---|
| **Precipitation vs. Yield Correlation (r)** | **-0.647** | Strong negative relationship; excess precipitation dampens yield |
| **Coefficient of Determination (R²)** | **0.418** | ~41.8% of yield variance is explained by annual rainfall alone |
| **Statistical Significance (p-value)** | **0.043** | Significant at the 95% confidence level (p < 0.05) |
| **Historic Peak Rainfall (2021)** | **3,099.2 mm** | Critical trough: coincided with an all-time low yield of **0.92 t/ha** |
| **Average Baseline Yield** | **1.23 t/ha** | Normal productivity range across the 2015–2024 decade |
| **Temperature vs. Yield Correlation (r)** | **+0.371** | Moderate positive correlation; warmer, drier cycles favored productivity |

### The Water Saturation Paradox
In 2021, intense La Niña conditions drove municipal rainfall to a record **3,099.2 mm**, resulting in a **25.2% drop in coffee yield** compared to the multi-year baseline (1.23 t/ha).
---

## Interactive Dashboard (Tableau)

An interactive dashboard was developed in **Tableau** to present executive insights and dynamic visual storytelling.

<img width="999" height="799" alt="Rendimiento_cafe_temperatura" src="https://github.com/user-attachments/assets/da3eb91e-245d-4cfa-a8dd-ac990a2b2bd4" />




### Dashboard Visual Features:
- **Executive KPI Cards:** Tracking baseline average yield (1.23t/ha) and all-time record rainfall (3,099 mm in 2021).
- **Dual-Axis Time Series:** Overlaying annual precipitation totals (bars) with annual coffee yields (line) across 2015–2024.
- **Parametric Scatter Plot & Trend Line:** Highlighting data clustering, linear slope (-0.000245), and the outlier severity of the 2021–2022 La Niña cycle.

👉 **[Explore the Interactive Dashboard on Tableau Public](https://public.tableau.com/app/profile/juan.arosa.orjuela/viz/Redimientodelcafefrentealatemperatura/Dashboard1)**

---

## Data Pipeline & Methodology

```text
[ IDEAM Weather Records (CSV) ]      [ UPRA / EVA Agricultural Data (CSV) ]
  - Precipitation (Monthly)            - Area Harvested (ha)
  - Mean Temperature (Monthly)         - Production (ton)
  - Bright Sunshine (Monthly)          - Yield (ton/ha)
                 │                                    │
                 └───► [ Python / Pandas ETL ] ◄──────┘
                         - UTF-8-BOM sanitization
                         - Comma/dot decimal formatting
                         - Inner merge on Station & Date
                         - Annual feature aggregation
                                      │
                                      ▼
                        [ datos_cafe_clima_tableau.csv ]
                                      │
                                      ▼
                        [ Tableau Public Dashboard ]
