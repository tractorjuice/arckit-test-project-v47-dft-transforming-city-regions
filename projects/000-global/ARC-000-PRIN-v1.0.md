# DfT CRSTS Funding Platform — Enterprise Architecture Principles

> **Template Origin**: Official | **ArcKit Version**: 4.8.0 | **Command**: `/arckit:principles`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-000-PRIN-v1.0 |
| **Document Type** | Enterprise Architecture Principles |
| **Project** | Global (applies across all projects; initially sponsored by Project 001 — DfT CRSTS Funding Platform) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | Annual |
| **Next Review Date** | 2027-04-20 |
| **Owner** | Mark Craddock, Enterprise Architect (prospective) |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING (target: SRO + DfT CDIO) |
| **Distribution** | DfT Enterprise Architecture; Project 001 delivery team; MCA digital leads (9); MHCLG Digital Funding Service team; NISTA liaison; HMT Transport team; CDDO |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-04-20 | ArcKit AI (Claude Opus 4.7) | Initial creation from `/arckit:principles` command, seeded from discovery research and stakeholder analysis | PENDING | PENDING |

---

## Executive Summary

This document establishes the architecture principles governing technology decisions for the DfT CRSTS Funding Platform and related funding-administration initiatives. The principles are tuned to the programme's defining constraints:

- A federated relationship between DfT and 9 Mayoral Combined Authorities under the Integrated Settlement [DFSN-C1]
- A mandatory preference for reuse under the Technology Code of Practice (TCoP), with MHCLG Funding Service as the default substrate [DFSN-C2]
- A £15.6bn grant throughput that justifies a platform spend of no more than a few tens of basis points [DFSN-C3]
- NISTA-assured delivery and NAO-defensible governance [DFSN-C4]

**Scope**: All technology projects, systems, and shared components within the DfT CRSTS Funding Platform programme; referenced as the default principle set for DfT funding-administration systems more broadly.

**Authority**: DfT Enterprise Architecture Review Board (TBC) with CDDO spend-control endorsement.

**Compliance**: Mandatory unless a time-bound, documented exception is approved by the SRO (operational principles) or by DfT CDIO + SIRO (security/data principles).

**Philosophy**: These principles are **technology-agnostic**. They describe WHAT qualities the architecture must have, not WHICH products implement them. Technology selection happens during research and design phases, guided by these principles.

**Non-negotiable principles**: P-1 (Reuse before build), P-2 (Federated, not centralised), P-5 (Secure by Design), P-6 (Accessible by default), P-9 (Lawful data handling) are **hard constraints** on this programme. Exceptions are not available for these.

---

## I. Strategic Principles

### P-1: Reuse Before Build; Buy Only When Reuse Fails (NON-NEGOTIABLE)

**Principle Statement**:
All new capabilities MUST exhaust cross-government reuse options before any new build or buy decision. Where a suitable open-government platform, service or codebase exists (notably the MHCLG Funding Service under OGL v3, GOV.UK One Login, Notify, Pay, Forms, Design System, OS Data Hub), it MUST be adopted by default. A decision to build or buy instead MUST be documented as an Architecture Decision Record (ADR) with explicit reuse-rejection rationale [DFSN-C2][DFSN-C5].

**Rationale**:
TCoP Point 8 (Share, reuse and collaborate) places a positive obligation on departments. Reuse reduces duplication, accelerates delivery, lowers TCO, improves interoperability, and creates a defensible posture under NAO audit. On this programme, ignoring MHCLG Funding Service reuse is a category of decision that will attract PAC scrutiny [DFSN-C6].

**Implications**:

- Before commissioning any new functional capability, a documented reuse search covers: MHCLG Funding Service, `code.gov.uk` / `github.com/alphagov`, Cabinet Office Spotlight, cross-department platform catalogues
- "Fork and contribute" is preferred over private fork; private fork is preferred over full rebuild
- Buy (commercial SaaS) is permitted only as an interim / fallback and MUST have a documented transition plan back to reuse unless explicitly signed off by the SRO
- Differentiated capabilities (the TAG/BCR microservice, Integrated Settlement outcomes schema, MCA federation SDK, NISTA reporting adapter) MUST themselves be published under OGL v3 so that the programme is a net reuse producer, not just consumer

**Validation Gates**:

- [ ] Reuse search documented for every new capability, with search scope, results and decision recorded in an ADR
- [ ] Joint engineering governance board with MHCLG Digital (for Funding Service reuse) is live before SOC submission
- [ ] Build decisions accompanied by a commitment to publish the differentiator under OGL v3
- [ ] Buy decisions accompanied by a time-boxed transition plan or SRO-signed waiver

**Good example**: "We forked `communitiesuk/funding-service` and contributed the outcomes-framework extension upstream; MHCLG has accepted the PR."
**Bad example**: "We issued an RFP for grant management SaaS without a documented reuse search."

**Common violations**:

