# Architecture

Terra Nexus is a single static HTML file. All data, logic and presentation live in `index.html`.

## Runtime overview

```
index.html
 ├── <head>   fonts, global CSS, keyframe animations, loading screen
 ├── CDN scripts: React 18.2 · ReactDOM · prop-types · Recharts 2.12.7 · Babel Standalone
 └── <script type="text/babel">
       ├── Constants      MO (months), T (theme tokens)
       ├── Data layer     FACILITIES, SCOPE_CATS, REGULATIONS
       ├── Helpers        S (sum), P (% change), F / FP / FM (formatters)
       ├── Components     Metric, Sec (section header), Card, TT (chart tooltip)
       └── Dashboard()    state, derived data, eight tab renderers, layout
```

On load, Babel compiles the JSX in the browser, React mounts `Dashboard` into `#root`, and the loading screen is hidden.

## Data flow

```
FACILITIES (static object, 8 sites × 12 months × 2 years)
      │
      ├── facility filter (state: "ALL" or a site code)
      │
      ├── agg  ── useMemo ──► annual totals for the selected scope
      ├── md   ── useMemo ──► 12 monthly rows for the selected scope
      └── hc   ── useMemo ──► one comparison row per facility
                                 │
                                 ▼
              renderExec · renderEmissions · renderScope · renderCarbon
              renderESG  · renderFin       · renderCompliance · renderAI
```

Every view reads from these three derived structures. Changing the facility filter recalculates `agg` and `md`, so every tab updates together.

## State

| State | Type | Purpose |
|---|---|---|
| `tab` | string | Active tab id: `exec`, `emissions`, `scope3`, `carbon`, `esg`, `fin`, `compliance`, `ai` |
| `facility` | string | `"ALL"` or a facility code such as `"AE-DXB"` |

## Derived data

| Name | Built from | Contents |
|---|---|---|
| `agg` | selected facilities | Annual totals: Scope 1–3 for both years, electricity, water, waste generated and diverted, floor area, employees, credits, carbon tax, green revenue |
| `md` | selected facilities | One row per month with Scope 1–3, electricity and water for both years |
| `hc` | all facilities | One row per facility with YoY changes, diversion rate, average ESG score, risk score, financials |

## Components

| Component | Role |
|---|---|
| `Metric` | KPI tile: label, value, prior-year line, YoY badge, optional accent and badge |
| `Sec` | Section heading with optional subtitle and tag |
| `Card` | Panel container |
| `TT` | Shared chart tooltip |

## Adding a facility

1. Add an entry to `FACILITIES` following the schema in [DATA_DICTIONARY.md](DATA_DICTIONARY.md).
2. Use a code in the form `CC-XXX` (country plus city).

No other change is needed. Every aggregate, chart and table iterates over the object's keys.

## Known limitations

- Babel compiles in the browser, which adds a short delay on first load. A production build would precompile with Vite or similar.
- Data is embedded in the file. A production version would load it from an API or database (see [ROADMAP.md](ROADMAP.md)).
