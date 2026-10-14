# Methodology

How each figure on the dashboard is derived. `S()` sums an array, and the "selected scope" is either the whole portfolio or the single facility chosen in the filter.

## Emissions

Emissions follow the **GHG Protocol** split into three scopes:

- **Scope 1:** direct emissions from owned sources (fuel combustion, company vehicles, refrigerant leaks)
- **Scope 2:** indirect emissions from purchased electricity, heating and cooling
- **Scope 3:** other value-chain emissions (purchased goods, travel, commuting, logistics, waste)

| Metric | Formula |
|---|---|
| Total emissions (year) | S(Scope 1) + S(Scope 2) + S(Scope 3) across the selected scope |
| YoY change % | (2025 − 2024) ÷ 2024 × 100 |
| Carbon intensity | Total emissions ÷ total floor area (tCO₂e / m²) |

Negative YoY means emissions fell.

## Resources

| Metric | Formula |
|---|---|
| Electricity, water YoY % | (2025 total − 2024 total) ÷ 2024 total × 100 |
| Waste diversion rate | Waste diverted ÷ waste generated × 100 |

## ESG and risk

| Metric | Formula |
|---|---|
| Facility ESG average | (E + S + G) ÷ 3 |
| Portfolio ESG average | Mean of facility ESG averages |
| Net-zero indicator year | 2040 + round((100 − portfolio ESG average) ÷ 10) |

The net-zero indicator is a **simple heuristic for display**: a higher ESG average brings the indicated year closer. It is not a science-based target, and a real version would use an SBTi-validated reduction pathway.

## Financial

| Metric | Formula |
|---|---|
| Total carbon-tax exposure | Sum of facility `fin.ctax` |
| Total green revenue | Sum of facility `fin.grev` |
| Average ROI | Mean of facility `fin.roi` |
| Credit portfolio value | Credits held × average price |

## Scenarios & Forecasts

The scenario tab compares three lines: actual emissions, a **projected** path and an **optimised** path that assumes the recommended actions are taken. Projection values, confidence figures and the recommended-action impacts are **illustrative inputs**, not output from a trained model.

In a production version this tab would be driven by a forecasting model (for example seasonal time-series per facility, trained on several years of monthly data) and back-tested before any accuracy figure is shown.

## Data quality rules a production version would enforce

- No negative consumption or emissions values
- Twelve monthly values per year per metric; missing months flagged, not zero-filled
- Diverted waste never exceeds generated waste
- Emission factors versioned and recorded per facility and year
- Every figure traceable to a source document and submission date