- "Nobody in government has done exactly this" — without evidence of a search
- Procurement initiated before reuse assessment completed
- Treating MHCLG Funding Service as "MHCLG's tool", not a cross-government platform

---

### P-2: Federated, Not Centralised (NON-NEGOTIABLE)

**Principle Statement**:
The platform MUST federate with the existing technology estates of the 9 MCAs rather than require them to replace, migrate, or restrict their current tooling. Integration occurs via published APIs and event streams; no MCA is required to adopt a DfT-hosted user interface in order to participate [DFSN-C7].

**Rationale**:
Mayoral Combined Authorities have won Integrated Settlement autonomy under HMG devolution policy [DFSN-C1]. A centrally-imposed replacement system represents political regression and will be resisted. MCAs have also invested in Microsoft Dynamics 365, Power Platform, Salesforce, and bespoke portfolio tooling — forced displacement of this estate is neither affordable nor politically viable [DFSN-C7].

**Implications**:

- The platform exposes scheme, claim, outcome, indicator, milestone and drawdown objects via versioned OpenAPI and AsyncAPI contracts
- A reference client SDK is provided for MCAs with limited engineering capacity (EMCCA, smaller CCAs)
- A DfT-hosted "recipient view" is offered as an OPTIONAL component for MCAs that wish to use it
- DfT never demands direct database access to MCA systems; MCAs never demand direct database access to the DfT platform
- Federated identity (SAML / OIDC) is the default authentication pattern; no central user store is imposed on MCAs

**Validation Gates**:

- [ ] API contracts published before Requirements Freeze
- [ ] At least one Tier-1 MCA (GMCA or WMCA) participates via API-only integration as a reference
- [ ] Reference SDK released before Private Beta
- [ ] No platform feature requires an MCA to replace an existing stack component

**Good example**: "GMCA pushes outcome updates via our AsyncAPI contract; their Mayoral view remains Dynamics 365; they have no DfT-hosted UI."
**Bad example**: "All 9 MCAs must onboard to our new recipient portal; Dynamics integration will be deprecated."

**Common violations**:

- Assuming MCAs will adopt a single DfT-hosted UI "because it is simpler for us"
- Direct SQL queries into MCA databases
- Requiring MCAs to use DfT-hosted identity providers for their own users

---

### P-3: Outcomes-First Data Model

**Principle Statement**:
The canonical data model MUST treat **outcomes and indicators** as first-class entities alongside (and increasingly above) schemes, claims and milestones. The schema MUST be forward-compatible with the Integrated Settlement extension to 7+ MCAs by April 2026 [DFSN-C1].

**Rationale**:
DfT's role is shifting from scheme-approver to outcomes-steward [DFSN-C8]. A scheme-centric data model entrenches the old relationship and will require painful refactoring when the Integrated Settlement expands. Building the outcomes-first model from day 1 future-proofs the platform and aligns with HMT's direction of travel.

**Implications**:

- Every scheme links to one or more outcomes; every outcome links to one or more indicators with published measurement definitions
- Outcome and indicator schemas are versioned and published to `data.gov.uk`
- Reporting views are defined in terms of outcomes by default; scheme detail is available to Tier-3 MCAs without being mandatory for Tier-1
- The data model accommodates MCAs at different Integrated Settlement tiers simultaneously

**Validation Gates**:

- [ ] Outcome / indicator entities present in the logical data model before Alpha
- [ ] Schema stability policy defined (breaking changes deprecated over ≥ 2 release cycles)
- [ ] Machine-readable outcomes published to `data.gov.uk` before Public Beta

**Common violations**:

- Outcome fields as free-text memos rather than structured, referenced entities
- Scheme-only reporting dashboards that implicitly exclude Integrated-Settlement MCAs

---

### P-4: Open by Default (Code, Standards, Data)

**Principle Statement**:
All code written by DfT or its suppliers for this programme MUST be published under the Open Government Licence v3 (code and content) unless a written exception applies (security, trade-secret, third-party IP). All data schemas MUST use open standards; all non-sensitive outcome data MUST be published to `data.gov.uk` with stable URIs [DFSN-C9].

**Rationale**:
Open source is a TCoP obligation and a cross-government reuse enabler. Open data is a transparency obligation and answers public-interest scrutiny before it escalates. Stable URIs make the published data usable by third parties (academics, campaign groups, other departments).

**Implications**:

- Source-code repositories are public from day 1 (not "open-sourced at launch")
- Open standards selected for data exchange (JSON Schema, OpenAPI 3, AsyncAPI, GeoJSON for spatial, ISO 8601 for dates)
- Published outcomes data follows the 5-star open-data maturity model (≥ 3 stars mandatory; 5 stars target)
- Closed-source exceptions require written SIRO + CDIO approval with justification
- Publication obligations (Cabinet Office Grants Function minimum requirements) mapped to automated feeds

**Validation Gates**:

