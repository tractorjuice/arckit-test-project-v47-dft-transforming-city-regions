# Vendor Profile: MHCLG Funding Service (open-source reuse candidate)

> **Template Origin**: Official (adapted — treating a government-built open-source platform as a "vendor" for consistent discovery) | **ArcKit Version**: 4.8.0 | **Command**: `/arckit.research`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | mhclg-funding-service-profile |
| **Document Type** | Vendor Profile (open-source reuse) |
| **Project** | DfT Transforming City Regions (discovery, pre-requirements) |
| **Classification** | PUBLIC |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | Quarterly (tight cadence — platform is new) |
| **Next Review Date** | 2026-07-20 |
| **Owner** | Mark Craddock |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Architecture WG, prospective SRO |
| **Source Research** | dft-transforming-city-regions-research-v1.0 |
| **Confidence** | high (5+ public data points; source code inspected) |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-04-20 | ArcKit AI | Initial creation from `/arckit.research` agent | PENDING | PENDING |

---

## Overview

The MHCLG Funding Service is an open-source, end-to-end grant-administration platform built by the Ministry of Housing, Communities and Local Government (MHCLG) Digital team. It went live in December 2025, replacing MHCLG's previous microservices with a single codebase. The service comprises two tightly-integrated components: **Deliver grant funding** (for civil-service grant teams and form-builders) and **Access grant funding** (for grant recipients). Development is ongoing in the open at `github.com/communitiesuk/funding-service` and the sister repository `github.com/communitiesuk/funding-service-design-fund-application-builder` (FAB). The platform is published under the Open Government Licence v3.0 and is explicitly intended for reuse by other government departments.

## Products & Services

- **Deliver grant funding** — internal service for civil servants to build, configure, publish, and manage grant rounds. WYSIWYG form preview; self-service configuration by non-technical staff.
- **Access grant funding** — external service for grant applicants and recipients to submit, track, and report against awards.
- **Fund Application Builder (FAB)** — Flask-based web app for configuring new application rounds and building tasklists, built to shorten onboarding time for new grants and new rounds.
- **MHCLG Svelte Component Library** — public Svelte 5 implementations of GOV.UK Design System components (`communitiesuk.github.io/mhclg_svelte_component_library`).
- At launch, two grants were onboarded: **Pride in Place Impact Fund** and the **Common Ground Local Resilience Fund**. Onboarding cadence continues through 2026.

## Pricing Model

- **Software licence**: zero (Open Government Licence v3.0).
- **Consumers host and run their own instance** (AWS Aurora Postgres on AWS UK regions). DfT-hosted instance indicative: ~£30–60k/year per environment for hosting.
- **Engineering**: DfT will need 2–3 FTE core engineers on the fork/contribute, plus Green Book / TAG / BCR extensions.
- **Shared governance**: an implied "contribute back" commitment; MHCLG Digital runs a public engineering community.

## UK Government Presence

- **G-Cloud listed**: no (this is an open-source government platform, not a commercial SaaS — consumed via fork/reuse, not procurement).
- **Code repository**: `github.com/communitiesuk/funding-service` and `github.com/communitiesuk/funding-service-design-fund-application-builder` — OGL v3.
- **UK data centres**: consumer-hosted (AWS UK South / UK West or Azure UK South).
- **Accreditations**: inherits from MHCLG Group 1 department Secure-by-Design posture (live users are MHCLG programmes).

## Strengths

- **Zero licence cost**.
- **GOV.UK Design System compliant by default**.
- **Technology Code of Practice Point 8 (share and reuse) mandates considering this first**.
- Simple modern stack: Python 3 / Flask / SQLAlchemy / AWS Aurora Postgres / Cloud Native Buildpacks / GitHub Actions CI/CD.
- Two-tier monolithic architecture (application + database) — simple to operate; no microservices sprawl.
- Self-service grant configuration by non-technical staff (valuable for DfT teams onboarding multiple CRSTS sub-programmes).
- Open to contribution — DfT can co-invest in shared roadmap.
- Aligns with MHCLG Svelte component library — reusable UI.

## Weaknesses

- **Immature** — only two grants onboarded at launch (Dec 2025); production track record is weeks, not years.
- **No multi-tenant, multi-department operating model yet proven** — DfT + 9 MCAs is larger scale than MHCLG's current use.
- **Gaps versus transport-specific needs**: no Green Book 5-case workflow, no TAG Data Book integration, no BCR calculator, no Integrated Settlement outcomes framework.
- **Operational responsibility lies with the consuming department** — DfT will need ops / SRE / security capacity, not just developers.
- Lead developer (Gideon Goldberg) moved to a different MHCLG programme after launch — so continuity will be tested.

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
