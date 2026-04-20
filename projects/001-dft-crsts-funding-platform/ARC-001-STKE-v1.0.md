# Stakeholder Drivers & Goals Analysis: DfT CRSTS Funding Platform

> **Template Origin**: Official | **ArcKit Version**: 4.8.0 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis |
| **Project** | DfT CRSTS Funding Platform (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-07-20 |
| **Owner** | Mark Craddock, Enterprise Architect (DfT, prospective) |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | DfT Rail, Places & Local Transport DG; HMT PFM team; NISTA Assurance; MHCLG Digital (Funding Service team); MCA digital leads (9); Cabinet Office Grants Function |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-04-20 | ArcKit AI (Claude Opus 4.7) | Initial creation from `/arckit:stakeholders` command, seeded from discovery research in 000-global/external | PENDING | PENDING |

---

## Executive Summary

### Purpose

This document identifies the stakeholder ecosystem for a shared administrative platform supporting DfT's city-region transport funding programmes (CRSTS1, CRSTS2, TCR, and the Integrated Settlement). Unlike a single-authority project, this initiative sits at a **federated interface** between a central department (DfT) and nine Mayoral Combined Authorities, underneath HMT spending control and NISTA assurance, and alongside a strategic reuse opportunity (MHCLG Funding Service) [DFSN-C1]. Stakeholder mapping must therefore treat the 9 MCAs as near-peer participants rather than beneficiaries.

### Key Findings

- The **policy trajectory is from scheme approver to outcomes steward** — GMCA and WMCA are already on the Integrated Settlement (April 2025) and five more MCAs plus the GLA follow in April 2026 [DFSN-C2]. This shifts the "customer" of the platform from DfT assurance officers toward MCA portfolio leads and NISTA analysts.
- **NISTA (IPA + NIC merger, live 1 April 2025) holds the £530bn / 780-project pipeline** and is now the senior assurance stakeholder for any DfT transport capital platform [DFSN-C3]. It did not exist when most current systems were commissioned — it is a new governance interlocutor.
- **Conflict risk is highest between HMT/NISTA and MCA Mayors**: HMT wants scheme-level visibility and outcome evidence; devolved Mayors want fewer strings, less reporting, and local flexibility. The platform is the meeting-point of that tension.
- **A reuse path (MHCLG Funding Service) exists** and reframes stakeholder engagement: MHCLG Digital becomes a strategic partner, not a vendor [DFSN-C4]. Failing to engage them early is a governance risk, not just a technical one.

### Critical Success Factors

- **CSF-1**: Secure SRO appointment at DfT Director level (DG-sponsored) with explicit mandate covering all 9 MCAs and NISTA interface.
- **CSF-2**: Reach a written technical partnership agreement with MHCLG Digital (Funding Service team) on reuse-or-fork strategy before SOC submission.
- **CSF-3**: Obtain signed engagement commitment from at least 5 of the 9 MCAs (the 5 on Integrated Settlement from April 2026) before requirements freeze.
- **CSF-4**: Align platform capability to NISTA's outcomes-reporting schema before beta — not after.
- **CSF-5**: Avoid displacing existing MCA stacks (Dynamics 365, Salesforce, etc.) — federate, do not centralise [DFSN-C5].

### Stakeholder Alignment Score

**Overall Alignment**: **MEDIUM**

DfT, HMT, NISTA and MHCLG Digital are directionally aligned on "reuse-first, outcomes-led, federated". Alignment weakens at the MCA tier, where past experience of DfT-imposed assurance (CRSTS1 DP1–DP7 gates) has been contentious and Mayors are publicly campaigning for fewer strings. ICO / DPO alignment is contingent on a robust DPIA — currently absent. NAO posture will become clearer post-SR25 bus-funding PAC evidence (NAO already flagged fragmentation). The alignment can be raised to HIGH with explicit Integrated Settlement data-model commitments and a real technical partnership with MHCLG.

---

## Stakeholder Identification

### Internal Stakeholders (DfT)

| Stakeholder | Role/Department | Influence | Interest | Engagement Strategy |
|-------------|-----------------|-----------|----------|---------------------|
| Permanent Secretary (DfT) | Accounting Officer; accountable to PAC | HIGH | LOW | Keep Satisfied — Accounting Officer letter at FBC; quarterly risk escalation |
| DG Rail, Places & Local Transport | Programme sponsor, likely SRO home | HIGH | HIGH | Manage Closely — monthly steering; decision authority |
| SRO (to be appointed, Director-level) | Delivery accountability, spend controls | HIGH | HIGH | Manage Closely — weekly steering; primary governance owner |
| DfT CDIO | Technology assurance, Digital spend controls | HIGH | MEDIUM | Keep Satisfied — spend-control gates; TCoP sign-off |
| DfT Chief Analyst / TAG owner | Owns TAG Data Book; custodian of Green Book appraisal guidance | HIGH | HIGH | Manage Closely — differentiator microservice (Bet 4) cannot ship without them [DFSN-C6] |
| DfT Assurance Hub | Current operators of CRSTS1 DP1–DP7 gates | MEDIUM | HIGH | Keep Informed — requirements co-design; early users |
| DfT Finance / Clear Line of Sight team | OSCAR submissions, drawdown scheduling | MEDIUM | MEDIUM | Keep Informed — integration stakeholder |
| DfT Commercial Directorate | Procurement route (G-Cloud 14 → 15, DOS6) | MEDIUM | LOW | Keep Satisfied — procurement gate; Procurement Act 2023 compliance |
| DfT DDaT Profession Lead | Digital capability, recruitment | LOW | MEDIUM | Monitor — skills pipeline |

### External Stakeholders (Central Government)

| Stakeholder | Organisation | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| HMT Treasury Officers (Transport spending team) | HMT | Spend control, business-case approval above delegation | HIGH | HIGH |
| NISTA (National Infrastructure & Service Transformation Authority) | Cabinet Office / HMT | Assurance authority (IPA+NIC merger, live 01-Apr-2025); holds 780-project pipeline [DFSN-C3] | HIGH | HIGH |
| Cabinet Office Grants Function | Cabinet Office | Minimum Requirements for Grants; Spotlight due-diligence tool; GGIS register | HIGH | MEDIUM |
| MHCLG Digital — Funding Service team | MHCLG | **Strategic reuse partner** (not vendor) [DFSN-C4] | HIGH | HIGH |
| CDDO (Central Digital & Data Office) | Cabinet Office | Digital spend controls, Service Standard, TCoP, Service Manual | HIGH | MEDIUM |
| Government Digital Service (GDS) | Cabinet Office | GOV.UK platforms (One Login, Notify, Pay, Design System); Service Assessments | MEDIUM | MEDIUM |
| NAO (National Audit Office) | Independent of HMG | Ex-post VfM audit; has already flagged city-region funding fragmentation | HIGH | MEDIUM |
| PAC (Public Accounts Committee) | Parliament | Ex-post scrutiny of Accounting Officer | HIGH | LOW |
| ICO | Independent regulator | Data protection oversight; multi-controller complexity here | HIGH | LOW |
| ONS / DfT Statistics | ONS / DfT | Official-statistics obligations on CRSTS performance | MEDIUM | MEDIUM |

### Mayoral Combined Authorities (9 + GLA)

The nine CRSTS2 / TCR-eligible MCAs are **near-peer stakeholders** to DfT, not beneficiaries. Engagement strategy varies by Integrated Settlement tier.

| Authority | Integrated Settlement tier | Funding (indicative) | Current stack signals | Engagement strategy |
|-----------|----------------------------|----------------------|------------------------|---------------------|
| Greater Manchester CA (GMCA / TfGM) | **Tier 1** — live since April 2025 | £2.5bn [DFSN-C2] | Microsoft Dynamics 365 CE + Power Platform (TfGM) [DFSN-C5] | Manage Closely — Integrated Settlement co-design; federation reference |
| West Midlands CA (WMCA / TfWM) | **Tier 1** — live since April 2025 | £2.4bn [DFSN-C2] | GOV.UK-aligned design system; Power BI [DFSN-C5] | Manage Closely — Integrated Settlement co-design |
| West Yorkshire CA (WYCA) | **Tier 2** — joins April 2026 | TBC | DP1–DP7 assurance framework [DFSN-C5] | Manage Closely — early adopter; assurance-framework alignment |
| Liverpool City Region CA (LCRCA) | **Tier 2** — joins April 2026 | £1.6bn [DFSN-C2] | Not public | Manage Closely |
| South Yorkshire Mayoral CA (SYMCA) | **Tier 2** — joins April 2026 | TBC | Not public | Manage Closely |
| North East CA (NECA) | **Tier 2** — joins April 2026 | TBC | Not public | Manage Closely |
| Tees Valley CA (TVCA) | **Tier 3** — retains scheme-level oversight for now | £978m [DFSN-C2] | Not public | Keep Informed — scheme-level workflow remains relevant |
| West of England CA (WECA) | **Tier 3** — retains scheme-level oversight | TBC | Not public | Keep Informed |
| East Midlands CCA (EMCCA) | **Tier 3** — newest member, CCA not CA | £2bn (2026–2032) [DFSN-C2] | Not public — newest authority | Keep Informed — capacity-building needs |
| Greater London Authority (GLA / TfL) | **Tier 2** — joins April 2026 | TBC | Extensive in-house tooling; TfL SPS | Keep Informed — observer; TfL unlikely to adopt but may integrate |

### External Stakeholders (Beneficiaries, Suppliers, Public)

| Stakeholder | Organisation | Relationship | Influence | Interest |
|-------------|--------------|--------------|-----------|----------|
| Local Transport Authorities (inside MCAs) | Local Authorities | Scheme sponsors / delivery bodies | LOW | HIGH |
| Sub-regional transport bodies (e.g. Transport for the North, Midlands Connect) | Pan-regional | Evidence base, scheme prioritisation | LOW | MEDIUM |
| Delivery contractors / Tier 1 civil engineering | Private sector | Ultimate claim payees | LOW | MEDIUM |
| Transport users / citizens | Public | Outcome beneficiaries | LOW | LOW (platform); HIGH (services delivered) |
| Transport campaigning groups (Campaign for Better Transport, Transport for New Homes, Sustrans) | Third sector | Public-interest scrutiny | LOW | MEDIUM |
| Commercial grant-platform vendors (Flexi-Grant, SmartSimple, Blackbaud, GovGrants, Civica, HSO, ANS) | Private sector | Prospective suppliers (fallback route) [DFSN-C7] | LOW | HIGH |

### UK Government Digital Roles (GovS 005)

> The [Government Functional Standard for Digital (GovS 005)](https://www.gov.uk/government/publications/government-functional-standard-govs-005-digital) defines mandatory digital governance roles.

| Role | Responsibility | Power/Interest | Engagement Strategy |
|------|----------------|----------------|---------------------|
| Senior Responsible Owner (SRO) | Accountable for digital outcomes and spend controls | HIGH / HIGH | Manage Closely — steering chair |
| Service Owner | End-to-end service & user outcomes across DfT + MCAs | HIGH / HIGH | Manage Closely — federated service design |
| Product Manager | Feature prioritisation against policy (DfT) and MCA needs | MEDIUM / HIGH | Keep Informed — sprint reviews, MCA advisory group |
| Delivery Manager | Delivery cadence, risk, MHCLG integration | MEDIUM / HIGH | Keep Informed — stand-ups |
| CDDO spend-controls assessor | Digital spend control; cross-gov standards assurance | HIGH / MEDIUM | Keep Satisfied — mandatory gate at SOC/OBC/FBC |
| DfT CDIO | Departmental digital strategy | HIGH / MEDIUM | Keep Satisfied — quarterly strategy alignment |
| DDaT Profession Lead (DfT) | DDaT capability & recruitment | LOW / MEDIUM | Monitor — capability plan |

### UK Government Security Roles (GovS 007)

| Role | Responsibility | Power/Interest | Engagement Strategy |
|------|----------------|----------------|---------------------|
| Senior Security Risk Owner (SSRO, DfT) | Owns protective security risk at Board level | HIGH / MEDIUM | Keep Satisfied — security risk escalation |
| Departmental Security Officer (DSO, DfT) | Day-to-day security coordination | HIGH / MEDIUM | Keep Satisfied — compliance gates |
| Senior Information Risk Owner (SIRO, DfT) | Owns information & cyber risk; signs off DPIA | HIGH / MEDIUM | Keep Satisfied — DPIA approval |
| Cyber Security Lead (DfT) | CAF / GovAssure operational assurance | MEDIUM / HIGH | Keep Informed — GovAssure cycle, pen test scheduling |

### Stakeholder Power-Interest Grid

```text
                                 INTEREST
                  Low                                 High
          ┌─────────────────────────────┬─────────────────────────────┐
          │                             │                             │
          │       KEEP SATISFIED        │       MANAGE CLOSELY        │
    High  │                             │                             │
          │ • Perm Sec (DfT)            │ • DG Rail, Places & Local   │
          │ • HMT (if lower interest)   │ • SRO (DfT)                 │
          │ • DfT CDIO                  │ • HMT Transport team        │
          │ • Cabinet Office Grants Fn  │ • NISTA                     │
          │ • CDDO spend controls       │ • MHCLG Digital (FS team)   │
          │ • SSRO / DSO / SIRO (DfT)   │ • DfT Chief Analyst / TAG   │
  P       │ • NAO                       │ • GMCA, WMCA (Tier-1 IS)    │
  O       │ • PAC                       │ • WYCA, LCRCA, SYMCA, NECA  │
  W       │ • ICO                       │   (Tier-2 IS, joining '26)  │
  E       │                             │                             │
  R       ├─────────────────────────────┼─────────────────────────────┤
          │                             │                             │
          │           MONITOR           │        KEEP INFORMED        │
          │                             │                             │
    Low   │ • Campaign groups           │ • DfT Assurance Hub         │
          │ • Transport users / citizens│ • TVCA, WECA, EMCCA (Tier-3)│
          │ • DDaT Profession Lead      │ • GLA / TfL (observer)      │
          │ • GDS (non-blocking)        │ • LTAs (scheme sponsors)    │
          │ • Commercial vendors        │ • Cyber Security Lead (DfT) │
          │                             │ • Product / Delivery mgrs   │
          │                             │                             │
          └─────────────────────────────┴─────────────────────────────┘
```

**Quadrant Interpretation:**

- **Manage Closely** (High Power, High Interest): Key decision-makers requiring active engagement
- **Keep Satisfied** (High Power, Low Interest): Influential stakeholders needing periodic updates
- **Keep Informed** (Low Power, High Interest): Engaged stakeholders needing regular communication
- **Monitor** (Low Power, Low Interest): Minimal engagement required

---

## Stakeholder Drivers Analysis

### SD-1: DfT SRO — Deliver CRSTS2/TCR administration without NAO or PAC criticism

**Stakeholder**: SRO (Director-level, DfT Rail, Places & Local Transport DG)

**Driver Category**: RISK / PERSONAL / OPERATIONAL

**Driver Statement**: Establish a defensible administrative platform for £15.6bn CRSTS2/TCR funding [DFSN-C8] that survives NAO VfM audit, withstands PAC scrutiny, avoids the "fragmentation" critique NAO applied to BSIP funding, and meets Integrated Settlement commitments without becoming a cautionary tale.

**Context & Background**: The SRO inherits a live critique. NAO flagged 19% BSIP capital delivery by December 2024 and cited "capacity to manage" [DFSN-C9]. SR25 baked CRSTS2 into the fiscal path at £15.6bn over 5 years — political exposure is higher than under CRSTS1. NISTA now assures the pipeline; getting this wrong reaches Cabinet-level visibility.

**Driver Intensity**: **CRITICAL**

**Enablers**:

- Reuse MHCLG Funding Service (reduces build risk, aligns to TCoP Point 8)
- Early NISTA engagement (makes this an "inside-the-tent" assurance relationship)
- Publishing TAG/BCR microservice under OGL v3 (defensive narrative: "DfT is a reuse producer")

**Blockers**:

- MCA non-cooperation or public Mayoral criticism
- MHCLG Funding Service instability (2 grants onboarded at launch)
- NISTA assurance asks that force re-architecting mid-build

**Related Stakeholders**: DG Rail/Places/Local Transport, HMT, NISTA, NAO

---

### SD-2: HMT Treasury Officers — Demonstrable value-for-money & drawdown control

**Stakeholder**: HMT Treasury Officers (Transport spending team)

**Driver Category**: FINANCIAL / COMPLIANCE

**Driver Statement**: Secure timely, accurate, auditable drawdown of £15.6bn against the SR25 profile; obtain machine-readable BCR/VfM evidence to defend future settlements; maintain Clear Line of Sight and OSCAR alignment.

**Context & Background**: Post-SR25 the Chief Secretary is under pressure to demonstrate fiscal discipline at a time of very tight headroom. Transport capital is one of the larger discretionary envelopes. HMT wants to see that its money is converting to outcomes, not just commitments. [DFSN-C10]

**Driver Intensity**: **HIGH**

**Enablers**: Integrated Settlement outcomes framework made machine-readable; TAG-compliant BCR data; OSCAR/CLoS integration.

**Blockers**: MCA reluctance to expose scheme-level data; outcomes framework still being negotiated (governance risk).

**Related Stakeholders**: SRO, NISTA, MCAs, NAO.

---

### SD-3: NISTA — Credible pipeline assurance for infrastructure programmes

**Stakeholder**: NISTA (post-merger IPA + NIC, live 01-Apr-2025)

**Driver Category**: STRATEGIC / COMPLIANCE

**Driver Statement**: Establish NISTA as the credible single assurance authority across the £530bn / 780-project infrastructure pipeline [DFSN-C3]; receive structured, timely data feeds from all major capital programmes — CRSTS2/TCR is one of the most visible.

**Context & Background**: NISTA is new, still defining its operating model, and its first year will be judged by whether it imposes control or reproduces the old IPA workload. Being a late interlocutor on a £15.6bn programme would be a reputational problem.

**Driver Intensity**: **HIGH**

**Enablers**: Pipeline-update API from day 1; alignment to NISTA's evolving data schema; DfT SRO positioning NISTA as partner not gate.

**Blockers**: NISTA data schema still emerging (moving target); competing IPA legacy formats.

**Related Stakeholders**: SRO, HMT, NAO.

---

### SD-4: MHCLG Funding Service team — Cross-government reuse validation

**Stakeholder**: MHCLG Digital — Funding Service team

**Driver Category**: STRATEGIC / PERSONAL

**Driver Statement**: Prove that the MHCLG Funding Service (OGL v3, live December 2025) is a genuine cross-government platform — not "just for MHCLG schemes" [DFSN-C4]. DfT adoption or credible fork would be the single largest validation moment in the team's first 18 months.

**Context & Background**: The Funding Service launched December 2025 with 2 grants onboarded; its strategic case depends on cross-departmental traction. Early partners de-risk the platform's funding case internally to MHCLG.

**Driver Intensity**: **HIGH** (for them; indirect driver for DfT — mutual benefit)

**Enablers**: Early joint-engineering governance board; shared roadmap; credited upstream contributions.

**Blockers**: DfT picking a commercial SaaS fallback instead.

**Related Stakeholders**: CDDO (likely a champion), DfT SRO, DfT CDIO.

---

### SD-5: GMCA & WMCA (Tier-1 Integrated Settlement) — Preserve autonomy won in 2025

**Stakeholder**: GMCA (TfGM), WMCA (TfWM) — the two MCAs already on Integrated Settlement since April 2025

**Driver Category**: STRATEGIC / PERSONAL (Mayoral)

**Driver Statement**: Protect the newly-won Integrated Settlement autonomy — resist any DfT platform that reintroduces scheme-level approval where outcomes-level accountability was agreed [DFSN-C2]; avoid forced replacement of existing Dynamics 365 / Power Platform stacks already paid for and working [DFSN-C5].

**Context & Background**: Mayors of Greater Manchester and the West Midlands fought for years for single-pot devolution. Any centrally-mandated system feels like regression. Both authorities also have sunk IT investment in Microsoft stacks.

**Driver Intensity**: **HIGH**

**Enablers**: Federated design (clean APIs, no forced UI); explicit commitment that DfT platform does not duplicate MCA tooling; Mayoral political cover from central-government endorsement of Integrated Settlement.

**Blockers**: Any DfT language suggesting "single system for all CRSTS", perceived scheme-level approval re-entering through the back door.

**Related Stakeholders**: Other MCAs (who watch GMCA/WMCA as canary), SRO, HMT.

---

### SD-6: Tier-2 & Tier-3 MCAs (WYCA, LCRCA, SYMCA, NECA, TVCA, WECA, EMCCA) — Onboarding capacity

**Stakeholder**: Seven MCAs outside the Tier-1 Integrated Settlement, with varying sizes, capacity and capability — notably EMCCA as the newest (CCA, not CA) authority.

**Driver Category**: OPERATIONAL / PERSONAL

**Driver Statement**: Gain an administrative platform that reduces local compliance overhead (each MCA today runs a bespoke DP1–DP7-equivalent assurance framework) [DFSN-C5] without adding cost or forcing procurement of a new case-management substrate. EMCCA in particular needs capability uplift.

**Driver Intensity**: **HIGH** (for EMCCA, WYCA, LCRCA, SYMCA); **MEDIUM** (for TVCA, WECA); **MEDIUM** (for NECA).

**Enablers**: Hosted recipient view (Access Grant Funding component of MHCLG Funding Service) available out-of-box; documented MCA onboarding playbook; shared MCA architect community.

**Blockers**: MCA finance ledger heterogeneity (Unit4/SAP/Oracle) making drawdown integration fragmented.

**Related Stakeholders**: GMCA/WMCA (as reference), SRO, MHCLG Digital.

---

### SD-7: DfT Chief Analyst / TAG owner — Protect the integrity of Green Book/TAG appraisal

**Stakeholder**: DfT Chief Analyst's office; TAG Unit (custodians of the Transport Analysis Guidance)

**Driver Category**: COMPLIANCE / PROFESSIONAL

**Driver Statement**: Ensure any automated BCR / VfM calculations strictly track the TAG Data Book (updated every November and May) and do not compromise HMT Green Book methodology. If a microservice is going to output BCRs, the TAG team must own the logic [DFSN-C6].

**Driver Intensity**: **HIGH**

**Enablers**: Microservice source code owned by TAG team; data-book versioning explicitly surfaced in API; TAG team embedded in sprint cadence.

**Blockers**: A vendor SaaS that does BCR opaquely; any move to "simplify" TAG calculations for UX reasons.

**Related Stakeholders**: SRO, HMT, NISTA, NAO.

---

### SD-8: ICO / DfT SIRO / DPOs across authorities — Lawful multi-controller data handling

**Stakeholder**: ICO (external); DfT SIRO; nine MCA DPOs

**Driver Category**: COMPLIANCE / RISK

**Driver Statement**: Ensure that a federated multi-authority platform processing personal data (scheme sponsors, individual beneficiaries where applicable, authority staff accounts) has clear controller/processor roles, a defensible DPIA, Article 28 DPAs across the federation, and UK GDPR transfer mechanisms if any SaaS component is non-UK-hosted.

**Driver Intensity**: **HIGH**

**Enablers**: Early DPIA (before alpha); Cabinet Office data-sharing agreements template; UK sovereignty of hosting.

**Blockers**: Informal data-sharing; unclear joint-controller boundaries; US-hosted SaaS components.

**Related Stakeholders**: SRO, CDIO, SIRO, MCA DPOs.

---

### SD-9: NAO / PAC — Audit defensibility and fragmentation avoidance

**Stakeholder**: National Audit Office (current and successor PAC sessions)

**Driver Category**: COMPLIANCE / RISK

**Driver Statement**: Produce a CRSTS2/TCR administrative regime that NAO can audit ex-post without concluding "fragmentation" [DFSN-C9] — i.e. proportionate, consolidated, evidence-based, with clear Accounting Officer sign-off trail.

**Driver Intensity**: **HIGH** (for NAO); **CRITICAL** if NAO has recently flagged DfT elsewhere.

**Enablers**: Single authoritative pipeline view; consolidated MRM reporting; clear audit trail with versioned decisions.

**Blockers**: Multiple parallel systems; inaccessible MCA-side data; decisions not captured as artifacts.

**Related Stakeholders**: Perm Sec (Accounting Officer), SRO, HMT.

---

### SD-10: Transport-user / citizen interest groups (Campaign for Better Transport, Transport for New Homes, Sustrans)

**Stakeholder**: Third-sector scrutineers of transport investment

**Driver Category**: STRATEGIC (external, public-interest)

**Driver Statement**: Obtain transparent evidence that CRSTS2/TCR funding is being allocated to modal shift, active travel, and sustainable outcomes rather than road expansion — and that evidence is public, machine-readable, and updated at a meaningful cadence.

**Driver Intensity**: **MEDIUM** (they have no formal veto, but they shape public narrative)

**Enablers**: Open-data publication of outcomes indicators; `data.gov.uk` feeds; algorithmic transparency for TAG automation if AI-assisted.

**Blockers**: Outcomes data published only in redacted PDFs; inconsistent reporting across MCAs.

**Related Stakeholders**: ONS, DfT statistics, Ministers.

---

### SD-11: CDDO & GDS — Cross-government platform reuse & TCoP compliance

**Stakeholder**: CDDO (spend control), GDS (Service Assessments, GOV.UK platform team)

**Driver Category**: STRATEGIC / COMPLIANCE

**Driver Statement**: Ensure DfT adoption of GOV.UK One Login (mandatory by end of 2027), Notify, Pay, Forms, Design System and the Funding Service becomes an exemplar of Technology Code of Practice compliance.

**Driver Intensity**: **MEDIUM** (blocks progression at spend-control gate if off-track)

**Enablers**: Early Service Assessment booking; TCoP self-assessment evidence pack; DWP/MoJ case studies.

**Blockers**: Vendor SaaS that duplicates GOV.UK platforms.

**Related Stakeholders**: DfT CDIO, SRO.

---

## Driver-to-Goal Mapping

### Goal G-1: Deliver a shared DfT platform that is operational for at least 5 of 9 MCAs by Integrated Settlement Tier-2 start (April 2027)

**Derived From Drivers**: SD-1, SD-2, SD-3, SD-5, SD-6, SD-11

**Goal Owner**: SRO

**Goal Statement**: By April 2027, the platform is in public beta supporting **at least 5 of the 9 MCAs** — specifically GMCA, WMCA (Tier-1 reference) and three of the five Tier-2 authorities (WYCA/LCRCA/SYMCA/NECA/GLA) — with end-to-end scheme → outcome → claim workflow, reuse of MHCLG Funding Service as case-management substrate, and TAG-BCR microservice published under OGL v3.

**Why This Matters**: Anchors delivery to the Integrated Settlement trajectory [DFSN-C2], which is a fixed HMG policy commitment; gives NISTA structured pipeline data ahead of its own maturity curve; proves DfT isn't a straggler on the MHCLG Funding Service adoption narrative.

**Success Metrics**:

- **Primary**: Number of MCAs live on the platform (target ≥ 5 by Apr 2027)
- **Secondary**: % of CRSTS2 scheme intake going through the platform vs bespoke email/SharePoint fallback; median time-to-first-drawdown post-FBC

**Baseline**: 0 of 9 MCAs; current intake via heterogeneous email + portal + Sharepoint; time-to-first-drawdown currently > 6 months post-FBC (CRSTS1 evidence).

**Target**: ≥ 5 MCAs; > 80% of new CRSTS2 schemes on platform; time-to-first-drawdown < 3 months.

**Measurement Method**: Platform onboarding register; DfT/MCA quarterly MRM; drawdown ledger from OSCAR integration.

**Dependencies**: MHCLG Funding Service reuse decision (G-5); SRO appointment; MCA engagement (G-4); procurement route locked in G-Cloud 14 window or committed G-Cloud 15.

**Risks to Achievement**: MHCLG Funding Service instability; any one MCA publicly withdraws; NISTA data schema churn; Procurement Act 2023 transition friction.

---

### Goal G-2: Deliver a TAG-compliant BCR/VfM microservice with TAG team ownership, published under OGL v3, by FBC

**Derived From Drivers**: SD-2, SD-3, SD-7, SD-11

**Goal Owner**: DfT Chief Analyst (delivery); SRO (accountability)

**Goal Statement**: A stateless microservice, consuming the published TAG Data Book (May and November refreshes), exposing BCR and VfM category outputs via OpenAPI, owned by the DfT TAG Unit, published under OGL v3, in production by FBC submission (target Q4 2026).

**Why This Matters**: Protects Green Book/TAG integrity [DFSN-C6] against vendor-opaque calculations, gives DfT a **publishable cross-government asset**, and becomes the "differentiator" Bet 4 in the strategy notes.

**Success Metrics**: Number of schemes scored through microservice; HMT/TAG team sign-off; external adopters (DLUHC/MHCLG/DESNZ).

**Baseline**: TAG calculations currently done in spreadsheets, inconsistent tooling across MCAs.

**Target**: 100% of CRSTS2 schemes assessed via microservice by April 2027; at least 1 non-DfT department evaluating adoption by March 2027.

**Measurement Method**: Microservice usage metrics; OGL v3 repo traffic; cross-department technical-partnership log.

**Dependencies**: TAG Unit staffing; OGL v3 publication process; API versioning governance.

**Risks**: TAG Data Book change cadence outpacing service; TAG team opposes externalising the logic.

---

### Goal G-3: Achieve NISTA pipeline-update integration and HMT OSCAR integration before OBC

**Derived From Drivers**: SD-2, SD-3, SD-1

**Goal Owner**: SRO; DfT Finance / Clear Line of Sight team

**Goal Statement**: By Outline Business Case (OBC) submission (target Q3 2026), the platform has live integration contracts with NISTA's pipeline-update endpoint and HMT's OSCAR/Clear Line of Sight interface, tested end-to-end with at least one MCA.

**Why This Matters**: NISTA is new and its schema is emergent — the later we integrate, the more rework. HMT drawdown integration is non-negotiable for any grant platform.

**Success Metrics**: Signed-off integration contracts; successful test runs; NISTA analyst sign-off.

**Baseline**: No integration with NISTA (NISTA is new); limited OSCAR integration across MCAs.

**Target**: Both integrations tested by OBC; productionised by Public Beta.

**Measurement Method**: Integration test evidence; NISTA and HMT analyst sign-off.

**Dependencies**: NISTA schema availability; DfT Finance commitment.

**Risks**: NISTA schema still under design; OSCAR access approvals.

---

### Goal G-4: Secure signed MCA engagement commitments from ≥ 5 authorities before Requirements Freeze

**Derived From Drivers**: SD-1, SD-5, SD-6

**Goal Owner**: SRO; DG Rail/Places/Local Transport

**Goal Statement**: By Requirements Freeze (target Q2 2026), signed Memoranda of Collaboration with at least 5 of the 9 CRSTS2/TCR-eligible MCAs agreeing to co-design and pilot the platform.

**Why This Matters**: Without early MCA signal, the platform risks being built in a vacuum and rejected on delivery (a replay of central-digital tensions seen in other departments).

**Success Metrics**: MoC count and signatory seniority (Mayor / CE / CFO / Digital Director).

**Baseline**: 0 MoCs.

**Target**: ≥ 5 by Requirements Freeze; ≥ 7 by OBC.

**Measurement Method**: MoC register; MCA steering group attendance log.

**Dependencies**: Proposition clarity; federated (not centralised) design commitment.

**Risks**: Tier-1 MCAs (GMCA, WMCA) perceive loss of autonomy and decline; political change at Mayoral level mid-engagement.

---

### Goal G-5: Close the reuse-or-fork decision with MHCLG Funding Service before SOC submission

**Derived From Drivers**: SD-1, SD-4, SD-11

**Goal Owner**: SRO; DfT CDIO

**Goal Statement**: By Strategic Outline Case (SOC) submission (target Q2 2026), a joint governance agreement with MHCLG Digital is signed, documenting one of: (a) straight reuse of Funding Service hosted instance, (b) fork + contribute upstream, or (c) justification for alternative route.

**Why This Matters**: MHCLG reuse is the most defensible TCoP answer [DFSN-C4]; unresolved, it becomes a late-stage bottleneck.

**Success Metrics**: Signed Joint Engineering Governance terms; documented decision with reasoning.

**Baseline**: No agreement.

**Target**: Signed by SOC.

**Measurement Method**: Governance document; ADR `ARC-001-ADR-001`.

**Dependencies**: MHCLG Digital capacity; CDDO facilitation.

**Risks**: MHCLG platform immaturity causes hesitation; political pressure for a commercial-off-the-shelf answer.

---

### Goal G-6: DPIA approved and lawful basis documented across all authorities before Private Beta

**Derived From Drivers**: SD-8, SD-1

**Goal Owner**: DfT SIRO

**Goal Statement**: Before Private Beta (target Q1 2027), DPIA signed off by DfT SIRO, shared with all 9 MCA DPOs, reviewed (not veto) by ICO if processing is novel, with controller/processor/joint-controller roles explicitly documented and Article 28 DPAs in place.

**Why This Matters**: Multi-authority data processing without clear lawful basis is the single highest-impact compliance risk.

**Success Metrics**: DPIA sign-off; DPA register.

**Baseline**: No DPIA.

**Target**: Approved before Private Beta.

**Measurement Method**: DPIA artifact `ARC-001-DPIA-v1.0`; DPA register.

**Dependencies**: Data model finalised; hosting decision finalised.

**Risks**: Unresolved joint-controller boundaries with MCAs; ICO consultation if processing is novel.

---

### Goal G-7: Pass GDS Service Assessment at Alpha and Beta; TCoP self-assessment Green before each spend-control gate

**Derived From Drivers**: SD-11, SD-1

**Goal Owner**: Service Owner; SRO

**Goal Statement**: Pass Service Assessments at Alpha and Beta; TCoP self-assessment returns Green across all 12 points at each CDDO spend-control submission.

**Why This Matters**: Required for spend-control progression and establishes an exemplar narrative for NAO/PAC.

**Success Metrics**: Service Assessment pass; TCoP Green.

**Baseline**: N/A (pre-Alpha).

**Target**: Pass at Alpha (target Q3 2026) and Beta (target Q1 2027).

**Measurement Method**: GDS assessment report; TCoP artifact `ARC-001-TCOP-v1.0`.

**Dependencies**: Federated identity design; accessible front-ends; publishing outcomes data.

**Risks**: Multi-authority UX divergence; accessibility gaps in MCA-hosted views.

---

## Goal-to-Outcome Mapping

### Outcome O-1: Consolidated, auditable view of all CRSTS2/TCR schemes across 9 MCAs

**Supported Goals**: G-1, G-3, G-4

**Outcome Statement**: A single pipeline ledger — covering scheme, outcome, indicator, milestone, claim, drawdown, and evaluation data — is queryable by DfT, HMT, NISTA and NAO for every CRSTS2/TCR scheme across all 9 MCAs by end of Year 2 post-Public-Beta.

**Measurement**:

- **KPI**: % of CRSTS2/TCR scheme throughput visible in single pipeline view
- **Current Value**: ~0% (fragmented across MCA systems)
- **Target Value**: ≥ 90% by end of Year 2 post-Public Beta
- **Frequency**: Quarterly DfT board; monthly operational
- **Data Source**: Platform database + MCA federation APIs
- **Report Owner**: SRO via PMO

**Business Value**:

- **Financial**: Faster drawdown; fewer delayed claims; reduced MRM overhead (est. saving £1.5–3m/yr across federation vs status quo per strategy-notes TCO Δ [DFSN-C11])
- **Strategic**: NAO defensibility against fragmentation critique; NISTA credibility
- **Operational**: Consolidated MRM; single source of truth for parliamentary questions
- **Customer**: MCAs get pre-populated assurance templates, lower admin burden

**Timeline**:

- **Phase 1 (Apr 2026 – Apr 2027)**: 2 Tier-1 MCAs fully on platform (GMCA, WMCA)
- **Phase 2 (Apr 2027 – Apr 2028)**: + 3 Tier-2 MCAs
- **Phase 3 (Apr 2028 – Apr 2029)**: All 9 authorities + GLA observer
- **Sustainment (Year 2+)**: Continuous improvement; open-data publication

**Stakeholder Benefits**:

- **SRO**: Defensible NAO/PAC position
- **HMT**: Real-time drawdown visibility
- **NISTA**: Pipeline feed
- **MCAs**: Less duplicate reporting

**Leading**: MoC count; MCAs with API integration complete; platform uptime

**Lagging**: % of schemes on platform; drawdown lag; audit findings count

---

### Outcome O-2: Green Book / TAG BCR microservice adopted by DfT and ≥ 1 other department

**Supported Goals**: G-2

**Outcome Statement**: A TAG-compliant BCR microservice, published under OGL v3, is used to appraise 100% of CRSTS2/TCR schemes and has at least one other department (DLUHC, DESNZ, or NHS England) in active evaluation by March 2028.

**Measurement**:

- **KPI**: Schemes scored via microservice; external-department engagement
- **Current Value**: 0 schemes; 0 external departments
- **Target Value**: 100% CRSTS2; ≥ 1 department
- **Frequency**: Monthly
- **Data Source**: Microservice telemetry; cross-dept technical partnership log
- **Report Owner**: DfT Chief Analyst

**Business Value**:

- **Financial**: Reduces bespoke BCR tooling cost across government (est. £0.5m/yr)
- **Strategic**: Establishes DfT as a cross-gov reuse producer (Strategy Bet 6 [DFSN-C12])
- **Operational**: Consistent BCR methodology across schemes
- **Customer**: TAG analysts relieved of spreadsheet toil

**Timeline**: alpha by Q4 2026; beta by Q2 2027; production by Q4 2027.

**Stakeholder Benefits**: Analyst, HMT, NISTA, external departments, transparency groups.

**Leading**: TAG team headcount on microservice; repo stars/forks; external-dept enquiries.

**Lagging**: Schemes scored; external adopters; cited in NAO report as exemplar.

---

### Outcome O-3: Integrated Settlement outcomes data made machine-readable and open

**Supported Goals**: G-1, G-3

**Outcome Statement**: By end of Year 1 post-Public Beta, the Integrated Settlement outcomes framework is represented in machine-readable form (open schema, open data) and published to `data.gov.uk`, with quarterly refresh and stable URIs per indicator.

**Measurement**:

- **KPI**: Outcomes published (count); refresh cadence; URI stability
- **Current Value**: Outcomes currently in PDFs
- **Target Value**: 100% of published outcomes machine-readable; quarterly refresh; 0 broken URIs
- **Frequency**: Quarterly
- **Data Source**: `data.gov.uk` + platform API
- **Report Owner**: Service Owner

**Business Value**:

- **Strategic**: Answers transparency scrutiny before it escalates
- **Operational**: NISTA and HMT ingest automatically
- **Customer**: Third-sector scrutineers get parity access; academic research enabled

**Leading**: Outcomes schema ratified; publishing pipeline live.

**Lagging**: `data.gov.uk` downloads; third-sector citations.

---

### Outcome O-4: Net TCO of < £6m over 3 years for the platform (excluding grant throughput)

**Supported Goals**: G-1, G-5, G-7

**Outcome Statement**: The platform's 3-year TCO (2026/27 to 2028/29) is contained within the hybrid reuse band identified in the discovery research: £3.0m–£5.5m [DFSN-C11], representing < 0.04% of grant throughput.

**Measurement**: Quarterly cost report against budget; third-party cost-review at FBC.

**Baseline**: £0 (pre-investment).

**Target**: ≤ £5.5m 3-year TCO.

**Business Value**:

- **Financial**: < 0.04% of £15.6bn grant throughput (CRSTS2/TCR) — exceptional ratio
- **Strategic**: Defensible VfM narrative under NAO audit

**Leading**: Run-rate against forecast; per-sprint cost.

**Lagging**: Audited 3-year actuals.

---

### Outcome O-5: Zero notifiable data breaches and ICO-positive DPIA outcome

**Supported Goals**: G-6

**Outcome Statement**: Through Public Beta and the first 24 months of Live running, zero notifiable personal-data breaches occur; DPIA reviewed and not challenged by ICO; multi-controller DPAs signed with all onboarded MCAs.

**Measurement**: ICO breach register; internal security incident log; DPA register.

**Target**: 0 notifiable breaches; DPIA not challenged.

**Business Value**: Compliance, reputation, SRO/SIRO personal assurance.

**Leading**: Pen test pass rate; DPO review cadence; DPA execution tracker.

**Lagging**: Breach count; ICO enforcement notices (target: 0).

---

## Complete Traceability Matrix

### Stakeholder → Driver → Goal → Outcome

| Stakeholder | Driver ID | Driver Summary | Goal ID | Goal Summary | Outcome ID | Outcome Summary |
|-------------|-----------|----------------|---------|--------------|------------|-----------------|
| SRO | SD-1 | NAO/PAC-defensible delivery | G-1 | ≥5 MCAs by Apr 2027 | O-1 | Consolidated pipeline view |
| SRO | SD-1 | NAO/PAC-defensible delivery | G-5 | MHCLG reuse decision | O-4 | TCO < £5.5m |
| HMT | SD-2 | VfM & drawdown control | G-3 | OSCAR/NISTA integration | O-1 | Consolidated pipeline view |
| HMT | SD-2 | VfM & drawdown control | G-2 | TAG/BCR microservice | O-2 | Microservice adopted |
| NISTA | SD-3 | Credible pipeline assurance | G-3 | OSCAR/NISTA integration | O-1 | Consolidated pipeline view |
| NISTA | SD-3 | Credible pipeline assurance | G-1 | ≥5 MCAs by Apr 2027 | O-3 | Outcomes open data |
| MHCLG Digital | SD-4 | Cross-gov reuse validation | G-5 | MHCLG reuse decision | O-1 | Consolidated pipeline view |
| GMCA / WMCA | SD-5 | Preserve Integrated Settlement autonomy | G-4 | MoCs signed | O-1 | Consolidated pipeline view |
| Tier-2/3 MCAs | SD-6 | Onboarding capacity | G-4 | MoCs signed | O-1 | Consolidated pipeline view |
| Tier-2/3 MCAs | SD-6 | Onboarding capacity | G-1 | ≥5 MCAs by Apr 2027 | O-4 | TCO < £5.5m |
| DfT TAG Unit | SD-7 | TAG integrity | G-2 | TAG/BCR microservice | O-2 | Microservice adopted |
| ICO / SIRO / MCA DPOs | SD-8 | Lawful multi-controller | G-6 | DPIA + DPAs | O-5 | Zero breaches |
| NAO / PAC | SD-9 | Fragmentation avoidance | G-1 | ≥5 MCAs by Apr 2027 | O-1 | Consolidated pipeline view |
| NAO / PAC | SD-9 | Fragmentation avoidance | G-7 | Service Std + TCoP | O-4 | TCO < £5.5m |
| Campaign groups | SD-10 | Public transparency | G-1 | ≥5 MCAs by Apr 2027 | O-3 | Outcomes open data |
| CDDO / GDS | SD-11 | TCoP / Service Std | G-7 | Service Std + TCoP | O-3 | Outcomes open data |
| CDDO / GDS | SD-11 | TCoP / Service Std | G-5 | MHCLG reuse decision | O-4 | TCO < £5.5m |

### Conflict Analysis

**Competing Drivers**:

- **Conflict 1 — HMT/NISTA visibility vs MCA autonomy (SD-2, SD-3 vs SD-5, SD-6)**: HMT and NISTA want granular, near-real-time, scheme-level data. Tier-1 Mayors fought for outcomes-level accountability precisely to avoid that level of central oversight.
  - **Resolution Strategy**: Design two clearly separated data planes. MCAs publish **outcomes** (mandatory under Integrated Settlement) to DfT; MCAs additionally publish **scheme detail** (Tier-3 MCAs) or **nil** (Tier-1 MCAs). HMT/NISTA must accept that Tier-1 visibility is outcomes-only. Make this a written Principle (ARCH-PRIN-x) before requirements.

- **Conflict 2 — Reuse of MHCLG Funding Service (SD-4, SD-11) vs speed pressure from SRO & HMT (SD-1, SD-2)**: MHCLG Funding Service is immature (2 grants onboarded at launch). SRO under PAC pressure may prefer a commercial SaaS that is "proven".
  - **Resolution Strategy**: Fork + contribute (Bet 2) with explicit commercial-SaaS contingency gate at OBC. Time-box the MHCLG Funding Service engagement decision to SOC+3 months; if technical fit workshop indicates > 6 months to onboard CRSTS, fall back to Flexi-Grant or Salesforce GovGrants as interim while continuing to invest upstream.

- **Conflict 3 — TAG Unit ownership (SD-7) vs vendor offering "BCR-as-a-service" (SD-11 operational realism)**: A commercial vendor offering push-button BCR would simplify UX but opaque TAG logic is unacceptable.
  - **Resolution Strategy**: TAG Unit owns microservice source code; vendor (if any) integrates via API, not the reverse.

- **Conflict 4 — Transparency/open-data (SD-10) vs commercial confidentiality of sponsor bids (SD-6)**: Some scheme data is commercially sensitive (e.g. tender-stage rates) and MCAs may resist publication.
  - **Resolution Strategy**: Two-tier publication — outcomes/indicators open; scheme-level financial detail restricted with explicit publish-at-FBC trigger.

- **Conflict 5 — Procurement Act 2023 transition (SD-1 SRO pressure) vs MCA procurement autonomy**: DfT procures centrally; MCAs often procure their own tooling separately.
  - **Resolution Strategy**: DfT procures the central platform; MCAs are beneficiaries via MoC, not procurement parties. Avoids fragmented contracting.

**Synergies**:

- **Synergy 1 (SD-1 SRO + SD-4 MHCLG + SD-11 CDDO)**: All three drivers align on MHCLG Funding Service reuse. This is the strongest axis of alignment and should anchor the narrative.
- **Synergy 2 (SD-2 HMT + SD-3 NISTA + SD-9 NAO)**: All three central-oversight stakeholders want consolidated pipeline data. A single pipeline ledger satisfies all three with one investment.
- **Synergy 3 (SD-7 TAG + SD-11 CDDO)**: TAG microservice + OGL v3 publication gives both a professional-integrity win (TAG) and a TCoP reuse win (CDDO).
- **Synergy 4 (SD-5 GMCA/WMCA + SD-10 campaigners)**: Both want outcomes-level transparency; Mayors will champion open data if it legitimises devolution.

---

## Communication & Engagement Plan

### SRO & DG Rail/Places/Local Transport

**Primary Message**: "This platform is how DfT survives the NAO scrutiny that BSIP attracted. It is defensible, reuse-first, and gives HMT/NISTA clean data without re-centralising the Integrated Settlement."

**Key Talking Points**:

- £3–5.5m 3-yr TCO for < 0.04% of grant throughput
- MHCLG reuse is the TCoP-compliant default
- Federated design protects Mayoral relationships

**Frequency**: Weekly (SRO); monthly (DG)
**Channel**: SRO steering; DG board submission

### HMT Treasury & NISTA

**Primary Message**: "You get scheme-, outcome- and drawdown-level data on a cadence you have never had before. OSCAR integrates natively. NISTA pipeline updates are automated from day 1."

**Frequency**: Monthly steering; quarterly deep-dive
**Channel**: Joint DfT-HMT-NISTA governance board

### MHCLG Digital — Funding Service team

**Primary Message**: "You are the single largest cross-government validation of the Funding Service so far. Let's establish a joint engineering governance board in the first 90 days."

**Frequency**: Fortnightly technical; monthly governance
**Channel**: Joint Engineering Governance Board; shared backlog

### Tier-1 Mayoral CAs (GMCA, WMCA)

**Primary Message**: "Your Integrated Settlement autonomy is not at risk. DfT federates with your Dynamics/Power Platform stack. You publish outcomes; we consume them. No forced UI."

**Frequency**: Monthly CE-level; quarterly Mayoral
**Channel**: Steering group; direct Mayoral correspondence on red-flag items

### Tier-2 & Tier-3 MCAs (especially EMCCA)

**Primary Message**: "You get a hosted recipient view and pre-built claim workflow out-of-the-box — less administrative overhead, and we will co-invest in your onboarding capacity."

**Frequency**: Bi-weekly working group; quarterly CE-level
**Channel**: MCA architect community of practice

### DfT TAG Unit

**Primary Message**: "You own the microservice source code and its Data Book versioning. The BCR logic is never opaque."

**Frequency**: Embedded in sprint (daily); monthly escalation
**Channel**: Joint product team

### ICO / DPOs

**Primary Message**: "DPIA before alpha, lawful basis documented per authority, Article 28 DPAs in place before Private Beta."

**Frequency**: Quarterly
**Channel**: DPO forum; ICO prior consultation if processing is novel

### NAO / PAC

**Primary Message**: "Consolidated pipeline, TCoP-compliant, audited TCO, DPIA-complete. This is the answer to the BSIP fragmentation critique."

**Frequency**: Annual (NAO); on-demand (PAC)
**Channel**: Accounting Officer report; pre-issue engagement

### Campaign groups / public

**Primary Message**: "Outcomes data published openly on `data.gov.uk` with quarterly refresh and stable URIs."

**Frequency**: Quarterly data-publication milestones
**Channel**: `data.gov.uk`; DfT blog; stakeholder newsletter

---

## Change Impact Assessment

### Impact on Stakeholders

| Stakeholder | Current State | Future State | Change Magnitude | Resistance Risk | Mitigation Strategy |
|-------------|---------------|--------------|------------------|-----------------|---------------------|
| DfT Assurance Hub | DP1–DP7 by SharePoint + email | Platform-driven workflow with TAG microservice | HIGH | MEDIUM | Co-design; early-adopter status; no headcount reduction narrative |
| GMCA / WMCA (Tier-1) | Dynamics-based, self-governed | Federation APIs + outcomes feed only | LOW | MEDIUM (political) | Principle commitment; no forced UI; Mayoral champion |
| Tier-2 MCAs (4+1) | Bespoke per-MCA | Platform-hosted recipient view + API federation | MEDIUM | LOW-MEDIUM | Onboarding playbook; capacity-building fund |
| Tier-3 MCAs + EMCCA | Nascent, some bespoke | Platform as primary case-management | HIGH | LOW | Capacity uplift investment; tech-enabled onboarding |
| DfT TAG Unit | Spreadsheet-based BCR | API-delivered microservice they own | HIGH | MEDIUM | Source-code ownership; embedded engineers |
| HMT / NISTA | Reactive reporting | Real-time pipeline feeds | MEDIUM | LOW | Early joint-governance |
| ICO / DPOs | Fragmented multi-controller picture | Joint-controller agreements in place | MEDIUM | LOW | Early DPIA; template DPAs |
| Campaign groups | PDF outcomes data | `data.gov.uk` feeds | LOW | LOW | Open-data publication commitment |

### Change Readiness

**Champions** (Enthusiastic supporters):

- MHCLG Digital (validates their platform)
- DfT TAG Unit (if microservice ownership committed)
- CDDO (exemplar of TCoP reuse)
- Tier-3 MCAs & EMCCA (need the capability uplift)
- Transparency campaign groups (open data wins)

**Fence-sitters** (Neutral, need convincing):

- GMCA, WMCA (politically cautious; need written autonomy commitments)
- HMT (will support once drawdown integration demonstrated)
- NISTA (will champion once data schema stabilises)

**Resisters** (Opposed or skeptical):

- Potentially commercial SaaS vendors if procurement route favours reuse
- Potentially DfT Assurance Hub staff concerned about role change
- Potentially a political actor seeking to deliver "quickly" via off-the-shelf SaaS

---

## Risk Register (Stakeholder-Related)

### Risk R-1: MHCLG Funding Service immaturity delays MVP

**Related Stakeholders**: SRO, MHCLG Digital, HMT

**Risk Description**: MHCLG Funding Service launched December 2025 with only 2 grants onboarded; its extension velocity for CRSTS-scale use cases is unknown.

**Impact on Goals**: G-1 (MCA onboarding), G-5 (reuse decision)

**Probability**: MEDIUM
**Impact**: HIGH

**Mitigation Strategy**: Technical fit workshop in first 30 days; joint engineering governance board; time-boxed reuse decision at SOC+3 months; documented commercial-SaaS fallback.

**Contingency Plan**: Fall back to Flexi-Grant or Salesforce GovGrants as interim, while continuing to invest in MHCLG upstream contributions.

---

### Risk R-2: Tier-1 MCA (GMCA or WMCA) publicly rejects the platform

**Related Stakeholders**: SRO, GMCA, WMCA, DG, Ministers

**Risk Description**: A Mayor perceives the platform as regression on Integrated Settlement autonomy and publicly withdraws engagement, triggering a cascade at Tier-2.

**Impact on Goals**: G-1, G-4, O-1

**Probability**: MEDIUM
**Impact**: CRITICAL

**Mitigation**: Federated-design principle (written, signed); Mayoral correspondence; shared governance authorship; Tier-1 gets API-only participation option with no forced UI.

**Contingency**: Reframe platform scope to Tier-2/Tier-3 only; continue Tier-1 API integration on opt-in.

---

### Risk R-3: NISTA data schema churn forces late-stage re-architecture

**Related Stakeholders**: NISTA, SRO, delivery team

**Risk Description**: NISTA is new (April 2025); its data and reporting schema may change significantly during our build, forcing rework.

**Impact on Goals**: G-3, O-1

**Probability**: HIGH
**Impact**: MEDIUM

**Mitigation**: Embed a NISTA analyst in the delivery team; abstract NISTA-specific fields via anti-corruption layer; monthly schema review.

**Contingency**: Maintain schema versioning; accept one post-beta rework cycle as planned cost.

---

### Risk R-4: SRO not appointed before SOC submission

**Related Stakeholders**: DG Rail/Places/Local Transport, Perm Sec

**Risk Description**: Without an SRO, no accountable owner exists for spend controls, MCA engagement, or NISTA interface.

**Impact on Goals**: All.

**Probability**: MEDIUM
**Impact**: HIGH

**Mitigation**: DG commitment to appoint by end Q1 2026; interim sponsor from DG's office.

**Contingency**: DG carries SRO accountability personally until appointment made.

---

### Risk R-5: DPIA reveals unresolved joint-controller ambiguity with MCAs

**Related Stakeholders**: SIRO, ICO, MCA DPOs

**Risk Description**: Federation model may create joint-controller rather than controller-processor relationships, which are more complex under UK GDPR.

**Impact on Goals**: G-6, O-5

**Probability**: HIGH
**Impact**: MEDIUM

**Mitigation**: Early DPIA; Cabinet Office data-sharing agreements template; ICO prior consultation if novel.

**Contingency**: Data-flow redesign to minimise joint controllership.

---

### Risk R-6: TAG Unit rejects externalising BCR logic

**Related Stakeholders**: TAG Unit, Chief Analyst, SRO

**Risk Description**: TAG Unit sees microservice as a loss of control over Green Book appraisal integrity.

**Impact on Goals**: G-2, O-2

**Probability**: LOW-MEDIUM
**Impact**: HIGH

**Mitigation**: Source-code ownership to TAG Unit; embedded engineers; version control of Data Book clearly surfaced in API.

**Contingency**: Revert to TAG-hosted spreadsheet calling platform APIs; reduced reuse benefit.

---

### Risk R-7: Procurement Act 2023 transition (G-Cloud 14 → 15) creates window-of-opportunity gap

**Related Stakeholders**: DfT Commercial, SRO

**Risk Description**: G-Cloud 15 launches March 2026 under new rules; call-offs made too early miss G-Cloud 15 benefits, too late miss G-Cloud 14 certainty.

**Impact on Goals**: G-5 fallback options, G-1 timing

**Probability**: MEDIUM
**Impact**: LOW-MEDIUM

**Mitigation**: Book G-Cloud 14 window for any commercial component by March 2026; otherwise commit to G-Cloud 15 in SOC.

**Contingency**: Defer commercial procurement to Q3 2026 to land cleanly in G-Cloud 15.

---

### Risk R-8: NAO publishes a critical city-region-funding report pre-FBC

**Related Stakeholders**: NAO, Perm Sec, SRO

**Risk Description**: NAO may publish a follow-up to its BSIP critique that reshapes the political context mid-build.

**Impact on Goals**: G-1, G-7, O-1

**Probability**: MEDIUM
**Impact**: MEDIUM (could be positive if platform is well-positioned)

**Mitigation**: Pre-publication engagement with NAO team; position platform as the response to NAO critique.

**Contingency**: Re-baseline OBC/FBC messaging to reference NAO findings directly.

---

## Governance & Decision Rights

### Decision Authority Matrix (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Reuse-or-fork of MHCLG Funding Service | Enterprise Architect | SRO | DfT CDIO, MHCLG Digital, CDDO | HMT, NISTA, MCAs |
| Principles (federated design, no forced UI) | Enterprise Architect | SRO | MCAs, CDDO, SIRO | HMT, NISTA |
| Business case (SOC / OBC / FBC) | Delivery PM + Finance | SRO | HMT, DfT CDIO, NISTA | Perm Sec, MCAs |
| Technology choices (platform substrate) | Technical Lead | Enterprise Architect | DfT CDIO, Security, Service Owner | DfT Commercial, MCAs |
| DPIA approval | DPO | SIRO | SRO, MCA DPOs, ICO (if novel) | MCAs, Perm Sec |
| Accessibility / Service Assessment pass | Service Owner | SRO | GDS assessors, accessibility leads | Delivery team |
| MCA onboarding sign-off (per MCA) | Service Owner | SRO + MCA CE | SIRO, DPO, Commercial | HMT, NISTA |
| TAG Data Book release handling (microservice) | TAG Unit | DfT Chief Analyst | Delivery team | HMT, NISTA |
| NISTA pipeline-update schema contract | Enterprise Architect | SRO | NISTA, DfT Finance | HMT, MCAs |
| Security classification + GovAssure pass | Cyber Security Lead | SSRO / SIRO | Security Architect, DSO | SRO |
| Open-sourcing under OGL v3 (microservice) | Service Owner | SRO | DfT Commercial, DfT Legal, CDDO | HMT, NISTA, other depts |
| Go / No-go for Public Beta | SRO | DG Rail/Places/Local Transport | CDDO (Service Assessment), MHCLG, Security, SIRO, MCAs | All |

### Escalation Path

1. **Level 1**: Product Manager / Delivery Manager (day-to-day scope, backlog, impediments)
2. **Level 2**: Service Owner / Enterprise Architect (technical direction, integration decisions)
3. **Level 3**: SRO (budget variance, MCA relationship risks, NISTA/HMT escalations)
4. **Level 4**: DG Rail, Places & Local Transport (cross-departmental conflict, Mayoral issues)
5. **Level 5**: Permanent Secretary (Accounting Officer; NAO / PAC-level issues)
6. **Ministerial escalation**: Secretary of State for Transport (policy or political escalation)

---

## Validation & Sign-off

### Stakeholder Review

| Stakeholder | Review Date | Comments | Status |
|-------------|-------------|----------|--------|
| SRO (to be appointed) | PENDING | — | PENDING |
| DG Rail, Places & Local Transport | PENDING | — | PENDING |
| DfT CDIO | PENDING | — | PENDING |
| MHCLG Digital Funding Service team | PENDING | — | PENDING |
| HMT Transport Team (consultative) | PENDING | — | PENDING |
| NISTA Assurance (consultative) | PENDING | — | PENDING |
| GMCA / WMCA Digital Directors | PENDING | — | PENDING |

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Sponsor (DG) | | | |
| SRO | | | |
| Enterprise Architect | | | |
| DfT CDIO | | | |

---

## Appendices

### Appendix A: Stakeholder Interview Summaries

No stakeholder interviews conducted at this discovery-research stage. This document is seeded from public-domain research. Planned interviews (to be scheduled by SRO office):

- MHCLG Digital Funding Service lead
- DfT TAG Unit head
- GMCA and WMCA portfolio directors
- NISTA assurance lead for transport
- HMT Transport team deputy director

### Appendix B: Survey Results

Not applicable at this stage.

### Appendix C: References

- `projects/000-global/external/dft-funding-strategy-notes-v1.0.md` (companion strategy brief)
- `projects/000-global/external/dft-transforming-city-regions-research-v1.0.md` (discovery research)
- Government Functional Standard GovS 005 (Digital)
- Government Functional Standard GovS 007 (Security)
- HMT Integrated Settlement policy documents (gov.uk)
- NAO reports on BSIP and local transport funding
- `communitiesuk/funding-service` (MHCLG, OGL v3)
- Cabinet Office Minimum Requirements for Grants

---

## External References

> This section provides traceability from generated content back to source documents.

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| DFSN | dft-funding-strategy-notes-v1.0.md | Strategy | 000-global/external/ | Discovery-phase strategy brief accompanying the main research document |
| DTCR | dft-transforming-city-regions-research-v1.0.md | Research | 000-global/external/ | Discovery-phase market and landscape research on DfT Transforming City Regions funding |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| DFSN-C1 | DFSN | §1 "The problem" | Stakeholder Need | "The administrative overhead falls on a DfT central team and 9 MCA counterparts, each running its own Green Book assurance framework and programme-management tooling. There is no shared platform." |
| DFSN-C2 | DFSN | §2 "The 8-MCA (now 9-authority) landscape" | Stakeholder Need | "CRSTS2 extends to nine eligible Mayoral Combined Authorities ... GMCA and WMCA already operate under Integrated Settlements from April 2025 ... Five more MCAs plus the GLA follow in 2026–27 (North East, South Yorkshire, West Yorkshire, Liverpool City Region)." |
| DFSN-C3 | DFSN | §6 "What to do in the next 30 days" and §2 | Stakeholder Need | "NISTA ... holds a £530bn/780-project pipeline." |
| DFSN-C4 | DFSN | §3 "The build-vs-buy verdict" | Design Decision | "MHCLG's new Funding Service went live in December 2025, is built on Python/Flask/Aurora Postgres, is published under the Open Government Licence v3 at github.com/communitiesuk/funding-service, and is explicitly designed to be reused across government." |
| DFSN-C5 | DFSN | §2 and §4 Bet 3 | Stakeholder Need | "TfGM runs Microsoft Dynamics 365 CE + Power Platform, TfWM has a GOV.UK-aligned design system and Power BI dashboards, WYCA publishes a DP1–DP7 assurance framework ... The DfT platform must not ask MCAs to replace their existing Dynamics / Salesforce / portfolio tools." |
| DFSN-C6 | DFSN | §3 and §4 Bet 4 | Compliance Constraint | "The gaps the MHCLG Funding Service does not close ... Green Book 5-case assurance workflow — specifically SOC/OBC/FBC progression, DP1–DP7 decision gates, VfM categorisation, and BCR calculation against the DfT TAG Data Book." |
| DFSN-C7 | DFSN | §3 "The build-vs-buy verdict" | Procurement Constraint | "Commercial grant-management SaaS (Flexi-Grant, SmartSimple, Blackbaud, GovGrants, Civica Dynamics) should be kept on the shortlist as a fallback / interim ... All six are live on G-Cloud 14." |
| DFSN-C8 | DFSN | §5 "Headline numbers" | Business Requirement | "Scale of underlying grant relationship: £15.6bn / 5 years / 9 MCAs (CRSTS2 + TCR)" |
| DFSN-C9 | DFSN | §1 "The problem" | Risk Factor | "The NAO has already flagged the fragmentation cost in bus funding: 13 separate streams, 19% of BSIP capital delivered by December 2024, capacity-to-manage cited as a root cause." |
| DFSN-C10 | DFSN | §2 and §5 | Business Requirement | "Over £500m has been front-loaded into 2025–26 / 2026–27." |
| DFSN-C11 | DFSN | §5 "Headline numbers" | Design Decision | "Programme administrative platform indicative 3-year TCO: £3m–£6m (hybrid: reuse MHCLG FS + bespoke TAG/BCR layer + GOV.UK platforms)" |
| DFSN-C12 | DFSN | §4 "Bet 6 — Open-source" | Design Decision | "The combined DfT-side asset (TAG-BCR microservice + Integrated Settlement outcomes data model + MCA federation SDK + NISTA reporting adapter) is of direct reuse value to DWP, MHCLG, DESNZ, NHS England, Scottish Government, Welsh Government and Northern Ireland devolved administrations." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| dft-transforming-city-regions-research-v1.0.md | 000-global/external/ | Main research document reviewed; detailed content (vendor comparisons, TCO models) feeds directly into `/arckit:research` outputs already and will be referenced formally in `/arckit:requirements` and `/arckit:sobc`. Not quoted directly here to avoid duplicating the strategy-notes distillation. |
| vendors/*.md (6 profiles) | 000-global/external/vendors/ | Vendor-specific detail is out of scope for stakeholder analysis; will be referenced in `/arckit:evaluate` and `/arckit:sow`. |
| tech-notes/*.md (3 notes) | 000-global/external/tech-notes/ | Technology-detail reference material; will be referenced in `/arckit:wardley` and `/arckit:hld-review`. |

---

**Generated by**: ArcKit `/arckit:stakeholders` command
**Generated on**: 2026-04-20
**ArcKit Version**: 4.8.0
**Project**: DfT CRSTS Funding Platform (Project 001)
**AI Model**: Claude Opus 4.7 (1M context)