- [ ] Repository published under OGL v3 before first commit to main is merged
- [ ] Open-standards register maintained per component
- [ ] `data.gov.uk` publishing pipeline tested before Public Beta
- [ ] Closed-source exception register (expected: empty)

**Good example**: "The TAG-BCR microservice is hosted at `github.com/dft/tag-bcr-service` under OGL v3, with DLUHC actively evaluating reuse."
**Bad example**: "We'll open-source it once it's stable" (i.e. never).

---

### P-5: Secure by Design (NON-NEGOTIABLE)

**Principle Statement**:
All architectures MUST implement defence-in-depth security aligned to NCSC Secure by Design, the NCSC Cyber Assessment Framework (CAF), and the Government Functional Standard GovS 007. Security is NOT a feature to be added later — it is a foundational constraint.

**Rationale**:
The threat landscape requires assuming breach. The platform processes OFFICIAL data (some OFFICIAL-SENSITIVE under claim-fraud or commercial-confidence contexts). NAO and PAC treat cyber-security failures as accountability failures.

**Zero-Trust Pillars**:

1. **Identity-based access**: No network-based trust; every request authenticated
2. **Least privilege**: Role-based access, time-bound where practicable
3. **Encryption everywhere**: Data encrypted in transit (strong TLS) and at rest
4. **Continuous verification**: Structured security logging, correlation, and analysis

**Mandatory Controls**:

- [ ] Multi-factor authentication for all human access (GOV.UK One Login by 2027 end; current best-in-class MFA until then)
- [ ] Service-to-service authentication (mutual TLS, signed tokens, or equivalent)
- [ ] Secrets management via hardened secret store (never in code, config files, or repository)
- [ ] Network segmentation with minimal trust zones
- [ ] Encryption at rest for all data stores
- [ ] Encrypted transport for all network communication (TLS 1.2+ minimum; TLS 1.3 target)
- [ ] Structured logging of authentication and authorisation events with 1-year minimum retention
- [ ] Regular security testing (ITHC/CHECK annually; SAST/DAST in CI; SBOM per release)

**Compliance Frameworks**:

- NCSC Secure by Design principles (mandatory)
- NCSC CAF (via GovAssure) for high-impact services
- ISO/IEC 27001 control families (mapped, not necessarily certified)
- UK GDPR / Data Protection Act 2018 (see P-9)

**Exceptions**: NONE. Specific control implementations may vary with compensating controls documented in the threat model, but the principle is inviolate.

**Validation Gates**:

- [ ] Threat model completed and reviewed per service
- [ ] Security controls mapped to requirements
- [ ] GovAssure CAF assessment scheduled where applicable
- [ ] Incident response runbook created and tested

---

### P-6: Accessible by Default (NON-NEGOTIABLE)

**Principle Statement**:
All user-facing components MUST meet WCAG 2.2 AA at minimum and be compliant with the Public Sector Bodies Accessibility Regulations 2018. Accessibility is tested continuously, not audited retrospectively.

**Rationale**:
PSBAR 2018 is a legal obligation. Accessibility failure is a service-assessment failure and a legal enforcement risk. MCA staff and grant recipients include users with a wide range of assistive-technology needs; designing around the median user fails the programme's statutory duties.

**Implications**:

- GOV.UK Design System components used by default (already meet WCAG 2.2 AA)
- Automated accessibility checks run in CI (`axe-core` or equivalent)
- Manual accessibility audit by a third party before Public Beta
- Published accessibility statement per service
- No reliance on a separate "accessible version" — primary service IS the accessible service

**Validation Gates**:

- [ ] Automated a11y checks in CI with zero critical issues
- [ ] Manual audit booked before Public Beta
- [ ] Accessibility statement published per service
- [ ] GOV.UK Design System (or audited equivalent) used for UI components

**Exceptions**: NONE. Specific AAA-level criteria may be deferred with documented reasoning, but AA is mandatory.

---

### P-7: Observability as a First-Class Requirement

**Principle Statement**:
All systems MUST emit structured logs, metrics, and distributed traces sufficient to detect, diagnose, and recover from failures without code changes.

**Telemetry Requirements**:

- **Logging**: Structured JSON with correlation/request IDs
- **Metrics**: Volume, latency (p50/p95/p99), error rate, saturation — the RED + USE signals
- **Tracing**: Distributed trace context carried across service boundaries
- **Alerting**: SLO-based alerting with actionable runbooks (not threshold-spam)

**Required Instrumentation**:

- Request volume, latency distribution, error rate per endpoint
- Resource utilisation (CPU, memory, network, storage)
- Business metrics (schemes submitted, drawdowns approved, outcomes reported)
- Security events (auth failures, policy violations, anomalous patterns)

**Log Retention**:

- Security and audit logs: 1–7 years per compliance context
- Application logs: 90 days minimum
- Metrics: 13 months minimum (enables year-on-year comparison)

