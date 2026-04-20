# Tech Note: CRSTS / Transforming Cities / Integrated Settlement Landscape

> **Template Origin**: Official | **ArcKit Version**: 4.8.0 | **Command**: `/arckit.research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | crsts-integrated-settlement-landscape |
| **Document Type** | Tech Note |
| **Project** | DfT Transforming City Regions (discovery, pre-requirements) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-07-20 |
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

A concise reference to the DfT city-region transport funding family and the Integrated Settlement overlay: who receives, what value, over which horizon, and what the administrative data model looks like. Intended to be the "north star" fact-sheet carried into requirements, principles, SOBC and Wardley work.

## Key Findings

### Programme family (as of April 2026)

- **Transforming Cities Fund (TCF)**: £2.5bn competitive + £1.28bn co-developed, originally 2018/19–2022/23, extended to March 2025, now **closing out**. 12 shortlisted city regions. National evaluation (UWE Bristol, Sustrans, Transport for Quality of Life) ongoing.
- **CRSTS1**: £5.7bn, 2022/23–2026/27, 8 MCAs. **Live, year 4/5**. Delivery plans confirmed; quarterly MRM cycle embedded; 7-activity / DP1–DP7 assurance patterns (WYCA pattern).
- **CRSTS2 / Transport for City Regions (TCR)**: **£15.6bn, 2027/28–2031/32**, 9 MCAs (original 8 + East Midlands CCA). £500m+ brought forward to 2025–26/2026–27. Announced at Spending Review June 2025.
  - GMCA: £2.5bn
  - WMCA: £2.4bn
  - EMCCA: £2bn
  - Liverpool City Region: £1.6bn
  - Tees Valley: £978m
  - Remainder split across WYCA, SYMCA, NECA, West of England CA (full table yet to publish)
- **Local Transport Grant (LTG)**: £2.3bn from 2025 for non-CRSTS areas.
- **Network North / redirected HS2 funding**: £4.7bn (North £2.5bn + Midlands £2.2bn), under review under current administration.
- **Bus Service Improvement Plans (BSIPs)**: 13 separate funding streams 2020/21–2024/25; only 19% of capital delivered by December 2024 per NAO.

### Integrated Settlement (the transformational overlay)

- **Policy**: HMT-led single-pot funding model with an outcomes framework, replacing scheme-by-scheme departmental approvals.
- **Live (April 2025)**: GMCA (£650m first-year settlement), WMCA.
- **Joining April 2026**: North East MCA, South Yorkshire MCA, West Yorkshire MCA, Liverpool City Region CA, Greater London Authority.
- **Multi-year**: first IS ran to March 2026; multi-year settlement April 2026–April 2029 now confirmed.
- **Implication for tech**: data model shifts from scheme-centric to **outcome + indicator-centric**, with triggers for drawdown based on outcome achievement.

### Governance and assurance fabric

- **Green Book 2022 (HMT)**: five-case model (strategic, economic, commercial, financial, management). SOC → OBC → FBC progression.
- **Green Book Review 2025** (June 2025) aimed at simplification.
- **DfT TAG / Transport Analysis Guidance**: April 2025 update bundle, November 2025 TAG Transport Appraisal Process document; TAG Data Book updated twice yearly.
- **DfT Value for Money Framework**: May 2025 version.
- **NISTA** (National Infrastructure and Service Transformation Authority): HMT + Cabinet Office, live 1 April 2025. Merger of IPA + NIC. Becky Wood CEO. Holds £530bn / 780-project pipeline.
- **IPA Gateway reviews**: now transitioning to NISTA assurance processes.
- **Government Functional Standards**: GovS 002 (Project Delivery), GovS 006 (Finance), GovS 007 (Security), GovS 008 (Commercial), GovS 013 (Counter Fraud).
- **Technology Code of Practice**: 13 points, last update 7 July 2025 (added Point 12 — sustainability).
- **Secure by Design**: Group 1 (ministerial departments / CNI) already mandated; Group 2 (ALBs, executive agencies) from January 2025.

### Data-model implications for any DfT platform

- Must hold scheme, claim, drawdown, and outcome/indicator entities.
- Must federate with 9 MCA systems and NISTA reporting interfaces.
- Must integrate with GGIS (cross-gov grants register) and optionally Spotlight (due-diligence).
- Must serve both DfT (assurance / reporting) and MCA (delivery) personas.
- Retention obligations: TNA 20-year rule + NAO / PAC audit horizons.

## Relevance to Projects

- DfT Transforming City Regions Funding (discovery, 2026-04-20) — primary project
- Future DWP / DESNZ / MHCLG / NHS England capital grant programmes — this framework is recognisable across those domains.

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
