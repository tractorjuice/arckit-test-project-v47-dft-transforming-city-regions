# DfT Transforming City Regions — Strategy Notes

> **Scope**: Strategic brief to accompany the discovery-phase technology research.
> **Audience**: Prospective SRO, enterprise architect, HMT/NISTA liaison, MCA architect counterparts.
> **Length**: ~1,500 words.
> **Status**: DRAFT | v1.0 | 2026-04-20

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | dft-funding-strategy-notes-v1.0 |
| **Classification** | OFFICIAL |
| **Version** | 1.0 |
| **Created** | 2026-04-20 |
| **Owner** | Mark Craddock |
| **Companion document** | `dft-transforming-city-regions-research-v1.0.md` |

---

## 1. The problem, in one paragraph

DfT administers a family of city-region transport funding programmes that are simultaneously **maturing** (Transforming Cities Fund closing out in 2024–25), **operating** (CRSTS1 £5.7bn running to 2026–27), **scaling** (CRSTS2 / TCR £15.6bn for 2027–2032 announced at SR25), and **transforming** (Integrated Settlement single-pot, live for GMCA/WMCA from April 2025, rolling to 5 more MCAs plus the GLA from April 2026). The administrative overhead falls on a DfT central team and 9 MCA counterparts, each running its own Green Book assurance framework and programme-management tooling. There is no shared platform. The NAO has already flagged the fragmentation cost in bus funding: 13 separate streams, 19% of BSIP capital delivered by December 2024, capacity-to-manage cited as a root cause. DfT now has an opportunity — and, post-SR25, a mandate — to consolidate the administrative layer.

## 2. The 8-MCA (now 9-authority) landscape

CRSTS2 extends to nine eligible Mayoral Combined Authorities: **Greater Manchester, West Midlands, West Yorkshire, Liverpool City Region, South Yorkshire, Tees Valley, North East, West of England** (the original 8) plus **East Midlands Combined County Authority** (EMCCA, added). Known public allocations include GMCA £2.5bn, WMCA £2.4bn, EMCCA £2bn (2026–2032 window), Liverpool City Region £1.6bn, Tees Valley £978m. Over £500m has been front-loaded into 2025–26 / 2026–27.

Crucially, **GMCA and WMCA already operate under Integrated Settlements from April 2025**, meaning DfT no longer approves schemes one-by-one — it sets outcome frameworks. Five more MCAs plus the GLA follow in 2026–27 (North East, South Yorkshire, West Yorkshire, Liverpool City Region). The EMCCA, Tees Valley and West of England retain more scheme-level oversight for now.

The MCAs' technology stacks are heterogeneous but dominated by Microsoft: **TfGM runs Microsoft Dynamics 365 CE + Power Platform**, TfWM has a GOV.UK-aligned design system and Power BI dashboards, WYCA publishes a DP1–DP7 assurance framework operated via a portfolio-management function (exact tooling not public). Each MCA has its own identity provider (typically Microsoft 365), its own finance ledger (Unit4 / SAP / Oracle), and its own reporting cadence.

A shared system cannot replace these. It must **federate with them** and sit where the DfT–MCA interface is — intake of schemes/outcomes frameworks, assurance reviews, claims/drawdowns, MRM reporting, evaluation data, and NISTA pipeline updates.

## 3. The build-vs-buy verdict

**Reuse-first, buy-tactical, build-only-the-differentiator.**

The single most important finding of this discovery is that **MHCLG's new Funding Service went live in December 2025**, is built on Python/Flask/Aurora Postgres, is published under the Open Government Licence v3 at `github.com/communitiesuk/funding-service`, and is explicitly designed to be reused across government. It covers the "bread and butter" of grant administration — scheme definition, application intake, form-builder, assessment workflow, recipient portal, and claim forms — and its developer experience lets non-technical grant teams onboard new grants without code changes.

Under TCoP Point 8 (Share, reuse and collaborate) the default answer is **reuse**. The burden of proof falls on any option that re-implements what MHCLG has already built and open-sourced.

The gaps the MHCLG Funding Service does *not* close, and that DfT must either build or buy:

- **Green Book 5-case assurance workflow** — specifically SOC/OBC/FBC progression, DP1–DP7 decision gates, VfM categorisation, and BCR calculation against the DfT TAG Data Book.
- **Integrated Settlement outcomes framework** — machine-readable representation of the outcomes, indicators, and trigger conditions.
- **Multi-authority federation** — identity, data and view separation across DfT central + 9 MCAs + external suppliers.
- **NISTA / HMT reporting interfaces** — pipeline update feeds to NISTA (new from 1 April 2025) and OSCAR/Clear Line of Sight drawdowns.

These four items are the **genuinely differentiated** capabilities. Build them. Keep them thin. Publish them under OGL v3 so other departments (DWP, DESNZ, MHCLG itself) can reuse them when they operate similar programmes.

For everything else — case-management substrate (if that route is chosen over Funding Service), due-diligence, document management, reporting — **reuse GOV.UK platforms and commodity SaaS**. GOV.UK One Login (mandated by end-2027), Notify, Pay, the Design System, OS Data Hub under PSGA, and Power BI/Fabric.