**Validation Gates**:

- [ ] Structured logging, metrics, and tracing instrumented per service
- [ ] Dashboards and alerts configured before first non-dev deployment
- [ ] SLOs and SLIs defined per service before Public Beta
- [ ] Runbooks created for common failure scenarios

---

### P-8: Scalability and Elasticity

**Principle Statement**:
All services MUST be designed to scale horizontally to meet demand, with the ability to adjust capacity based on load.

**Rationale**:
Demand across 9 MCAs is uneven and bursty — quarterly claim deadlines concentrate traffic; Integrated Settlement onboarding events create one-off spikes; SR and FBC cycles drive reporting bursts. Vertical-only scaling is a dead end at this scale.

**Implications**:

- Stateless application components wherever practicable; state externalised to managed stores
- No hard-coded capacity limits or single-instance assumptions
- Load testing demonstrates capacity headroom at 2× peak before Public Beta
- Auto-scaling triggers defined on business-relevant metrics (queue depth, request rate), not only infrastructure metrics

**Validation Gates**:

- [ ] Services scale horizontally in load tests
- [ ] No single points of failure limiting scaling
- [ ] Cost model reflects variable capacity

---

### P-9: Resilience and Fault Tolerance

**Principle Statement**:
All systems MUST gracefully degrade when dependencies fail and recover automatically, without data loss beyond the agreed RPO or downtime beyond the agreed RTO.

**Implications**:

- Circuit breakers on external dependencies (NISTA, OSCAR, MHCLG Funding Service hosted instance, MCA federation endpoints)
- Timeouts on every network call
- Retries with exponential backoff and jitter for transient failures
- Graceful degradation for non-critical services (e.g. reporting is read-only when the write path is recovering)
- Chaos testing in non-production

**Target SLOs** (indicative, to be ratified by Service Owner):

- Core platform availability: **99.9 %** (≤ 43 min/month downtime)
- TAG/BCR microservice: **99.5 %** (batch-friendly)
- Public outcomes feed: **99.9 %**
- RPO: **≤ 15 minutes** for transactional data; **24 hours** for analytics stores
- RTO: **≤ 4 hours** for core services

**Validation Gates**:

- [ ] Failure modes identified and mitigated
- [ ] RTO and RPO defined per service
- [ ] Automated failover tested
- [ ] Degraded-mode behaviour documented

---

## II. Data Principles

### P-10: Data Sovereignty and UK Hosting

**Principle Statement**:
All personal data processed by the platform MUST be hosted within the United Kingdom. All data, personal or not, MUST be subject to UK legal jurisdiction primarily; onward transfers outside the UK-adequacy area MUST use appropriate UK-GDPR transfer mechanisms [DFSN-C10].

**Data Classification Tiers**:

1. **Public**: Outcomes open data, published indicators, public-facing service content
2. **Internal (OFFICIAL)**: Staff case-work, scheme metadata, routine claim processing
3. **Confidential (OFFICIAL-SENSITIVE)**: Commercial-confidence bid data, pre-decision assurance judgements, fraud-related flags, personal-data risk-containing records
4. **Restricted**: None anticipated; any SECRET classification triggers a re-scope

**Data Residency**:

- Primary, secondary, and backup storage within the UK
- No processor sub-processing outside UK-adequacy area without a documented UK-GDPR transfer mechanism (standard contractual clauses or equivalent)
- Extraterritorial-law exposure (e.g. US CLOUD Act) assessed per candidate supplier and documented in the supplier risk register

**Data Retention**:

- Automated deletion after the defined retention period (grant-administration records: typically 6 years from scheme closure; longer where NAO / TNA rules apply)
- Legal-hold process for litigation, fraud, or NAO audit
- Backup retention aligned with both compliance and recovery requirements

**Validation Gates**:

- [ ] Data classification performed for all stores
- [ ] Residency requirements mapped to infrastructure and contracts
- [ ] Retention policies configured with automated deletion
- [ ] Extraterritorial-law exposure documented per supplier

---

### P-11: Single Authoritative Source per Data Domain

**Principle Statement**:
Every data domain (schemes, outcomes, indicators, claims, drawdowns, scheme sponsors, authority entities, TAG scoring runs) MUST have a single authoritative source. Derived copies MUST be clearly labelled, read-only, and synchronised via a documented mechanism.

**Implications**:

- System of record identified for each data entity and documented in the data model
- Derived copies (reporting cubes, local caches, MCA downstream views) are read-only
- Synchronisation strategy defined for each derived copy (frequency, freshness, conflict handling)
- No bidirectional synchronisation without a documented conflict-resolution strategy
- Master data for reference entities (authority codes, indicator definitions, TAG Data Book versions) is managed centrally

**Good example**: "The TAG Data Book version in use is the authoritative fact, held by the TAG-BCR microservice; MCAs consume it via signed-version API calls."
**Bad example**: "Each MCA keeps its own copy of the TAG Data Book, updated manually."

