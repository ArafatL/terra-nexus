# Terra Nexus

**An ESG and carbon analytics blueprint: one dataset, three audiences.**

Terra Nexus is a browser-based dashboard showing how a multi-site organisation could report sustainability performance to its Board, its operations teams and its regulators from a single, documented data model, without rebuilding the data for each audience.

> **Illustrative data.** All eight facilities are fictional and every figure is illustrative. The project demonstrates dashboard design, data modelling and reporting logic; it does not describe any real organisation.

**Live demo:** `https://<your-username>.github.io/terra-nexus/`

---

## The problem it addresses

Sustainability reporting usually sits in spreadsheets owned by different teams, and each framework (CSRD, ISSB, TCFD and others) asks for the same underlying numbers in a different shape. The result is repeated manual work and figures that don't reconcile between reports.

Terra Nexus models the alternative: capture each facility's data once, in one schema, and derive every view from it.

## What's inside

| Tab | Audience | What it shows |
|---|---|---|
| **Command Centre** | Board / executives | Headline KPIs with year-on-year change, carbon intensity, net-zero indicator, strategic insights |
| **Emissions Intelligence** | Sustainability team | Scope 1, 2 and 3 monthly, 2024 vs 2025, by facility |
| **Supply Chain** | Procurement | Scope 3 category breakdown |
| **Carbon Markets** | Finance | Credits held, average price, offset coverage, offset project portfolio |
| **ESG Analytics** | Board / investors | Environmental, Social and Governance scores per facility |
| **Financial Impact** | CFO | Carbon-tax exposure, green revenue, ROI per facility |
| **Regulatory** | Compliance | Readiness by framework: CSRD, ISSB, SEC, TCFD, SBTi, CDP, UAE Net Zero 2050, Singapore Green Plan |
| **Scenarios & Forecasts** | Strategy | Projected vs optimised emissions scenarios and ranked recommended actions |

A facility filter at the top switches every tab between the full portfolio and any single site.

## Run it

No build step and no install.

```bash
git clone https://github.com/<your-username>/terra-nexus.git
cd terra-nexus
# open index.html in any modern browser
```

The page loads React, Recharts and Babel from the unpkg CDN, so it needs an internet connection the first time it opens.

## Tech stack

| Layer | Choice |
|---|---|
| UI | React 18.2 (UMD build) |
| Charts | Recharts 2.12.7 |
| JSX | Babel Standalone 7.23.9, compiled in the browser |
| Styling | Inline styles from a single theme object |
| Fonts | Sora, Space Mono (Google Fonts) |
| Hosting | Any static host: GitHub Pages, Netlify, Vercel |

## Documentation

| Document | Contents |
|---|---|
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | How the app is structured, data flow, component map |
| [docs/DATA_DICTIONARY.md](docs/DATA_DICTIONARY.md) | Every field in the data model, with units |
| [docs/METHODOLOGY.md](docs/METHODOLOGY.md) | How each KPI is calculated, and the assumptions behind it |
| [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md) | Publishing to GitHub Pages, Netlify or Vercel |
| [docs/ROADMAP.md](docs/ROADMAP.md) | What a production version would add |

## Design decisions

- **One schema, many views.** Every tab reads from the same `FACILITIES` object; nothing is precomputed per view, so the numbers always reconcile.
- **Year-on-year and target status are separate signals.** A metric can be improving and still miss its target; the dashboard shows both.
- **Portfolio or single site.** Aggregations are recalculated when the facility filter changes, so every chart answers the same question at the selected scope.
- **Zero build tooling.** A single HTML file anyone can open, which suits demos and reviews.

## Author

**Arafat Lakhani** · Data & AI Analyst · Dubai, UAE
[LinkedIn](https://linkedin.com/in/arafat-lakhani) · arafatilakhani24@gmail.com

## Licence

All rights reserved. Published for portfolio review; see [LICENSE](LICENSE).
