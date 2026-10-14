# Data dictionary

All data is **illustrative**. Facilities are fictional and figures are invented to exercise the dashboard.

## `FACILITIES`

An object keyed by facility code (`CC-XXX`: ISO country code plus city abbreviation).

| Code | Name | City | Sector | Floor area (m²) | Employees |
|---|---|---|---|---:|---:|
| SG-SIN | Singapore Mixed-Use Campus | Singapore | Mixed-Use | 155,000 | 4,200 |
| US-NYC | New York Office Tower | New York | Commercial RE | 98,000 | 2,800 |
| DE-FRA | Frankfurt Green Campus | Frankfurt | Technology | 45,000 | 1,600 |
| AE-DXB | Dubai Financial District Hub | Dubai | Financial Services | 62,000 | 1,900 |
| JP-TKY | Tokyo Net-Zero Tower | Tokyo | Manufacturing HQ | 72,000 | 2,200 |
| GB-LDN | London ESG Centre | London | Banking & Finance | 54,000 | 1,800 |
| BR-SAO | São Paulo Green Complex | São Paulo | Agri-Tech | 38,000 | 1,200 |
| AU-SYD | Sydney Carbon-Neutral Hub | Sydney | Energy & Utilities | 48,000 | 1,400 |

### Fields per facility

| Field | Type | Unit | Description |
|---|---|---|---|
| `f` | string | | Display name |
| `city`, `country` | string | | Location; `country` is ISO 3166 alpha-2 |
| `sector` | string | | Business sector |
| `sqm` | number | m² | Gross floor area, used for carbon intensity |
| `emp` | number | people | Headcount |
| `s1.a`, `s1.b` | number[12] | tCO₂e | Scope 1 monthly; `a` = 2024, `b` = 2025 |
| `s2.a`, `s2.b` | number[12] | tCO₂e | Scope 2 monthly |
| `s3.a`, `s3.b` | number[12] | tCO₂e | Scope 3 monthly |
| `elec.a`, `elec.b` | number[12] | MWh (assumed) | Electricity consumption |
| `water.a`, `water.b` | number[12] | m³ (assumed) | Water consumption |
| `waste.gen`, `waste.div` | number[12] | tonnes | Waste generated; waste diverted from landfill |
| `carbon.credits` | number | tCO₂e | Carbon credits held |
| `carbon.price` | number | USD / tCO₂e | Average credit price |
| `carbon.offset` | number | % | Share of emissions offset |
| `esg.e`, `esg.s`, `esg.g` | number | score 0–100 | Environmental, Social, Governance scores |
| `ai.risk` | number | score 0–100 | Climate risk score (higher = more exposed) |
| `ai.conf` | number | % | Confidence assigned to the scenario projection |
| `ai.pred` | number | % | Projected emissions change for the next year |
| `fin.ctax` | number | USD M | Annual carbon-tax exposure |
| `fin.grev` | number | USD M | Green revenue |
| `fin.roi` | number | % | Return on sustainability investment |
| `compliance.csrd` / `.issb` / `.sec` / `.tcfd` | number | % | Readiness against each framework |

Units marked *assumed* are not labelled in the dashboard itself; they are the units the values were designed around.

The `ai.*` fields keep their original key names for compatibility. They hold illustrative scenario values, not the output of a trained model.

## `SCOPE_CATS`

Portfolio emissions by GHG Protocol category, as a share of the total (%).

| Category | Scope | Share % |
|---|:-:|---:|
| Purchased Electricity | 2 | 38.2 |
| District Cooling/Heating | 2 | 14.8 |
| Natural Gas (Stationary) | 1 | 12.4 |
| Purchased Goods | 3 | 8.6 |
| Company Vehicles | 1 | 5.2 |
| Upstream Transport | 3 | 5.1 |
| Business Travel | 3 | 4.8 |
| Employee Commuting | 3 | 3.2 |
| Refrigerant Leaks | 1 | 3.1 |
| Waste in Operations | 3 | 2.8 |
| Downstream Logistics | 3 | 1.8 |

## `REGULATIONS`

| Framework | Region | Deadline | Status | Readiness % |
|---|---|---|---|---:|
| CSRD | EU | 2026 Q1 | On Track | 82 |
| SEC Climate | US | 2026 Q2 | At Risk | 68 |
| ISSB S1/S2 | Global | 2025 Q4 | Compliant | 91 |
| TCFD | Global | Ongoing | Compliant | 88 |
| SBTi Validation | Global | 2026 Q3 | In Progress | 74 |
| CDP Disclosure | Global | 2025 Q3 | Submitted | 95 |
| UAE Net Zero 2050 | GCC | 2050 | On Track | 45 |
| Singapore Green Plan | APAC | 2030 | On Track | 62 |

Statuses and dates are illustrative and do not reflect the current legal status of any framework.