---

### P-12: Lawful, Documented Multi-Controller Data Handling (NON-NEGOTIABLE)

**Principle Statement**:
Every processing activity MUST have a documented lawful basis under UK GDPR Article 6 (and Article 9 where applicable). Controller / processor / joint-controller relationships across DfT and the 9 MCAs MUST be explicitly documented, with Article 28 data-processing agreements in place before any personal data flows.

**Rationale**:
The federation creates complex multi-controller scenarios that are the highest category of UK-GDPR risk on this programme. Getting it wrong invites ICO enforcement and stakeholder trust collapse [STKE-SD8].

**Implications**:

- A DPIA is drafted before Alpha and approved before Private Beta
- Role clarity per data flow: who is controller, who is processor, who is joint-controller
- Article 28 DPAs executed with every MCA and every material sub-processor
- Data-sharing agreements (beyond DPAs) where processing is joint-controller
- ICO prior consultation where processing is novel (likely for automated BCR / AI-assisted triage if that is ever in scope)
- Subject rights (access, rectification, erasure, portability) implementable in practice, not just theory

**Validation Gates**:

- [ ] DPIA present and approved before Private Beta (`ARC-001-DPIA-v1.0`)
- [ ] DPA register complete
- [ ] Subject-rights fulfilment tested
- [ ] Breach notification process tested (72-hour capability)

**Exceptions**: NONE. Novel processing may require ICO prior consultation, but the obligation itself is inviolate.

---

### P-13: Appraisal Integrity Owned by Professional Accountability

**Principle Statement**:
Where the platform automates or surfaces calculations that carry professional-accountability weight (notably TAG-based BCR, VfM categorisation, Green Book 5-case appraisal logic), the calculation logic MUST be owned and signed off by the accountable professional unit (the DfT TAG Unit / Chief Analyst for transport appraisal) and MUST expose the Data Book version used [DFSN-C11].

**Rationale**:
Automating professional judgement without professional ownership produces two failure modes: opaque calculations that NAO cannot audit, and drift from the published Green Book / TAG methodology that HMT relies on. Neither is acceptable on a £15.6bn programme.

**Implications**:

- TAG-BCR microservice source code is owned by the TAG Unit; delivery team contributes under their review
- Every output carries the TAG Data Book version (ISO-dated) that produced it
- Deprecations of Data Book inputs are surfaced in API responses, not silently absorbed
- Where an AI / ML component is introduced to assist (e.g. scheme-category triage), an Algorithmic Transparency Recording Standard (ATRS) record is mandatory

**Validation Gates**:

- [ ] TAG Unit has at least one embedded engineer or named code reviewer on the microservice
- [ ] Data Book version is surfaced in every API response and persisted with every calculation record
- [ ] ATRS records present for any ML-assisted appraisal step

---

## III. Integration Principles

### P-14: API-First with Stable, Versioned Contracts

**Principle Statement**:
All inter-service and inter-authority interactions MUST occur through versioned, documented, backward-compatible APIs. Contracts are published before implementation.

**Implications**:

- OpenAPI 3.x for synchronous HTTP interfaces; AsyncAPI for event streams
- Breaking changes go through a new major version; prior major version supported for a minimum of 12 months
- API gateways enforce authentication, rate limits, and contract conformance
- Mock servers generated from contracts for MCA client development
- No "just use the admin API for that" shortcuts

**Validation Gates**:

- [ ] API contract published before service implementation begins
- [ ] Contract conformance tested in CI
- [ ] Deprecation schedule documented per major version
- [ ] MCA integration SDK consumes the same contracts, not internal SPIs

---

### P-15: Loose Coupling

**Principle Statement**:
Systems MUST be loosely coupled through published interfaces. Shared databases, file systems, or direct in-process dependencies across system boundaries are prohibited.

**Implications**:

- Services communicate via APIs or events, never via direct database access
- Each service manages its own data lifecycle
- Shared libraries kept minimal (favour duplication over coupling for domain logic)
- No distributed transactions across service or authority boundaries
- Deployment of one service does not require deployment of another

**Validation Gates**:

- [ ] No cross-service direct database access
- [ ] Independent deployment demonstrated
- [ ] Interface changes accompanied by compatibility tests

---

### P-16: Asynchronous for Non-Real-Time Interactions

**Principle Statement**:
Interactions that do not require immediate synchronous response SHOULD use asynchronous messaging to improve resilience and decoupling, with idempotency and at-least-once delivery semantics.

**Typical async candidates** on this programme:

- Outcomes updates from MCAs to DfT
- NISTA pipeline updates
- OSCAR drawdown submissions
- Scheme-status change notifications
- Evaluation-data harvesting

**Typical synchronous candidates**:

- User-facing form submissions requiring immediate validation
- Point-in-time BCR/VfM lookups
- Query-only read paths

