# Roadmap

What would turn this blueprint into a production reporting system.

## Phase 1: Real data

- Move data out of the HTML into a database (PostgreSQL) behind a small API
- Standard monthly submission template per facility, validated on upload
- Versioned emission factors by country and year
- Audit trail: who submitted each figure, when, and from which source

## Phase 2: Governance

- Role-based access: Board, facility manager, compliance, auditor
- KPI register: definition, owner, frequency and deadline for every metric
- Submission tracker showing outstanding data per owner
- Framework mapping table so each KPI is tagged to the CSRD, ISSB or TCFD disclosure it feeds

## Phase 3: Analytics

- Forecasting model per facility, back-tested, with real accuracy reporting
- Science-based reduction pathway replacing the display heuristic for the net-zero year
- Scenario modelling for capital projects (renewable PPA, HVAC upgrades) with cost per tonne abated

## Phase 4: Delivery

- Precompiled production build (Vite) for faster load
- Scheduled PDF Board pack
- Power BI connector for teams that report there