Commercial grant-management SaaS (Flexi-Grant, SmartSimple, Blackbaud, GovGrants, Civica Dynamics) should be kept on the shortlist **as a fallback / interim** if MHCLG Funding Service adoption stalls or a sub-programme needs to go live faster than the strategic platform can be extended. All six are live on G-Cloud 14; Flexi-Grant enters at ~£37k Year 1 for 3 users, Blackbaud publishes at £2,565.75 per licence/year. They are viable for time-boxed pilots, risky as the permanent answer at this scale.

## 4. The 3–5 strategic bets

### Bet 1 — Treat DfT as a steward, not a scheme-approver

The Integrated Settlement trajectory means DfT's role is shifting from "approver of each scheme" to "steward of outcomes". Build the platform around that. The data model should have **outcomes and indicators** as first-class citizens alongside schemes and claims. Design for a future where 7+ MCAs are fully on Integrated Settlements and DfT holds the outcomes ledger, not the scheme ledger. (Evidence: HMT Integrated Settlement policy, GOV.UK.)

### Bet 2 — Fork-and-contribute MHCLG Funding Service

Don't build. Don't buy. **Fork `communitiesuk/funding-service`, extend for transport-specific needs, and contribute reusable parts back upstream.** The risks: MHCLG's platform is immature (2 grants onboarded at launch). The payoffs: zero licence cost, compliant-by-default with GOV.UK Design System / Secure by Design / TCoP, shares an engineering community with MHCLG, de-risks cross-departmental integration (Pride in Place / Local Resilience Fund / CRSTS all using the same substrate). Establish a joint engineering governance board with MHCLG Digital within the first 90 days of the SOBC gate.

### Bet 3 — Federate, do not centralise

The DfT platform must **not** ask MCAs to replace their existing Dynamics / Salesforce / portfolio tools. Build a federated-identity layer (SAML/OIDC to each MCA's M365 tenant), publish clean OpenAPI contracts for scheme / claim / outcome / indicator objects, and supply reference clients. MCAs that want a DfT-hosted recipient view can use the Access Grant Funding component; MCAs with their own systems can integrate via API. **This is the single most important design decision** and it should be made at principles / Wardley stage, not discovered at DLD.

### Bet 4 — Build only the Green Book / TAG / BCR appraisal microservice — and publish its API

The one component no one else has built: a microservice that consumes the DfT TAG Data Book (updated twice yearly, November and May), takes scheme inputs, runs BCR and VfM categorisation, and surfaces results via API to whichever grant platform hosts the assessment workflow. Make this the DfT flagship reusable component — it is valuable to non-DfT programmes too (e.g., DLUHC levelling-up evaluations, DESNZ Net Zero capital).

### Bet 5 — Plan for the G-Cloud 14 → 15 and Procurement Act 2023 transition

The Procurement Act 2023 came into force 24 February 2025 and G-Cloud 15 (the first framework under it) launches March 2026. Any procurement call-off made via G-Cloud 14 between now and March 2026 gives DfT a known rule-set; after that, G-Cloud 15 introduces mandatory Cyber Essentials Plus for Lot 1/1b, weighted supplier scoring, and enhanced Find-a-Tender publication. For a discovery that intends to procure any commercial component, **book the G-Cloud 14 window before it closes** or commit to the G-Cloud 15 timelines openly in the SOBC.

### (Optional) Bet 6 — Open-source the differentiated components under OGL v3

The combined DfT-side asset (TAG-BCR microservice + Integrated Settlement outcomes data model + MCA federation SDK + NISTA reporting adapter) is of direct reuse value to DWP, MHCLG, DESNZ, NHS England, Scottish Government, Welsh Government and Northern Ireland devolved administrations, all of whom run comparable capital-grant regimes. Publishing under OGL v3 costs almost nothing extra and sets DfT up as a "shared service" producer rather than consumer. This is the kind of move NISTA's 10-Year Infrastructure Strategy implicitly rewards.

## 5. Headline numbers to carry into the SOBC

- Scale of underlying grant relationship: **£15.6bn / 5 years / 9 MCAs** (CRSTS2 + TCR)
- Programme administrative platform indicative 3-year TCO: **£3m–£6m** (hybrid: reuse MHCLG FS + bespoke TAG/BCR layer + GOV.UK platforms)
- Alternative, pure SaaS route: **£1.3m–£2.6m** (Flexi-Grant / SmartSimple + bespoke assurance shim) — faster, strategically weaker
- Alternative, custom build: **£8m–£12m+** — not recommended
- Ratio of platform spend to grant throughput: **< 0.04%** — strongly favourable to invest

## 6. What to do in the next 30 days

1. Run `/arckit.stakeholders` against DfT, HMT, NISTA, Cabinet Office Grants Function, and the 9 MCAs' portfolio/finance/digital leads.
2. Engage MHCLG Digital early for a technical fit workshop on the Funding Service.
3. Create a new numbered project (e.g., `001-dft-crsts-funding-platform`) and run `/arckit.principles` and `/arckit.requirements`.
4. Pre-SOC scoping note: confirm whether this is a DfT-only capital project or a joint DfT+NISTA+MCA initiative (this is a governance decision, not a technical one).
5. Decide the governance forum: NISTA-led (assurance authority), DfT SRO-led, or CDDO-chaired (digital shared service). Evidence suggests SRO-led with NISTA assurance and MHCLG technical partnership is the pragmatic route.

---

**Generated by**: ArcKit `/arckit.research` agent (strategy-note companion)
**Generated on**: 2026-04-20
**ArcKit Version**: 4.8.0
**AI Model**: Claude Opus 4.7 (1M context)