**Validation Gates**:

- [ ] Async patterns used for non-real-time flows
- [ ] Message durability and delivery guarantees defined
- [ ] Event schemas versioned
- [ ] Dead-letter queues configured with operational runbooks

---

## IV. Quality Attributes

### P-17: Performance Targets Defined per Service

**Principle Statement**:
Each service MUST have documented performance targets (response-time percentiles, throughput, concurrency) validated by load testing before production deployment.

**Baseline expectations** (services may request higher):

- User-facing reads: p95 < 500 ms, p99 < 1 s
- User-facing writes: p95 < 1 s, p99 < 2 s
- TAG/BCR calculation: p95 < 5 s per scheme
- Outcomes-data bulk export: throughput ≥ 10 MB/s for authenticated downloads

**Validation Gates**:

- [ ] Performance targets documented in service handbook
- [ ] Load testing at 2× expected peak before Public Beta
- [ ] p95 and p99 latency monitored in production with SLO-based alerting

---

### P-18: Availability and Reliability with Explicit SLOs

**Principle Statement**:
Each service MUST declare an availability SLO, an error-budget policy, and operational RTO/RPO targets. SLO burn is a release-blocking signal.

**Typical SLOs** (see P-9 for core platform):

- Tier-1 (core funding operations): 99.9 %
- Tier-2 (internal reporting / analytics): 99.5 %
- Tier-3 (non-critical public-facing read-only feeds): 99 %

**Implications**:

- Redundancy across availability zones (and regions where justified)
- Automated health checks and failover
- Active-passive default; active-active where latency or resilience requires
- Disaster-recovery drill at least annually

---

### P-19: Maintainability and Evolvability

**Principle Statement**:
All components MUST be designed for ongoing change, with clear separation of concerns, modular boundaries, and sufficient documentation that a newly-onboarded engineer can make a safe change within one week.

**Implications**:

- Modular architecture with explicit module boundaries
- Business logic separate from data-access and presentation
- ADRs kept up-to-date per `/arckit:adr`
- Code self-documents via naming; comments explain WHY, not WHAT
- Automated tests give confidence for refactoring

**Validation Gates**:

- [ ] ADR register populated for significant decisions
- [ ] Module boundaries documented
- [ ] Test coverage thresholds met per service
- [ ] Onboarding runbook tested with new joiners

---

## V. Development Practices

### P-20: Infrastructure as Code

**Principle Statement**:
All infrastructure MUST be defined in declarative code, version-controlled, and deployed through automated pipelines. Manual changes to production infrastructure are prohibited.

**Implications**:

- Declarative IaC for all environments (dev, staging, production)
- Infrastructure changes reviewed via pull request before apply
- Environments reproducible from code with minimal manual inputs (signed secrets / keys only)
- Drift detection automated with reconciliation triggers

**Validation Gates**:

- [ ] All environments provisioned via IaC
- [ ] IaC stored in version control
- [ ] Drift-detection job runs at least daily

---

### P-21: Automated Testing Across the Pyramid

**Principle Statement**:
All code changes MUST be validated through automated testing before merge to main. Test types span the pyramid (unit, integration, end-to-end) with security and accessibility checks as standard gates.

**Pyramid Proportions** (indicative):

- Unit tests: 70–80 %
- Integration / contract tests: 15–20 %
- End-to-end tests: 5–10 %

**Required test types**:

- Functional (does it work?)
- Performance (is it fast enough?)
- Security (SAST/DAST/dependency scanning)
- Accessibility (automated a11y in CI)
- Resilience (chaos testing in non-production)

**Validation Gates**:

- [ ] CI pipeline exists and enforces test pass before merge
- [ ] Test coverage thresholds met and trending upward
- [ ] Critical user journeys have end-to-end coverage
- [ ] Security and accessibility checks are release-blocking

---

### P-22: Continuous Integration and Deployment with Quality Gates

**Principle Statement**:
All code changes MUST pass an automated build, test, security-scan, and deployment pipeline with defined quality gates at each stage. Production deployment is automated, repeatable, and reversible within minutes.

**Required stages**:

1. Source control: all changes committed to version control
2. Build: automated compilation and packaging; SBOM generated
3. Test: automated test execution (P-21)
4. Security scan: dependency, container, and code vulnerability scanning
5. Deploy: automated deployment with progressive rollout (canary / blue-green) for higher-tier services

**Quality Gates**:

- [ ] Tests pass
- [ ] No critical or high-severity security vulnerabilities unmitigated
- [ ] Accessibility checks pass
- [ ] Code review approval
- [ ] Production readiness checklist complete (observability, runbooks, SLOs defined)

**Validation Gates**:

- [ ] Pipeline exists end-to-end per service
- [ ] Rollback capability tested (time-to-rollback SLO ≤ 15 minutes for core services)
- [ ] SBOM published per release

---

## VI. Financial Proportionality

