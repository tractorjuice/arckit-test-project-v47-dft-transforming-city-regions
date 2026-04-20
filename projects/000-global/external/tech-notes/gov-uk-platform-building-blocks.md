# Tech Note: GOV.UK Platform Building Blocks (Pay, Notify, Forms, One Login, Design System)

> **Template Origin**: Official | **ArcKit Version**: 4.8.0 | **Command**: `/arckit.research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | gov-uk-platform-building-blocks |
| **Document Type** | Tech Note |
| **Project** | DfT Transforming City Regions (discovery, pre-requirements) |
| **Classification** | PUBLIC |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | Annual (or when mandate changes) |
| **Next Review Date** | 2027-04-20 |
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

Five GOV.UK building blocks — **One Login, Notify, Pay, Forms, Design System** — operated by the Government Digital Service (GDS) form the mandatory-first-consideration toolkit for any UK central-government digital service under the Technology Code of Practice (Points 5 and 8) and the cross-departmental adoption mandates. For a DfT / MCA funding-administration platform, all five are in scope; One Login in particular must be in the Phase 1 roadmap because central-government services are required to adopt it by the end of 2027.

## Key Findings

### GOV.UK One Login

- Centrally-provided identity and sign-in service for central-government services.
- **Mandate**: all central-government services to adopt by **end of 2027**. Departments were required to set out adoption plans by March 2025.
- **Live adopters**: Home Office, HMRC, DWP, Companies House, Department for Education among others; by late 2024 over 50 services had adopted with plans to exceed 100 within a year.
- **Functional scope**: authentication, identity proofing (including medium-confidence and high-confidence levels), account management.
- **Cost**: free at point of use (funded centrally by GDS via HMT uplift).
- **Integration**: OpenID Connect / OAuth 2.0 standards.

### GOV.UK Notify

- Managed send-messaging service: email, SMS, letters.
- Pricing: first 25,000 messages per financial year free; beyond that on a per-message basis (letters priced in bands; emails low pence-rate).
- API and web UI; supports templating, scheduling, and reply-tracking.
- Audit trails are built in.

### GOV.UK Pay

- Managed payment service for central gov, LAs, NHS, Police.
- Integrates with Stripe and other acquirers; public-sector preferential card rates.
- Free to use; payment card fees apply (approx. 1.4–1.5% + fixed per-transaction Fs).
- Reporting dashboard, refunds, 3DS included.

### GOV.UK Forms

- Simple online-form-building service.
- Free to gov; suited to straightforward forms (not complex multi-page workflows with branching logic).
- For richer workflow, MHCLG Funding Service or a case-management platform is a better fit.

### GOV.UK Design System

- The open design system used across GOV.UK services.
- Accessibility baked-in (WCAG 2.2 AA); nunjucks/nunjucks-compatible components, plus React, Vue, Svelte (community-contributed) bindings.
- MHCLG publishes a Svelte 5 component library compatible with GOV.UK Design System.
- Mandatory for services hosted under `gov.uk` domains.

### Mandates & policy

- **Technology Code of Practice** (updated 7 July 2025) — 13 points:
  - Point 5 = Use cloud first
  - Point 8 = Share, reuse and collaborate
  - Point 12 (new July 2025) = Make your technology sustainable
- **Use cloud first** policy — consider public cloud first.
- **Secure by Design** — Group 1 (ministerial departments / CNI) and Group 2 (ALBs / agencies) from January 2025.
- **Service Standard** — 14 points; GDS service assessments at Alpha, Beta, Live.

### Implications for the DfT platform

- **One Login in Phase 1** (for applicant identity). Back-office DfT/MCA officers continue to use Entra ID (or the MCA's M365 tenant).
- **Notify for all comms** — application status, award letters, claim acknowledgements.
- **Pay for any peripheral payments** (not drawdowns — drawdowns go via DfT finance systems into MCA ERP).
- **Design System mandatory** — applicant-facing UIs must be compliant.
- **Forms only for genuinely simple forms** — anything grant-application-scale is Funding Service / Dynamics / Salesforce territory.

## Relevance to Projects

- DfT Transforming City Regions Funding (discovery, 2026-04-20)
- Any central-gov digital service from 2025 onwards

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
