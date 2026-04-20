# Technology and Service Research: DfT Transforming City Regions Funding

> **Template Origin**: Official (adapted — discovery-phase, pre-requirements) | **ArcKit Version**: 4.8.0 | **Command**: `/arckit.research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | dft-transforming-city-regions-research-v1.0 |
| **Document Type** | Discovery-Phase Technology and Service Research |
| **Project** | DfT Transforming City Regions Funding (discovery — no project ID yet) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-07-20 |
| **Owner** | Mark Craddock (architect, mark.craddock@mcc.co.uk) |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Architecture WG, prospective sponsoring SRO, MCA architect counterparts |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-04-20 | ArcKit AI | Initial discovery-phase research — no requirements doc; explicit landscape + vendor scan | PENDING | PENDING |

---

## Executive Summary

### Research Scope

This document is a **discovery-phase** scan of the UK Department for Transport (DfT) "Transforming City Regions" funding landscape — covering the legacy Transforming Cities Fund (TCF), the current City Region Sustainable Transport Settlements (CRSTS1), the announced CRSTS2 / Transport for City Regions (TCR) £15.6bn 2027–2032 programme, adjacent BSIP / Local Transport Grant / Active Travel streams, and the new Mayoral Strategic Authority **Integrated Settlement** model being rolled out to 7 MCAs plus the GLA between 2025–26 and 2026–27.

No `ARC-*-REQ-*.md` exists yet. The purpose here is to seed strategy, stakeholder analysis and requirements work for a forthcoming funding-administration/management system that must serve **both sides** of the grant relationship: DfT (and HMT/NISTA for assurance) on one side, and the 8 MCAs (Greater Manchester, West Midlands, West Yorkshire, Liverpool City Region, South Yorkshire, Tees Valley, North East, West of England) plus East Midlands CCA on the other.

**Research Approach**: GOV.UK primary sources (DfT Annual Report 2024-25, Spending Review 2025, CRSTS guidance, Green Book / TAG), Digital Marketplace / G-Cloud 14 listings, Find a Tender / Contracts Finder notices, MHCLG Digital blog posts, NAO reports, UKRI and MHCLG live platforms, govreposcrape search for reusable UK-gov code.

**Research Categories Identified**: 9 (dynamically derived from the problem space — see Section 3).

### Key Findings

- **MHCLG's new Funding Service is the single most disruptive development in the UK grant-admin landscape.** Live from December 2025, built on Python/Flask/Aurora Postgres on a single codebase, published under OGL v3 at `github.com/communitiesuk/funding-service`. It is explicitly designed to be reused across government, and is a credible "no-build, no-buy" reuse candidate for a DfT/MCA funding platform. (Source: [MHCLG Digital blog, Feb 2026](https://mhclgdigital.blog.gov.uk/2026/02/04/funding-service-how-we-built-a-new-funding-platform-for-mhclg/))
- **The 8 MCAs already run heterogeneous programme-assurance stacks**, typically Microsoft Dynamics 365 + Power Platform (TfGM confirmed), combined with bespoke Green Book 5-case assurance workflows and SharePoint / Excel / Power BI back-ends. There is no single common "CRSTS system". Any DfT-side platform must federate with this.
- **CRSTS2 / TCR is £15.6bn over 2027–2032 across 9 eligible MCAs** ([HMT Spending Review June 2025](https://assets.publishing.service.gov.uk/media/686270a608bf2f53761219fc/E03349913_HMT_Spending_Review_June_2025_TEXT_PRINT_CS.pdf)). At least four indicative MCA allocations are public: GMCA £2.5bn, WMCA £2.4bn, EMCCA £2bn (2026–2032), Liverpool City Region £1.6bn, Tees Valley £978m. Over £500m has been front-loaded into 2025–26 / 2026–27. The scale justifies a purpose-built administration capability.
- **The Integrated Settlement model fundamentally changes the "what" of grant administration.** GMCA and WMCA moved to single-pot Integrated Settlements in 2025-26 with an outcomes framework rather than scheme-by-scheme approvals; North East, South Yorkshire, West Yorkshire, Liverpool City Region and the GLA follow in 2026-27 ([GOV.UK Integrated Settlements collection](https://www.gov.uk/government/collections/integrated-settlements-for-mayoral-combined-authorities)). This shifts the data model from project/scheme-level to outcome/indicator-level.
- **NISTA replaces IPA from 1 April 2025** — HMT + Cabinet Office infrastructure delivery authority, holding a £530bn / 780-project pipeline. Any DfT grant-admin platform must integrate with NISTA's assurance reporting regime (successor to the IPA Gateway and GMPP processes).
- **Commercial grant-management SaaS is viable as an interim.** Flexi-Grant (Fluent Technology / Valsoft), SmartSimple Cloud, Blackbaud Grantmaking, Salesforce Public Sector / GovGrants, Microsoft Dynamics 365 Government Accelerator and Civica D365 Grant Management are all live on G-Cloud 14. Flexi-Grant enters from ~£37k Year 1 for 3 users; Blackbaud from £2,565.75/licence/year. None are purpose-built for Green Book 5-case / TAG transport appraisal — customisation is always required.
- **Procurement Act 2023 came into force 24 February 2025**, with G-Cloud 15 expected March 2026 and the enhanced Find a Tender service now live. This creates a ~12 month window where procurement routes change mid-project.
- **govreposcrape returned near-zero matches for grant-management code from UK gov organisations outside MHCLG** — confirming MHCLG Funding Service is currently the only serious open-source reuse candidate for grant application workflow in UK central government.

### Build vs Buy / Reuse Summary (indicative, 3-year, 2026-27 to 2028-29)

| Approach | Capability Mix | 3-Year Indicative TCO | Rationale |
|----------|----------------|-----------------------|-----------|
| **REUSE (MHCLG Funding Service fork/contribute)** | Application intake, assessment, recipient portal, drawdown forms | £1.5m–£3.5m (integration, DfT-specific extensions, ops) | OGL v3, already GOV.UK Design System compliant, multi-tenant pattern, lowest strategic risk. Gaps: Green Book 5-case, TAG, benefits/BCR, Integrated Settlement outcomes. |
| **BUY (SaaS grant platform)** | Flexi-Grant / SmartSimple / GovGrants + config | £2m–£5m (licences + implementation + integration) | Fastest time-to-value; mature workflow engines; proven UK public-sector footprint (UKRI Je-S retired for TFS; NIHR uses Flexi-Grant; multiple trusts use Blackbaud). Gaps: bespoke assurance, data residency specifics, lock-in. |
| **BUILD (Custom on AWS/Azure + GOV.UK platforms)** | Bespoke multi-tenant, Green Book + TAG aware, federated with MCAs | £8m–£15m+ | Only justified if the gap between MHCLG Funding Service and transport assurance is deemed strategically too large. High delivery risk. |
| **HYBRID (Recommended)** | MHCLG Funding Service for intake + grant-recipient portal; bespoke TAG/Green Book assurance layer; GOV.UK Notify/Pay/One Login; Power BI/DfT Statistics Finder for reporting | £3m–£6m | TCoP-compliant (Point 8 reuse), serves both sides of the relationship, minimises lock-in. **See Section 5 for scenarios.** |

### Top Recommended Shortlist (to carry into `/arckit.requirements` → `/arckit.evaluate`)

1. **MHCLG Funding Service (reuse, OGL v3)** — for application intake, form builder, recipient access, claims/drawdown forms. The default starting point under TCoP Point 8.
2. **Microsoft Dynamics 365 Government Accelerator + HSO / ANS / Civica** — for case-managed assurance workflow across MCAs, recognising TfGM and other MCAs have Dynamics installed bases.
3. **Salesforce Public Sector Solutions / GovGrants (NPSP + Spotlight integration)** — alternative platform track; used by Cabinet Office Grants Function; mature integration with government due-diligence tooling.
4. **Flexi-Grant (Fluent Technology, ISO 27001 + Cyber Essentials Plus, G-Cloud 14)** — lowest-risk interim option if speed matters more than strategic fit; established UK-gov grantor customer base.
5. **GOV.UK One Login + GOV.UK Notify + GOV.UK Pay** — mandatory identity, comms and payment building blocks under TCoP and the "full adoption by 2027" One Login mandate.
6. **Power BI / Microsoft Fabric** (for reporting) + **Ordnance Survey Data Hub** (for OS MasterMap Highways Network scheme mapping) — data and geospatial layer common across DfT and MCAs.

### Requirements Coverage

No formal requirements document exists (by design — this is discovery). Instead:

- **9/9 candidate capability categories have at least one viable solution pathway**
- **0 capabilities have no credible option** — but the Green Book 5-case / TAG appraisal / BCR benefits-realisation space has **no off-the-shelf UK public-sector SaaS** and will require either custom development or significant configuration of a case-management platform.

---

## 1. Strategy & Landscape

### 1.1 The funding programmes in scope (as of April 2026)

| Programme | Value | Period | Recipients | Status (Apr 2026) |
|-----------|-------|--------|------------|---------------------|
| **Transforming Cities Fund (TCF)** | £2.5bn (competitive) + £1.28bn (co-developed) | 2017/18–2024/25 (extended to Mar 2025) | 12 city regions (shortlisted from 30 bids) | **Closing**. Final TCF allocations paid in 2024–25. National evaluation (UWE Bristol / Sustrans / Transport for Quality of Life) still ongoing — final report expected 2025/26. [[TCF evaluation, GOV.UK]](https://www.gov.uk/government/publications/transforming-cities-fund-tcf-evaluation) |
| **City Region Sustainable Transport Settlements (CRSTS1)** | £5.7bn | 2022/23–2026/27 | 8 MCAs | **Live, year 4/5**. Delivery plans confirmed; MRM cycle embedded. [[GOV.UK CRSTS confirmed allocations]](https://www.gov.uk/government/publications/city-region-sustainable-transport-settlements-confirmed-delivery-plans-and-funding-allocations) |
| **CRSTS2 / Transport for City Regions (TCR)** | **£15.6bn** | 2027/28–2031/32 (£500m+ brought forward into 2025–27) | 9 MCAs (original 8 plus EMCCA) | **Announced SR25 June 2025**. Allocations in planning / assurance mode. [[HMT SR25]](https://assets.publishing.service.gov.uk/media/686270a608bf2f53761219fc/E03349913_HMT_Spending_Review_June_2025_TEXT_PRINT_CS.pdf) |
| **Local Transport Grant (LTG)** | £2.3bn | From 2025 | Non-CRSTS LTAs | **Live**. Smaller cities, towns, rural. [[GOV.UK LTG allocations]](https://www.gov.uk/government/publications/local-transport-grant-allocations) |
| **Network North / redirected HS2 funding** | £4.7bn (North £2.5bn, Midlands £2.2bn), 2025–2032 | 2025–2032 | North & Midlands LTAs | **Under review** by current government; partial redirection under way. [[Highways Magazine]](https://www.highwaysmagazine.co.uk/4.7bn-Local-Transport-Fund-under-review-DfT-says/14335) |
| **Bus Service Improvement Plans (BSIPs)** | Multiple tranches (13 funding streams identified by NAO 2020-25) | 2020/21–2024/25 + refresh | LTAs and bus operators | **Live but fragmented**. Only 19% of BSIP capital schemes delivered by Dec 2024. [[NAO Local Bus Services in England, June 2025]](https://www.nao.org.uk/wp-content/uploads/2025/06/local-bus-services-in-england.pdf) |
| **Integrated Settlement (single-pot)** | £650m+ (GMCA first year) | Started Apr 2025 (GMCA, WMCA); NECA, SYMCA, WYCA, LCRCA, GLA join 2026–27 | Mayoral Strategic Authorities | **Live and expanding**. Replaces scheme-by-scheme approvals with outcomes framework. [[GOV.UK Integrated Settlement policy]](https://www.gov.uk/government/publications/integrated-settlement-policy-document/integrated-settlement-policy-document) |

### 1.2 The governance and assurance overlay

- **HMT Green Book 2022 five-case model** (strategic, economic, commercial, financial, management) with SOC → OBC → FBC progression remains the backbone.
- **DfT TAG (Transport Analysis Guidance, formerly WebTAG)** — live, with most recent updates published April 2025, new TAG transport appraisal process document published November 2025, and the TAG Data Book continuously updated. TAG Unit A2.3, A1.3, and the May 2025 update bundle are the live appraisal references. [[GOV.UK TAG]](https://www.gov.uk/guidance/transport-analysis-guidance-tag)
- **DfT Value for Money Framework** (updated May 2025) — underpins BCR calculation and VfM categorisation.
- **NISTA** (National Infrastructure and Service Transformation Authority, HMT + Cabinet Office, live from 1 April 2025) replaces IPA and absorbs NIC. Holds £530bn / 780-project pipeline. Becky Wood CEO (ex-EY, ex-DfT). Gateway-review equivalent assurance is part of its remit.
- **MCA-side assurance frameworks** — each MCA publishes its own. West Yorkshire CA publishes a granular 7-activity, DP1–DP7 decision-point framework aligned to Green Book ([WYCA Assurance Framework 2025](https://westyorkshire.moderngov.co.uk/documents/s41856/AssuranceFramework2025.pdf)). Other MCAs follow similar patterns (WMCA Readiness Check, GMCA Portfolio Office).
- **Government Functional Standards**: GovS 002 (Project Delivery), GovS 006 (Finance), GovS 007 (Security), GovS 008 (Commercial), GovS 013 (Counter Fraud).
- **Technology Code of Practice** (last updated 7 July 2025, with new Point 12 "Make your technology sustainable"). Point 5 = cloud-first, Point 8 = share, reuse and collaborate. [[GOV.UK TCoP]](https://www.gov.uk/guidance/the-technology-code-of-practice)
- **Secure by Design** — mandatory for Group 1 (ministerial departments / critical national infrastructure) and Group 2 (ALBs, executive agencies) from January 2025. [[security.gov.uk]](https://www.security.gov.uk/policy-and-guidance/secure-by-design/)
- **Procurement Act 2023** in force from 24 February 2025. Enhanced Find a Tender service live. G-Cloud 15 (first framework under Procurement Act 2023) launches March 2026 with Cyber Essentials Plus mandatory for Lot 1/1b.

### 1.3 What DfT and the MCAs currently run (known evidence)

- **DfT**: No single grant-administration platform publicly identified. DfT Annual Report 2024-25 references a £20.8bn capital budget and a 17-project Government Major Projects Portfolio. DfT Transport Statistics Finder (maps.dft.gov.uk) is the public interactive dashboard. Contract award analysis on Find a Tender shows DfT procuring tools such as the **National Transport Analysis Platform** (June 2025) and individual programme / policy consultancy support.
- **Cabinet Office**: **GGIS** (Government Grants Information System) — the cross-gov register of grants; bespoke system, data model published on GitHub (`cabinetoffice/Government-Grants-Information-System-Metadata`). **Spotlight** — cross-gov automated due-diligence tool on Salesforce, used to screen applications.
- **MHCLG**: **Funding Service** (Deliver grant funding + Access grant funding) — LIVE December 2025, Flask / Python / Aurora Postgres, single codebase, open source under OGL v3. Onboarded Pride in Place Impact Fund and Common Ground Local Resilience Fund.
- **UKRI**: **The Funding Service (TFS)** — replaces Je-S. Full end-to-end from December 2024. Bespoke built by UKRI.
- **Innovate UK**: **Innovation Funding Service (IFS)** — `apply-for-innovation-funding.service.gov.uk`. Bespoke. Project Monitoring Officer workflow is IFS-resident.
- **MCA layer** (examples): TfGM runs Microsoft Dynamics 365 CE / Power Platform (confirmed by current recruitment and management directory data); WYCA runs a seven-activity assurance process managed through its Portfolio Management function and publishes quarterly performance frameworks; WMCA runs an Integrated Settlement programme management office; each MCA has its own mix of SharePoint, Dynamics / Salesforce, Power BI / Tableau.

### 1.4 Policy direction (the "why now")

- **Integrated Transport Strategy** (DfT) — expected to consolidate the fragmented funding streams.
- **10 Year Infrastructure Strategy** (HMT, June 2025) — 780 projects, £530bn, now managed by NISTA.
- **Green Book Review 2025** (June 2025) — findings and actions aimed at simplifying appraisal ([Green Book Review 2025](https://assets.publishing.service.gov.uk/media/687129f52557debd867cc06f/Green_Book_Review_2025.pdf)).
- **Devolution deepening** — Integrated Settlement rollout and GovS-aligned devolution framework push more funding decisions to MCAs; DfT becomes a steward rather than a scheme-approver.
- **Digital sustainability** — TCoP Point 12 (July 2025) adds obligation on energy efficiency of tech; relevant for hosting choices.
- **One Login mandate** — all central-gov services to adopt GOV.UK One Login by end-2027; adoption plans required by March 2025.

### 1.5 Reuse landscape — other UK Gov funding platforms

| Platform | Owner | Stack | Open source? | Relevance |
|----------|-------|-------|-------------|-----------|
| MHCLG Funding Service | MHCLG | Flask/Python/Aurora Postgres | **Yes — OGL v3, `github.com/communitiesuk/funding-service`** | **HIGH** — direct reuse candidate for intake/recipient |
| Fund Application Builder (FAB) | MHCLG | Flask | **Yes — OGL v3** | **HIGH** — enables non-technical grant configuration |
| GGIS | Cabinet Office | Bespoke, Salesforce-adjacent | Metadata only on GitHub | **MEDIUM** — upstream cross-gov register, must integrate |
| Spotlight | Cabinet Office | Salesforce | No | **MEDIUM** — due-diligence, must integrate |
| UKRI The Funding Service (TFS) | UKRI | Bespoke | No | **LOW** — research-funding specific, different UX |
| Innovate UK IFS | Innovate UK | Bespoke | No | **LOW** — innovation-grant specific |
| GOV.UK Forms / Pay / Notify / One Login | GDS | GDS platforms | Open / service-based | **CRITICAL** — mandatory building blocks |

---

## 2. Research Categories

The following nine categories are derived from the problem space (discovery-phase — not from formal FR/NFR/INT/DR requirements, which do not yet exist):

1. Grant & funding-management platforms
2. Business-case / Green Book / TAG assurance tooling
3. Programme & portfolio management
4. Financial management & drawdown / claims processing
5. Data, reporting & visualisation
6. Geospatial (transport-scheme mapping)
7. UK Gov platform building blocks (Pay / Notify / Forms / One Login)
8. Identity & access (multi-authority federation)
9. Document, records & case management

---

## 3. Category 1: Grant & Funding-Management Platforms

**Why This Category**: Core capability. Must handle scheme definition, call/round creation, application intake, eligibility/due-diligence, assessment, award, agreement, claims/drawdown, variations, closure.

### 3.1 Option — REUSE MHCLG Funding Service

- **Description**: Python/Flask/SQLAlchemy on AWS Aurora Postgres. Two-tier monolith. `Deliver grant funding` (for civil servants building grants) + `Access grant funding` (for applicants). WYSIWYG form preview, self-service grant configuration, no-developer onboarding of new grants. Live since December 2025; 2 grants onboarded at launch (Pride in Place Impact Fund; Common Ground Local Resilience Fund).
- **Licence**: Open Government Licence v3.0
- **Repo**: `github.com/communitiesuk/funding-service` (primary), `github.com/communitiesuk/funding-service-design-fund-application-builder` (FAB)
- **UK Gov compliance**: GOV.UK Design System compliant by default; Secure by Design aligned as MHCLG Group 1 department
- **Pricing**: No licence cost. DfT would run/host its own instance (AWS Aurora hosting ~£30–60k/year/env), plus integration/extension engineering
- **Gaps for DfT-CRSTS**: No Green Book 5-case workflow, no TAG appraisal integration, no BCR monitoring, no Integrated-Settlement outcomes framework; multi-tenant across 8 MCAs not yet proven at scale
- **Effort to adopt**: 2–4 person-year initial fork/contribute; ongoing 2–3 FTE for engineering

### 3.2 Option — BUY Flexi-Grant (Fluent Technology / Valsoft)

- **Vendor**: Fluent Technology, Belfast (acquired by Valsoft Corporation in 2022). ISO 9001 / ISO 27001 / Cyber Essentials Plus accredited.
- **G-Cloud 14 listing**: [Flexigrant on Digital Marketplace](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/899316002882517)
- **Customers**: Community foundations, charitable trusts, medical research organisations, councils, local authorities, central government.
- **Pricing (G-Cloud 14 pricing doc)**: **From ~£37k Year 1** for 3 user licences (including Year 1 hosting and support). Scales by number of users (3 to 100+ concurrent). Volume discounts not publicly disclosed.
- **Fit**: Strong application intake, assessment, claims; configurable workflows; non-technical config.
- **Gaps**: Not Green Book / TAG aware; outcomes-framework customisation required; federated multi-authority hosting not its primary pattern.

### 3.3 Option — BUY SmartSimple Cloud for Granting

- **Vendor**: SmartSimple Software (Canada; UK entity SmartSimple Software Ltd). Merged with Foundant 2024. On G-Cloud 13/14. Used by government, federal grants, research funding bodies.
- **G-Cloud 14 listing**: [SmartSimple Cloud for Granting](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/381817298686710)
- **Pricing**: Not publicly disclosed on G-Cloud pricing doc (standard SaaS tiers); typically £50k–£200k+ Year 1 for UK public-sector deployments (industry benchmarks — not from a specific disclosed DfT/MCA contract).
- **Fit**: Highly configurable data model, portals, workflows, payments; strong for complex grants and contracts.
- **Gaps**: Heavier configuration overhead; no Green Book/TAG out of the box.

### 3.4 Option — BUY Blackbaud Grantmaking

- **Vendor**: Blackbaud (US-listed; UK operation). Longest-established nonprofit grant-management vendor.
- **G-Cloud 14 listing**: [Blackbaud Grantmaking](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/798791371526456)
- **Pricing (G-Cloud 14)**: **£2,565.75 per licence per year** (published rate).
- **Fit**: Mature grantmaker workflow, configurable.
- **Gaps**: Heavy US installed base; implementation typically 3–6 months and requires consultant support; not Green Book/TAG oriented; user-licence model may be expensive for 8 MCAs + DfT at scale.

### 3.5 Option — BUY Salesforce Public Sector + GovGrants / Grants Management

- **Vendor**: Salesforce (US); GovGrants by SpendEdge. UK Gov reference: **Cabinet Office Spotlight built on Salesforce** (automated due-diligence). DWP / HMRC / UKHSA use Salesforce at scale.
- **G-Cloud**: Multiple Salesforce and partner listings.
- **Pricing**: Not publicly disclosed; typically per-user org-wide SaaS with partner implementation. For a programme of this scale £500k–£2m+ Year 1 is a realistic industry range (not a disclosed contract value).
- **Fit**: Strongest for complex case management, due-diligence integration, partner ecosystem; aligns with existing Cabinet Office Grants Function tooling.
- **Gaps**: Vendor-lock concerns; cost at scale; not GOV.UK Design System native.

### 3.6 Option — BUY Microsoft Dynamics 365 Government Accelerator (Civica / HSO / ANS)

- **Vendor**: Microsoft (accelerator); partners HSO, ANS, Civica offering specialised grant-management implementations.
- **G-Cloud 14**: Multiple listings including [Microsoft Dynamics 365 Government Accelerator](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/776661635694366) and [Civica Microsoft Dynamics 365 Grant Management Service](https://www.digitalmarketplace.service.gov.uk/g-cloud/services/209167497127334).
- **UK Gov reference**: **South Gloucestershire Council** first UK council to deploy Dynamics 365 Government Accelerator (HSO case study). TfGM already runs Dynamics 365 CE.
- **Pricing**: Not publicly disclosed; per-user subscription + partner implementation; at scale £300k–£1.5m+ Year 1 is plausible (industry range).
- **Fit**: Very strong if MCAs already have Dynamics (TfGM does). Common Data Model covers grants/case management/licensing.
- **Gaps**: Not GOV.UK Design System by default; custom Green Book assurance workflow required.

### 3.7 Option — BUILD Custom

- **Stack (indicative)**: Node/Python on AWS or Azure (UK South region); GOV.UK Design System frontend; OpenAPI microservices; Aurora Postgres / Azure SQL. IaC via Terraform. CI/CD via GitHub Actions. Secure by Design.
- **Effort**: 30–60 person-years for a production platform covering all 9 categories end-to-end. 2–3 year delivery.
- **Rationale**: Only justified if the MHCLG Funding Service gap proves strategically too large, or DfT policy forbids reuse (no evidence today).
- **Risk**: High. GDS service standard assessment required at Alpha, Beta, Live.

### 3.8 Recommendation for Category 1

**Primary: REUSE MHCLG Funding Service** (fork/contribute), extended with a bespoke Green Book/TAG assurance layer.
**Fallback: Microsoft Dynamics 365 Government Accelerator via an accredited partner** if MCA installed base dominates the operating model, since TfGM is already on Dynamics.
**Not recommended**: full build (cost/time/risk); Blackbaud (per-licence model expensive at scale).

---

## 4. Category 2 — Business-Case / Green Book / TAG Assurance Tooling

**Why This Category**: Every CRSTS scheme, and every Integrated Settlement outcomes pack, must be appraised using the Green Book 5-case model and, for transport, TAG. No UK public-sector SaaS product is purpose-built for this today.

**Options**:

- **Bespoke workflow on MS Dynamics / Salesforce / MHCLG Funding Service** — case-management configured against the 5-case model, with DP1–DP7 decision gates (WYCA pattern).
- **Broadleaf** and similar proprietary benefits-realisation tools (limited UK-gov footprint; not G-Cloud featured at scale).
- **HMT Green Book Business Case Services for Cloud and Digital Programmes** — a G-Cloud 14 **service** (consultancy) rather than a product.
- **DfT TAG Data Book** — Excel-led; consumed by analytics pipelines (Power BI / Python / R). No procurable "TAG SaaS" exists.
- **BUILD** — DfT-specific microservice performing BCR calculations against TAG Data Book values, published as an API consumable by MCAs.

**Recommendation**: **BUILD a thin TAG-aware appraisal microservice**, surfaced inside whichever grant platform is chosen (MHCLG Funding Service or Dynamics). Combine with Green Book 5-case templates (configured forms). Buy consultancy (e.g., Sweco, Mott MacDonald, Jacobs, WSP on DOS/G-Cloud) for initial methodology. 3-year TCO £1.5m–£3m including consultancy.

---

## 5. Category 3 — Programme & Portfolio Management

**Why This Category**: DfT and each MCA must run a multi-scheme portfolio with dependencies, gateway reviews, and IPA/NISTA reporting (GMPP equivalents).

**Options**:

- **Microsoft Project for the Web / Project Online** — cross-gov installed base.
- **ServiceNow Strategic Portfolio Management (SPM)** — strong cross-department UK Gov footprint (Home Office, HMRC, MoJ).
- **Atlassian Jira + Jira Align** — strong in delivery teams; weaker in Green Book 5-case stage-gating.
- **Azure DevOps Boards** — for engineering delivery, not portfolio governance.
- **NISTA Infrastructure Pipeline** — DfT must report into this; it is a destination, not a product.

**Recommendation**: Use whatever DfT already runs for GMPP reporting; **do not add a new portfolio tool**. Focus bespoke build on the Green Book assurance workflow and the integration with NISTA's pipeline reporting.

---

## 6. Category 4 — Financial Management & Drawdown / Claims

**Why This Category**: Each MCA draws down against its CRSTS settlement quarterly or against Integrated Settlement outcomes triggers. Must reconcile with HMT OSCAR, DfT Clear Line of Sight, and each MCA's own finance system.

**Options**:

- **GOV.UK Pay** — payment receipt only, not drawdown. Free for gov users (card fees ~1.4–1.5% + fixed per tx).
- **HMT OSCAR II** — the target reporting destination (not procurable; integration only).
- **Bespoke claims workflow on MHCLG Funding Service / Dynamics / Salesforce** — configured.
- **SAP / Oracle Cloud ERP / Unit4** — where MCAs already run them, integrate at the ERP level for drawdown posting.

**Recommendation**: **BUILD** a drawdown/claims workflow on top of the grant platform (MHCLG Funding Service or Dynamics), integrate with DfT Clear Line of Sight and each MCA's ERP via standard finance APIs. Use GOV.UK Pay for any incidental payments. TCO ~£500k–£1m bespoke layer over 3 years.

---

## 7. Category 5 — Data, Reporting & Visualisation

**Options**:

- **Microsoft Power BI** / **Microsoft Fabric** — dominant in UK Gov; DfT uses Power BI dashboards in internal analytics; strong Azure integration.
- **Tableau** — in limited UK Gov use (DWP, some LAs).
- **Qlik** — narrower footprint.
- **GOV.UK publishing** — for statutory transparency; DfT Transport Statistics Finder is the consumer-facing dashboard.
- **Open Data / ONS / Transport Data** — obligation to publish.

**Recommendation**: **Power BI / Fabric** as the enterprise pattern, with open-data publishing to GOV.UK / data.gov.uk. If specific MCAs standardise on Tableau, surface the same data model via both.

---

## 8. Category 6 — Geospatial

**Options**:

- **Ordnance Survey Data Hub** — free-at-point-of-use for public-sector under the Public Sector Geospatial Agreement (PSGA). **OS MasterMap Highways Network** (Roads + Paths) is the authoritative transport network dataset.
- **OS MasterMap Highways Network - Routing and Asset Management** — targeted at asset-managing LAs.
- **Esri ArcGIS Online** — widespread in MCAs for scheme-level mapping.
- **QGIS / PostGIS** — open-source option.

**Recommendation**: **OS Data Hub / MasterMap** (free to DfT/MCAs under PSGA) as the data layer, Esri or QGIS as the authoring tool. No procurement burden for OS data.

---

## 9. Category 7 — UK Gov Platform Building Blocks

| Platform | Status | Cost | Use |
|----------|--------|------|------|
| **GOV.UK One Login** | Mandatory by end-2027; adoption plans due Mar 2025 | Free to gov | Applicant identity |
| **GOV.UK Notify** | Live | Pay-per-message; first 25,000 messages/year free | Email/SMS/letters |
| **GOV.UK Pay** | Live; LA/NHS/Police included from 2017 | Card fees only | Payments |
| **GOV.UK Forms** | Live | Free | Simple forms |
| **GOV.UK Design System** | Live | Free | Frontend |

**Recommendation**: Use all five. Mandatory under TCoP Point 8 and the One Login mandate.

---

## 10. Category 8 — Identity & Access (Federation)

**Options**:

- **GOV.UK One Login** for external applicants (mandatory by end-2027).
- **Entra ID / Azure AD** for DfT civil servants — cross-gov standard.
- **Federated access for 8+ MCAs** — each MCA runs its own IdP (usually Microsoft 365 tenant). Federate via SAML/OIDC into the DfT platform. Existing PSN-to-cloud patterns apply.
- **CDDO shared identity services** — watch this space; no production multi-tenant shared IdP yet.

**Recommendation**: GOV.UK One Login for applicants; federated SAML/OIDC to each MCA's M365 tenant for MCA officer access; Entra ID for DfT.

---

## 11. Category 9 — Document, Records & Case Management

**Options**:

- **Microsoft 365 / SharePoint Online** — dominant in MCAs and DfT.
- **Civica / Idox document management** — specialised in LA space.
- **iManage / NetDocuments** — enterprise DMS.
- **The National Archives 20-year rule** — retention obligation regardless of platform.

**Recommendation**: **Microsoft 365 / SharePoint** as the default case record store, with explicit TNA retention metadata. No new DMS procurement required.

---

## 12. Consolidated 3-Year Indicative TCO

> **Assumptions**: DfT-led, 2026–27 to 2028–29. Excludes direct grant value (£15.6bn TCR is separate). Excludes existing tooling costs already sunk by MCAs. Excludes NISTA/HMT/IPA reporting costs. Figures are **indicative ranges**, not quotes. Risk contingency of 20% (build) / 10% (SaaS escalation) included in upper bound.

| Scenario | Year 1 | Year 2 | Year 3 | 3-Year Total |
|----------|--------|--------|--------|--------------|
| **A. Reuse MHCLG FS + bespoke TAG/Green Book layer + GOV.UK platforms (RECOMMENDED)** | £1.5m–£2.5m | £0.9m–£1.6m | £0.6m–£1.4m | **£3.0m–£5.5m** |
| **B. Buy Dynamics/Salesforce + partner implementation + integration** | £1.2m–£2.2m | £0.7m–£1.3m | £0.7m–£1.5m | **£2.6m–£5.0m** (+vendor lock-in risk) |
| **C. Buy Flexi-Grant / SmartSimple + bespoke assurance layer** | £0.5m–£1.0m | £0.4m–£0.8m | £0.4m–£0.8m | **£1.3m–£2.6m** (fastest but least strategic fit) |
| **D. Custom build on AWS/Azure** | £3.5m–£5.5m | £2.5m–£3.5m | £2.0m–£3.0m | **£8.0m–£12.0m** (high risk) |
| **E. Do nothing (continue with spreadsheets / fragmented MCA systems)** | £0 direct capital; £50m+ p.a. implicit admin cost across DfT+MCAs | n/a | n/a | **Not a viable counterfactual** (per NAO, bus-funding fragmentation already evidenced) |

---

## 13. Build vs Buy vs Reuse — Recommendation

1. **REUSE** where the MHCLG Funding Service fits (intake, forms, recipient portal, claims forms).
2. **BUY** a case-management substrate where the MCAs are already Microsoft-heavy (Dynamics 365 Government Accelerator via HSO / Civica) OR Salesforce-heavy (GovGrants via Cabinet Office partner pattern) — but treat this as a *tactical* choice, not strategic.
3. **BUILD** only the Green Book/TAG/BCR assurance microservice, Integrated-Settlement outcomes framework, and the federation / integration layer. These are the genuinely differentiated capabilities.
4. **ADOPT** the GOV.UK Pay / Notify / Forms / One Login / Design System stack wholesale — mandatory under TCoP, One Login mandate, Secure by Design.

---

## 14. UK Gov Platform Reuse Shortlist

| Platform | Reuse Value | Effort to Integrate | Risk |
|----------|-------------|---------------------|------|
| MHCLG Funding Service (OGL v3) | HIGH — direct fork for intake + recipient portal | MEDIUM — Flask / Python / Aurora. Need DfT ops capability. | LOW — actively maintained; MHCLG team |
| Fund Application Builder (FAB, OGL v3) | HIGH — non-technical grant config | LOW–MEDIUM | LOW |
| GOV.UK Notify | HIGH — all comms | LOW | LOW |
| GOV.UK Pay | MEDIUM — for peripheral payments only | LOW | LOW |
| GOV.UK Forms | LOW — simple forms only; MHCLG FS is richer | LOW | LOW |
| GOV.UK One Login | CRITICAL — mandated by 2027 | MEDIUM | LOW |
| GOV.UK Design System | HIGH — UI layer | LOW | LOW |
| OS Data Hub / MasterMap | HIGH — free under PSGA | LOW | LOW |
| NISTA Infrastructure Pipeline | HIGH — reporting destination | MEDIUM | LOW |
| GGIS | MEDIUM — publication obligation | LOW | LOW |
| Spotlight | MEDIUM — due-diligence integration | MEDIUM | LOW |
| UKRI TFS / Innovate UK IFS | LOW — different domain | — | — |

---

## 15. Risks & Dependencies

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| CRSTS2 / Integrated Settlement policy shifts reduce the scope of what DfT needs to administer (more devolved) | High | High | Keep the DfT-side platform federated; allow each MCA to operate its own recipient view. Don't build a monolith. |
| MHCLG Funding Service is immature (only 2 grants onboarded at launch) and not yet proven at transport scale | Medium | High | Early engagement with MHCLG Digital; pilot on a small CRSTS scheme; contribute back fixes under OGL. |
| G-Cloud 14 → G-Cloud 15 transition (March 2026) and Procurement Act 2023 rules create procurement timing risk | High | Medium | Procure under G-Cloud 14 before 15 replaces (call-off window 12 months post-award); check supplier commitments. |
| 8 MCAs on different Microsoft / Salesforce / bespoke stacks — federation is harder than expected | High | High | Do a reference implementation with 2 MCAs (e.g., TfGM + TfWM) before scaling; publish an MCA integration SDK. |
| NISTA is new (April 2025) and its assurance / reporting interfaces are not yet stable | High | Medium | Defer heavy NISTA integration to Phase 2; file-based interchange as a stopgap. |
| Secure by Design & Technology Code of Practice obligations increase from 2025 onwards | Certain | Medium | Allocate specific security/compliance lead on the project; early SbD attestations. |
| Integrated Settlement outcomes framework data model is not yet published in machine-readable form | High | Medium | Assume JSON/OpenAPI translation from GOV.UK PDFs as an interim. |
| Vendor lock-in (Dynamics / Salesforce) if not designed around portable data model | Medium | High | Define DfT-owned canonical data model; demand exit clauses in call-off contracts. |
| Adoption friction across MCAs with existing programme-management tooling (WYCA, WMCA, TfGM, GMCA portfolio offices) | High | Medium | Lead with "does not replace MCA tooling, integrates with it"; focus on DfT-side view |
| One Login adoption deadline end-2027 — late adopters will be non-compliant | Medium | High | Include One Login in Phase 1 scope |

---

## 16. Recommended Next ArcKit Commands

1. **`/arckit.stakeholders`** — map DfT (SRO, policy, analyst, finance, commercial, NISTA liaison), the 9 MCAs (portfolio office, finance, scheme promoters, elected mayor briefings), HMT (Green Book team, NISTA), and external (applicants, contractors, NAO, PAC, audit).
2. **`/arckit.requirements`** targeting a new `001-*` project (e.g., `001-dft-crsts-funding-platform`) — derive FR/NFR/INT/DR from this discovery. Start with a **pre-SOC / scoping** requirements set, not a full FBC-ready set.
3. **`/arckit.wardley`** — map the capability value chain; early hypothesis: grant intake / recipient portal is **commodity** (reuse MHCLG FS), Green Book / TAG appraisal is **product / custom**, outcomes framework integration is **genesis / custom build**.
4. **`/arckit.sobc`** — once requirements + Wardley are in place, draft the Strategic Outline Business Case using HMT Green Book 5-case.
5. **`/arckit.principles`** — set architecture principles (TCoP-aligned, reuse-first, federated, open-source-default, GOV.UK Design System mandatory).
6. **`/arckit.tcop`** — explicit Technology Code of Practice review before procurement.
7. **`/arckit.secure`** — Secure by Design assessment.
8. **`/arckit.gcloud-search`** or **`/arckit.dos`** — finalise the procurement route for any bought components.

---

## 17. Sources & Citations

### Policy & programme

- HMT, Spending Review 2025 (June 2025) — <https://assets.publishing.service.gov.uk/media/686270a608bf2f53761219fc/E03349913_HMT_Spending_Review_June_2025_TEXT_PRINT_CS.pdf>
- GOV.UK, Integrated Settlements collection — <https://www.gov.uk/government/collections/integrated-settlements-for-mayoral-combined-authorities>
- GOV.UK, CRSTS guidance for MCAs — <https://www.gov.uk/government/publications/city-region-sustainable-transport-settlements-developing-proposals/city-region-sustainable-transport-settlements-guidance-for-mayoral-combined-authorities>
- GOV.UK, CRSTS confirmed allocations — <https://www.gov.uk/government/publications/city-region-sustainable-transport-settlements-confirmed-delivery-plans-and-funding-allocations>
- GOV.UK, Transforming Cities Fund evaluation — <https://www.gov.uk/government/publications/transforming-cities-fund-tcf-evaluation>
- GOV.UK, Local Transport Grant allocations — <https://www.gov.uk/government/publications/local-transport-grant-allocations>
- GOV.UK, DfT Annual Report & Accounts 2024–25 — <https://www.gov.uk/government/publications/dft-annual-report-and-accounts-2024-to-2025/department-for-transport-annual-report-and-accounts-2024-to-2025-html-version>
- NAO, Local Bus Services in England (June 2025) — <https://www.nao.org.uk/wp-content/uploads/2025/06/local-bus-services-in-england.pdf>
- NAO, DfT Overview 2024-25 (November 2025) — <https://www.nao.org.uk/wp-content/uploads/2025/11/Department-for-Transport-Overview-2024-25.pdf>
- GOV.UK, HMT Green Book 2022 and Green Book Review 2025 — <https://www.gov.uk/government/collections/the-green-book-and-accompanying-guidance-and-documents>, <https://assets.publishing.service.gov.uk/media/687129f52557debd867cc06f/Green_Book_Review_2025.pdf>
- GOV.UK, Transport business case guidance — <https://www.gov.uk/government/publications/transport-business-case/transport-business-case-guidance>
- GOV.UK, Transport Analysis Guidance (TAG) and data book — <https://www.gov.uk/guidance/transport-analysis-guidance-tag>, <https://www.gov.uk/government/publications/tag-data-book>
- GOV.UK, DfT Value for Money Framework, May 2025 — <https://assets.publishing.service.gov.uk/media/6899c8393080e72710b2e338/dft-value-for-money-framework.pdf>
- GOV.UK, NISTA Annual Report 2024-25 — <https://www.gov.uk/government/publications/nista-annual-report-2024-2025/nista-annual-report-2024-25>
- IPA Annual Report 2023-24 — <https://assets.publishing.service.gov.uk/media/678a4a9869b9b76c761d0574/IPA_Annual_Report_2023-24.pdf>

### Standards & governance

- GOV.UK, Technology Code of Practice (v current, updated 7 July 2025) — <https://www.gov.uk/guidance/the-technology-code-of-practice>
- GOV.UK, Share, reuse and collaborate — <https://www.gov.uk/guidance/share-and-reuse-technology>
- security.gov.uk, Secure by Design — <https://www.security.gov.uk/policy-and-guidance/secure-by-design/>

### Grant-management platforms & reuse

- MHCLG Digital blog, Funding Service launch (Feb 2026) — <https://mhclgdigital.blog.gov.uk/2026/02/04/funding-service-how-we-built-a-new-funding-platform-for-mhclg/>
- MHCLG Digital blog, Deliver grant funding and Access grant funding (Feb 2026) — <https://mhclgdigital.blog.gov.uk/2026/02/27/deliver-grant-funding-and-access-grant-funding-a-digital-service-built-to-last/>
- GitHub, communitiesuk/funding-service-design-fund-application-builder — <https://github.com/communitiesuk/funding-service-design-fund-application-builder>
- Cabinet Office, GGIS — <https://grantshub.civilservice.gov.uk/ggis/s/login>; GGIS metadata — <https://github.com/cabinetoffice/Government-Grants-Information-System-Metadata>
- Salesforce UK public-sector — <https://www.salesforce.com/uk/customer-success-stories/civil-service/>
- UKRI Funding Service transition — <https://www.ukri.org/apply-for-funding/improving-your-funding-experience/about-ukris-funding-service/>
- Innovate UK IFS — <https://apply-for-innovation-funding.service.gov.uk>
- Digital Marketplace, Flexi-Grant — <https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/899316002882517>
- Digital Marketplace, SmartSimple Cloud for Granting — <https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/381817298686710>
- Digital Marketplace, Blackbaud Grantmaking — <https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/798791371526456>
- Digital Marketplace, Microsoft Dynamics 365 Government Accelerator — <https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/776661635694366>
- Digital Marketplace, Civica Microsoft Dynamics 365 Grant Management — <https://www.digitalmarketplace.service.gov.uk/g-cloud/services/209167497127334>
- HSO, South Gloucestershire case study — <https://www.hso.com/customer-case/hso-public-sector-success-south-gloucestershire-council-becomes-the-first-uk-council-to-deploy-the-dynamics-365-government-accelerator>

### MCAs & assurance

- West Yorkshire Combined Authority, Assurance Framework 2025 — <https://westyorkshire.moderngov.co.uk/documents/s41856/AssuranceFramework2025.pdf>
- West Yorkshire Combined Authority, Performance Management Framework 2025-26 — <https://www.westyorks-ca.gov.uk/media/gq3dgq20/asf-performance-management-framework-25-26.pdf>
- WMCA Readiness Check summary — <https://www.gov.uk/government/publications/integrated-settlement-readiness-checks/west-midlands-combined-authority-readiness-check-summary>
- GMCA Integrated Settlement Outcomes Framework 2025-26 — <https://www.gov.uk/government/publications/integrated-settlements-outcomes-frameworks-for-2025-to-2026/greater-manchester-combined-authority-integrated-settlement-outcomes-framework-2025-to-2026>

### Procurement

- Crown Commercial Service, G-Cloud 14 — <https://www.crowncommercial.gov.uk/news/digital-outcomes-g-cloud-an-update-for-ccs-customers-and-suppliers>
- GOV.UK, Central Digital Platform factsheet (Procurement Act 2023) — <https://www.gov.uk/government/publications/procurement-act-2023-short-guides/central-digital-platform-factsheet-html>
- Find a Tender — <https://www.find-tender.service.gov.uk>
- Contracts Finder — <https://www.gov.uk/contracts-finder>

### Geospatial & data

- Ordnance Survey, OS MasterMap Highways Network (Roads) — <https://www.ordnancesurvey.co.uk/products/os-mastermap-highways-network-roads>
- DfT Transport Statistics Finder — <https://maps.dft.gov.uk/transport-statistics-finder/index.html>

### GOV.UK platforms

- GDS blog, GOV.UK One Login digital sustainability — <https://gds.blog.gov.uk/2025/01/08/gov-uk-one-login-advancing-digital-sustainability-in-government/>
- One Login adoption milestone — <https://www.publictechnology.net/2024/11/12/society-and-welfare/gov-uk-one-login-adoption-hits-50-services-and-plans-to-pass-100-within-a-year/>
- GOV.UK Notify pricing — <https://www.notifications.service.gov.uk/pricing/how-to-pay>
- GOV.UK Pay — <https://www.payments.service.gov.uk/>

---

## 18. Spawned Knowledge

The following standalone knowledge files were created from this research:

### Vendor Profiles

- `projects/000-global/external/vendors/flexi-grant-profile.md` — Created
- `projects/000-global/external/vendors/smartsimple-profile.md` — Created
- `projects/000-global/external/vendors/blackbaud-grantmaking-profile.md` — Created
- `projects/000-global/external/vendors/salesforce-public-sector-profile.md` — Created
- `projects/000-global/external/vendors/microsoft-dynamics-365-gov-accelerator-profile.md` — Created
- `projects/000-global/external/vendors/mhclg-funding-service-profile.md` — Created (treated as a reusable platform/"vendor" for consistent discovery)

### Tech Notes

- `projects/000-global/external/tech-notes/crsts-integrated-settlement-landscape.md` — Created
- `projects/000-global/external/tech-notes/green-book-tag-appraisal.md` — Created
- `projects/000-global/external/tech-notes/gov-uk-platform-building-blocks.md` — Created

---

**Generated by**: ArcKit `/arckit.research` agent (discovery-phase variant)
**Generated on**: 2026-04-20
**ArcKit Version**: 4.8.0
**Project**: DfT Transforming City Regions Funding (discovery, pre-requirements)
**AI Model**: Claude Opus 4.7 (1M context)