### P-23: Platform Spend Proportionate to Grant Throughput

**Principle Statement**:
The platform's operational and delivery spend MUST remain proportionate to the grant throughput it administers. Target ratio: platform cost ≤ 0.05 % of grant throughput over a rolling 3-year window [DFSN-C3].

**Rationale**:
A £15.6bn programme with £3–5.5m platform TCO yields a < 0.04 % ratio — exceptional value for money and a defensible NAO narrative. Any drift above 0.05 % is a signal to pause and re-examine scope, reuse opportunities, or supplier arrangements.

**Implications**:

- SOBC economic case includes the proportionality ratio as a headline figure
- Quarterly cost reporting tracks ratio against target
- Significant scope additions tested against the ratio before commitment
- Use of commercial SaaS with per-user licensing that scales non-linearly with grant throughput is flagged

**Validation Gates**:

- [ ] Ratio reported quarterly against target
- [ ] Scope changes assessed for ratio impact
- [ ] Benchmark against comparable cross-government platforms (MHCLG Funding Service, UKRI TFS) at annual review

---

## VII. Exception Process

### Requesting Architecture Exceptions

Principles 1–23 are mandatory unless a documented, time-bound exception is approved. Non-negotiable principles (P-1, P-2, P-5, P-6, P-9 security aspects, P-12) cannot be waived; compensating controls may be debated, but the principle stands.

**Valid Exception Reasons**:

- Technical constraints that genuinely prevent compliance (rare)
- Regulatory or legal requirements that override the principle
- Transitional state during reuse onboarding or migration
- Pilot or proof-of-concept with defined end date

**Exception Request Requirements**:

- [ ] Business / technical rationale
- [ ] Alternative approach and compensating controls
- [ ] Risk assessment and mitigation plan
- [ ] Expiration date (exceptions are time-bound; default maximum 12 months)
- [ ] Remediation plan to achieve compliance

**Approval Process**:

1. Request submitted to Enterprise Architecture
2. Review by architecture review board
3. For security / data principles: SIRO + CDIO approval required
4. For operational principles: SRO approval required
5. Exception documented as ADR (`ARC-*-ADR-*-v*.md`)
6. Quarterly review of active exceptions; SRO sign-off to extend

---

## VIII. Governance and Compliance

### Architecture Review Gates

All projects MUST pass architecture reviews at key milestones:

**Discovery / Alpha**:

- [ ] Principles understood and documented as applicable to the project
- [ ] High-level approach aligns with principles (reuse search, federation, outcomes-first, open-by-default)
- [ ] No obvious non-negotiable-principle violations

**Beta / Design (HLD / DLD reviews)**:

- [ ] Detailed architecture documented
- [ ] Compliance with each principle validated
- [ ] Exceptions requested and approved before build
- [ ] Security and data principles validated end-to-end

**Pre-Production**:

- [ ] Implementation matches approved architecture
- [ ] All validation gates passed
- [ ] Operational readiness verified (runbooks, SLOs, DR drill)

### Enforcement

- Architecture reviews are mandatory for all projects under this principle set
- Non-negotiable-principle violations must be remediated before production deployment
- Approved exceptions are time-bound and reviewed quarterly
- Retrospective principles-compliance reviews (`/arckit:principles-compliance`) conducted annually per live service

---

## IX. Principle Summary Checklist

| # | Principle | Category | Criticality | Primary Validation |
|---|-----------|----------|-------------|--------------------|
| P-1 | Reuse before build | Strategic | NON-NEGOTIABLE | ADR per new capability |
| P-2 | Federated, not centralised | Strategic | NON-NEGOTIABLE | API-first integration, no forced UI |
| P-3 | Outcomes-first data model | Strategic | HIGH | Data model review |
| P-4 | Open by default | Strategic | HIGH | OGL v3 repo + `data.gov.uk` feed |
| P-5 | Secure by Design | Strategic | NON-NEGOTIABLE | Threat model + GovAssure |
| P-6 | Accessible by default | Strategic | NON-NEGOTIABLE | WCAG 2.2 AA audit |
| P-7 | Observability first-class | Strategic | HIGH | SLOs + runbooks |
| P-8 | Scalability & elasticity | Strategic | HIGH | Load tests |
| P-9 | Resilience & fault tolerance | Strategic | CRITICAL | RTO/RPO + chaos tests |
| P-10 | UK data sovereignty | Data | CRITICAL | Hosting + contracts audit |
| P-11 | Single authoritative source | Data | HIGH | Data lineage |
| P-12 | Lawful multi-controller data | Data | NON-NEGOTIABLE | DPIA + DPA register |
| P-13 | Appraisal integrity | Data | HIGH | TAG Unit ownership + ATRS |
| P-14 | API-first stable contracts | Integration | HIGH | OpenAPI / AsyncAPI + conformance tests |
| P-15 | Loose coupling | Integration | HIGH | No cross-service DB access |
| P-16 | Async for non-real-time | Integration | MEDIUM | Event-schema register |
| P-17 | Performance targets | Quality | HIGH | Load tests + SLO |
| P-18 | Availability SLOs | Quality | CRITICAL | SLO burn reports |
| P-19 | Maintainability | Quality | MEDIUM | ADRs + onboarding runbook |
| P-20 | Infrastructure as Code | DevOps | HIGH | IaC repo + drift detection |
| P-21 | Automated testing | DevOps | HIGH | Coverage + a11y in CI |
| P-22 | CI/CD with quality gates | DevOps | HIGH | Pipeline audit + SBOM |
| P-23 | Spend proportionate to throughput | Financial | HIGH | Quarterly ratio reporting |

