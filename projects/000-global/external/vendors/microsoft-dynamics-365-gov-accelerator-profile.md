# Vendor Profile: Microsoft Dynamics 365 Government Accelerator

> **Template Origin**: Official | **ArcKit Version**: 4.8.0 | **Command**: `/arckit.research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | microsoft-dynamics-365-gov-accelerator-profile |
| **Document Type** | Vendor Profile |
| **Project** | DfT Transforming City Regions (discovery, pre-requirements) |
| **Classification** | PUBLIC |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | On-Demand |
| **Next Review Date** | 2026-10-20 |
| **Owner** | Mark Craddock |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Architecture WG |
| **Source Research** | dft-transforming-city-regions-research-v1.0 |
| **Confidence** | high (5+ public data points gathered) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-04-20 | ArcKit AI | Initial creation from `/arckit.research` agent | PENDING | PENDING |

---

## Overview

The Microsoft Dynamics 365 Government Accelerator is a pre-configured industry solution that extends Dynamics 365 Customer Engagement (CE) with a Common Data Model (CDM) and reference workflows for constituent management, case management, grants management, inspections, permits and licensing. It is available on G-Cloud 14 both directly from Microsoft and via implementation partners. Specialised grant-management variants are offered by **Civica**, **HSO** and **ANS** on G-Cloud. In the UK, **Transport for Greater Manchester (TfGM) already runs Dynamics 365 CE and Power Platform**, and **South Gloucestershire Council was the first UK council to deploy the Dynamics 365 Government Accelerator** (via HSO). This makes Dynamics a natural fit for any DfT / MCA grant programme that wants to align with existing installed bases.

## Products & Services

- **Microsoft Dynamics 365 Government Accelerator** (Microsoft / Power Platform)
- **Civica Microsoft Dynamics 365 Grant Management Service** — grant-management-specific implementation on G-Cloud
- **HSO Dynamics 365 Government Accelerator** — partner delivery
- **ANS Dynamics 365 for Grant Management** — partner delivery
- Built on Dynamics 365 CE + Power Platform (Power Apps / Power Automate / Power BI / Power Pages)
- Common Data Model covers grants, cases, constituents

## Pricing Model

- Per-user subscription: Dynamics 365 Customer Service Enterprise or Customer Engagement Plan (~£77–£147/user/month typical list; government tenants often discounted).
- Power Platform licences (Power Apps / Power Automate / Power Pages) priced separately.
- Partner implementation fees typically £300k–£1m+ for a programme of this scale (industry range, not a disclosed contract value).
- Government Community Cloud (GCC) pricing available for UK public sector.

## UK Government Presence

- **G-Cloud 14 listed**: yes — [Microsoft Dynamics 365 Government Accelerator on Digital Marketplace](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/776661635694366); also [Civica Microsoft Dynamics 365 Grant Management Service](https://www.digitalmarketplace.service.gov.uk/g-cloud/services/209167497127334).
- **UK data centres**: yes — Microsoft Azure UK South / UK West regions.
- **References**: TfGM (confirmed Dynamics 365 CE + Power Platform installed base); South Gloucestershire Council (via HSO); multiple LAs.

## Strengths

- Strong alignment with existing MCA installed bases (TfGM confirmed; most MCAs use M365 which shares identity fabric).
- Well-established UK partner ecosystem (Civica, HSO, ANS, Capgemini, KPMG etc.).
- Government Accelerator CDM reduces custom data modelling effort.
- Integrates with Power BI (already heavily used in UK Gov reporting).
- Aligns with UK Gov Microsoft-heavy baseline (OneDrive, Teams, SharePoint, Entra ID).

## Weaknesses

- Per-user + Power Platform economics can escalate at scale.
- Not GOV.UK Design System native — applicant portal (Power Pages) needs theming.
- Not Green Book / TAG / BCR aware — custom appraisal workflow required.
- Vendor lock-in risk via custom Dataverse / plugin / Power Platform development.
- Complexity of enterprise Dynamics administration in a cross-organisation (DfT + 9 MCA) operating model.

## Projects Referenced In

- DfT Transforming City Regions Funding (discovery, 2026-04-20)

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
