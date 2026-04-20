# Tech Note: HMT Green Book 2022 + DfT TAG for Transport Appraisal

> **Template Origin**: Official | **ArcKit Version**: 4.8.0 | **Command**: `/arckit.research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | green-book-tag-appraisal |
| **Document Type** | Tech Note |
| **Project** | DfT Transforming City Regions (discovery, pre-requirements) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | Biannual (TAG Data Book updates twice yearly) |
| **Next Review Date** | 2026-11-20 |
| **Owner** | Mark Craddock |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Architecture WG |
| **Source Research** | dft-transforming-city-regions-research-v1.0 |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-04-20 | ArcKit AI | Initial creation from `/arckit.research` agent | PENDING | PENDING |

---

## Summary

Any technology platform administering transport grants in England must operate against two authoritative assurance frameworks: **HM Treasury's Green Book 2022** (Five Case Model, with SOC / OBC / FBC progression) and the **Department for Transport's Transport Analysis Guidance (TAG)**, which is the transport-specific economic appraisal methodology that sits inside the Economic Case. There is no off-the-shelf UK public-sector SaaS product that natively represents either. This is the single biggest custom-build requirement for any DfT / MCA funding platform.

## Key Findings

### Green Book 2022 (Five Case Model)

- Published 31 March 2022 by HMT; reviewed June 2025 (Green Book Review 2025 — findings and actions).
- Five cases, all of which must be robust for a business case to progress:
  - **Strategic**: fit with policy, objectives, stakeholder priorities.
  - **Economic**: value for money — including BCR and wider value assessment.
  - **Commercial**: procurement strategy, market, risk allocation.
  - **Financial**: affordability, funding profile, drawdown.
  - **Management**: delivery capacity, risks, governance.
- Progression: **SOC (Strategic Outline Case) → OBC (Outline Business Case) → FBC (Full Business Case)**.
- Green Book Review 2025 aims to simplify and clarify; expect further updates.

### DfT Transport Analysis Guidance (TAG)

- TAG is DfT's transport-specific appraisal guidance, formerly known as **WebTAG**.
- Underpins the Economic Case for transport business cases.
- Latest structural document: **TAG Transport Appraisal Process (November 2025)**.
- Most recent methodological update bundle: **April/May 2025** (published in advance to allow lead time).
- Central to TAG: the **TAG Data Book** — a set of Excel-based authoritative values (time, reliability, accident costs, carbon, wider economic impacts, etc.). Updated twice yearly, typically May and November.
- Key TAG Units cross-cut transport appraisal:
  - A1.x — Cost-benefit analysis principles
  - A2.x — Scheme costs
  - A3.x — Environmental impacts
  - A4.x — Social & distributional impacts
  - A5.x — Wider impacts
  - M-series — Modelling

### DfT Value for Money Framework

- Current version: May 2025.
- Categorises VfM as Very Poor / Poor / Low / Medium / High / Very High based on BCR plus wider value considerations.
- Feeds the Economic Case conclusion.

### Tooling landscape

- **No UK public-sector SaaS product is TAG-native today.**
- The TAG Data Book is consumed primarily via Excel workbooks and custom analytics (Python, R, Power BI).
- Bespoke microservices to expose TAG values as an API, or to compute BCR given scheme inputs, do not exist as a shared public good.
- Consultancies (Sweco, Mott MacDonald, Jacobs, WSP, Arup, Steer, Atkins) use bespoke internal tooling, often proprietary.

### Implications for the DfT Transforming City Regions platform

- Any solution will need:
  - **Five-case templates** for SOC/OBC/FBC, configurable per scheme type.
  - **DP1–DP7 (or equivalent) decision-gate workflow**, with assurance reviewer queues, sign-off captures, and audit trails.
  - **TAG-aware appraisal microservice**: a small, owned-by-DfT service that takes scheme inputs (capital cost, length, modal shift assumptions, operating period), pulls TAG Data Book values (ideally machine-readable), and returns BCR + VfM category.
  - **Benefits-realisation / MRM capture** linked to original business-case assumptions, enabling ex-post evaluation per DfT's evaluation strategy.

## Relevance to Projects

- DfT Transforming City Regions Funding (discovery, 2026-04-20)
- Any future transport capital programme requiring Green Book/TAG appraisal
- Adjacent departments (DESNZ Net Zero capital, DHSC health capital, DLUHC regeneration) use Green Book but not TAG — a Green Book engine is reusable, TAG is transport-specific.

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| *None provided* | — | — | — | — |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| — | — | — | — | — |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit.research` agent
**Generated on**: 2026-04-20
**ArcKit Version**: 4.8.0
**Project**: DfT Transforming City Regions Funding
**Model**: Claude Opus 4.7 (1M context)