---

## X. External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| DFSN | dft-funding-strategy-notes-v1.0.md | Strategy | 000-global/external/ | Discovery-phase strategy brief |
| DTCR | dft-transforming-city-regions-research-v1.0.md | Research | 000-global/external/ | Discovery-phase market and landscape research |
| STKE | ARC-001-STKE-v1.0.md | Stakeholder Analysis | 001-dft-crsts-funding-platform/ | Companion stakeholder drivers analysis for Project 001 |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| DFSN-C1 | DFSN | §2 "8-MCA (now 9-authority) landscape" | Business Requirement | "CRSTS2 extends to nine eligible Mayoral Combined Authorities … GMCA and WMCA already operate under Integrated Settlements from April 2025 … Five more MCAs plus the GLA follow in 2026–27." |
| DFSN-C2 | DFSN | §3 "Build-vs-buy verdict" + §4 Bet 2 | Design Decision | "Don't build. Don't buy. Fork `communitiesuk/funding-service`, extend for transport-specific needs, and contribute reusable parts back upstream." |
| DFSN-C3 | DFSN | §5 "Headline numbers" | Design Decision | "Ratio of platform spend to grant throughput: < 0.04% — strongly favourable to invest." |
| DFSN-C4 | DFSN | §1 "The problem" + §6 | Risk Factor | "The NAO has already flagged the fragmentation cost in bus funding … capacity-to-manage cited as a root cause." |
| DFSN-C5 | DFSN | §4 Bet 3 "Federate, do not centralise" | Design Decision | "The DfT platform must not ask MCAs to replace their existing Dynamics / Salesforce / portfolio tools. Build a federated-identity layer … publish clean OpenAPI contracts … supply reference clients." |
| DFSN-C6 | DFSN | §3 "Build-vs-buy verdict" | Compliance Constraint | "Under TCoP Point 8 (Share, reuse and collaborate) the default answer is reuse. The burden of proof falls on any option that re-implements what MHCLG has already built and open-sourced." |
| DFSN-C7 | DFSN | §2 "landscape" | Stakeholder Need | "TfGM runs Microsoft Dynamics 365 CE + Power Platform, TfWM has a GOV.UK-aligned design system and Power BI dashboards … Each MCA has its own identity provider, its own finance ledger, and its own reporting cadence." |
| DFSN-C8 | DFSN | §4 Bet 1 "Treat DfT as a steward" | Design Decision | "The Integrated Settlement trajectory means DfT's role is shifting from 'approver of each scheme' to 'steward of outcomes'. Build the platform around that." |
| DFSN-C9 | DFSN | §4 Bet 6 "Open-source" | Design Decision | "Publishing under OGL v3 costs almost nothing extra and sets DfT up as a 'shared service' producer rather than consumer." |
| DFSN-C10 | DFSN | §3 + §4 Bet 3 | Compliance Constraint | "The platform must federate with [MCA stacks]" — implying UK hosting and federated-identity residency constraints across all authorities. |
| DFSN-C11 | DFSN | §4 Bet 4 "TAG-BCR microservice" | Design Decision | "A microservice that consumes the DfT TAG Data Book (updated twice yearly, November and May), takes scheme inputs, runs BCR and VfM categorisation, and surfaces results via API … Make this the DfT flagship reusable component." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| dft-transforming-city-regions-research-v1.0.md | 000-global/external/ | Main research document reviewed. Content drives downstream artifacts (`/arckit:research`, `/arckit:sobc`, `/arckit:wardley`) rather than principles directly; strategy-notes distillation is the principle-level source. |
| vendors/*.md (6 profiles) | 000-global/external/vendors/ | Vendor-specific; relevant to procurement and evaluation rather than principles. |
| tech-notes/*.md (3 notes) | 000-global/external/tech-notes/ | Technology-specific; relevant to research and HLD rather than principles. |

---

**Generated by**: ArcKit `/arckit:principles` command
**Generated on**: 2026-04-20
**ArcKit Version**: 4.8.0
**Project**: Global principles (sponsoring project: Project 001 — DfT CRSTS Funding Platform)
**AI Model**: Claude Opus 4.7 (1M context)
