# Project Requirements: DfT CRSTS Funding Platform

> **Template Origin**: Official | **ArcKit Version**: 4.8.0 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
| **Project** | DfT CRSTS Funding Platform (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-04-20 |
| **Last Modified** | 2026-04-20 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-05-20 |
| **Owner** | Mark Craddock (Enterprise Architect, prospective) |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Project Team, Architecture Team, SRO's office, MHCLG Digital liaison, MCA architect working group |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-04-20 | ArcKit AI (Claude Opus 4.7) | Initial creation from `/arckit:requirements` command, traced to STKE SD/G/O and PRIN | PENDING | PENDING |

## Document Purpose

Defines the business, functional, non-functional, data, and integration requirements for the DfT CRSTS Funding Platform. Used to:

- Guide HLD/DLD, architecture reviews, and SOC/OBC/FBC business-case submissions
- Inform procurement decisions (`/arckit:research`, `/arckit:sow`, `/arckit:evaluate`)
- Anchor the test strategy and GDS Service Assessment evidence
- Trace stakeholder drivers (`ARC-001-STKE-v1.0`) and architecture principles (`ARC-000-PRIN-v1.0`) through to deliverable features

---

## Executive Summary

### Business Context

DfT administers a family of city-region transport funding programmes totalling **£15.6bn across 9 Mayoral Combined Authorities over 2027–2032** (SR25 CRSTS2 + Transforming City Regions) [DFSN-C1]. CRSTS1 runs concurrently to 2026–27. Two MCAs (GMCA, WMCA) already operate under the **Integrated Settlement** from April 2025; five more plus the GLA follow in April 2026. Administration is currently fragmented across DfT and 9 MCA assurance teams with no shared platform, a pattern the NAO has already flagged in its BSIP critique [DFSN-C2].

A shared funding-administration platform is needed that **federates** with existing MCA stacks, integrates with **NISTA** pipeline assurance (live since 1 April 2025) and HMT **OSCAR/Clear Line of Sight** drawdown, and — crucially — **reuses the MHCLG Funding Service** (OGL v3, live December 2025) rather than rebuilding from scratch [DFSN-C3]. The platform must serve DfT as outcomes-steward (not scheme approver) for the Integrated Settlement, while continuing to support scheme-level workflows for non-Integrated-Settlement MCAs.

### Objectives

- Reduce the administrative overhead of CRSTS/TCR across the DfT↔MCA federation by consolidating intake, assurance, claims, drawdown and outcomes reporting onto a shared, OGL v3 substrate
- Expose a consolidated, machine-readable pipeline view to HMT, NISTA and NAO that answers the BSIP-fragmentation critique
- Deliver a TAG-compliant BCR/VfM microservice, owned by the DfT TAG Unit, published under OGL v3, and reusable by DLUHC / DESNZ / NHS England
- Federate — never centralise — across 9 MCAs while meeting UK GDPR multi-controller obligations
- Deliver within a 3-year platform TCO of **£3.0m–£5.5m** — < 0.04 % of grant throughput [DFSN-C4]

### Expected Outcomes

- **O-1**: ≥ 90 % of CRSTS2/TCR scheme throughput visible in a single pipeline view by end of Year 2 post-Public-Beta
- **O-2**: TAG/BCR microservice scoring 100 % of CRSTS2 schemes; at least one other department in active evaluation by March 2028
- **O-3**: Integrated Settlement outcomes published machine-readably on `data.gov.uk` with quarterly refresh and stable URIs
- **O-4**: 3-year platform TCO ≤ £5.5m (< 0.04 % of grant throughput)
- **O-5**: Zero notifiable personal-data breaches; DPIA not challenged by ICO

### Project Scope

**In Scope**:

- Scheme and programme intake for CRSTS1 (mid-life), CRSTS2 and TCR (from 2027) across all 9 MCAs and the GLA as observer
- Integrated Settlement outcomes/indicators modelling and reporting
- Green Book 5-case assurance workflow (SOC/OBC/FBC progression) including DfT DP1–DP7 decision gates
- TAG-compliant BCR/VfM microservice (DfT-owned, OGL v3)
- Claim capture, drawdown scheduling, and OSCAR / Clear Line of Sight reporting integration
- MCA federation (OpenAPI + AsyncAPI + reference SDK)
- Pipeline-update feed to NISTA
- Public outcomes publication to `data.gov.uk`
- Evaluation data capture for post-completion benefits realisation
- GOV.UK One Login integration (mandatory by end 2027)
- GOV.UK Notify, Pay, Forms, Design System adoption
- Spotlight + GGIS integration for due-diligence and cross-gov register

**Out of Scope**:

- Direct replacement of MCA Dynamics 365, Salesforce, or portfolio tooling — federation only
- Non-CRSTS / non-TCR transport funding streams (Active Travel Fund, HS2 scheme funding, Network Rail capital) — may be in scope for v2
- Internal DfT programme assurance for non-transport capital (handled by GMPP tooling)
- Grant recipient payment mechanics below the MCA level (scheme contractor payments are out of scope)
- Public-facing citizen service design (the citizens who use the transport outcomes are not users of this platform)

---

## Stakeholders

(See `ARC-001-STKE-v1.0.md` for full stakeholder analysis — summary reproduced here.)

| Stakeholder | Role | Organisation | Involvement Level |
|-------------|------|--------------|-------------------|
| SRO (to be appointed) | Senior Responsible Owner | DfT Rail, Places & Local Transport DG | Decision maker (accountable) |
| DG Rail, Places & Local Transport | Executive Sponsor | DfT | Accountable |
| DfT CDIO | Digital spend controls, technology assurance | DfT | Decision maker (technology) |
| DfT Chief Analyst / TAG Unit | TAG appraisal owner | DfT | Requirements definition (appraisal) |
| DfT Assurance Hub | DP1–DP7 assurance operations | DfT | Requirements definition (assurance) |
| Product Manager | End-to-end product | DfT | Requirements definition |
| Service Owner | End-to-end service | DfT | Requirements definition |
| Enterprise Architect | Architecture lead | DfT | Technical oversight |
| MHCLG Funding Service team | Strategic reuse partner | MHCLG | Technical partnership |
| HMT Transport team | Spend control | HMT | Decision maker (spend) |
| NISTA | Pipeline assurance | Cabinet Office / HMT | Consulted |
| Cabinet Office Grants Function | Minimum grant requirements | Cabinet Office | Consulted |
| CDDO | Digital spend control | Cabinet Office | Decision maker (spend) |
| GMCA, WMCA (Tier-1 IS) | Partner authorities | GMCA, WMCA | Requirements definition |
| WYCA, LCRCA, SYMCA, NECA, GLA (Tier-2 IS) | Partner authorities | Respective MCAs | Requirements definition |
| TVCA, WECA, EMCCA (Tier-3) | Partner authorities | Respective MCAs | Requirements definition |
| DfT SIRO | Information risk owner | DfT | Decision maker (information risk) |
| DfT SSRO / DSO | Security risk | DfT | Consulted |
| ICO | Data protection regulator | ICO | Consulted (novel processing) |
| NAO / PAC | External audit / scrutiny | External | Informed |
| Transport campaign groups | Public-interest scrutiny | Third-sector | Informed (open data) |

---

## Business Requirements

### BR-1: Consolidated CRSTS/TCR pipeline view across all 9 MCAs

**Description**: Provide a single authoritative view of every CRSTS2 / TCR scheme, outcome, indicator, milestone, claim, and drawdown across DfT and the 9 MCAs.

**Rationale**: Addresses NAO BSIP fragmentation critique [DFSN-C2]; satisfies HMT (SD-2), NISTA (SD-3) and NAO (SD-9). Traces to STKE outcome O-1. Grounded in PRIN P-3 (Outcomes-first data model) and P-11 (Single authoritative source).

**Success Criteria**:

- ≥ 90 % of CRSTS2/TCR scheme throughput visible in a single pipeline view by end of Year 2 post-Public Beta
- HMT, NISTA, NAO and DfT SRO can each query the same ledger at any time and return consistent results
- Queries are answerable without spreadsheets or ad-hoc MCA data requests

**Priority**: MUST_HAVE
**Stakeholder**: SRO, HMT, NISTA, NAO
**Traces to**: STKE SD-1, SD-2, SD-3, SD-9; Goals G-1, G-3; Outcome O-1

---

### BR-2: Reuse MHCLG Funding Service as case-management substrate

**Description**: The platform's case-management and form-builder foundation MUST be the MHCLG Funding Service (forked + contributed upstream) unless SRO-signed exception exists.

**Rationale**: TCoP Point 8 obligation [DFSN-C3]; CDDO spend-control default; cross-government reuse narrative; MHCLG Digital strategic partnership. Traces to PRIN P-1 (Reuse before build).

**Success Criteria**:

- Joint Engineering Governance agreement with MHCLG Digital signed before SOC submission
- MHCLG Funding Service deployed as substrate by Alpha
- Upstream contributions tracked (target ≥ 3 substantive PRs accepted by end of Year 1)
- Any alternative substrate selected only via SRO-signed exception ADR

**Priority**: MUST_HAVE
**Stakeholder**: SRO, MHCLG Digital, CDDO
**Traces to**: STKE SD-1, SD-4, SD-11; Goal G-5

---

### BR-3: TAG-compliant BCR/VfM microservice published under OGL v3

**Description**: Deliver a microservice consuming the published DfT TAG Data Book, computing Benefit-Cost Ratio and VfM categorisation, exposing results via OpenAPI, owned by the DfT TAG Unit, published under OGL v3.

**Rationale**: The genuinely differentiated capability DfT must build [DFSN-C5]; protects appraisal integrity (PRIN P-13); becomes cross-gov reusable asset (PRIN P-4).

**Success Criteria**:

- Microservice scores 100 % of CRSTS2 schemes by April 2027
- TAG Data Book version surfaced in every API response and persisted with every stored calculation
- Source repository public under OGL v3 before first non-dev deployment
- ≥ 1 non-DfT department in active evaluation by March 2028

**Priority**: MUST_HAVE
**Stakeholder**: DfT Chief Analyst / TAG Unit, HMT, NISTA
**Traces to**: STKE SD-2, SD-3, SD-7; Goal G-2; Outcome O-2

---

### BR-4: Federated MCA participation without forced stack replacement

**Description**: Nine MCAs (and GLA observer) participate via API and event contracts without being required to replace their existing Dynamics 365, Salesforce or portfolio tooling.

**Rationale**: Protects Mayoral Integrated Settlement autonomy [DFSN-C6]; avoids political regression. PRIN P-2 (non-negotiable).

**Success Criteria**:

- ≥ 5 MCAs on platform by April 2027 (Tier-2 Integrated Settlement start)
- At least 1 Tier-1 MCA (GMCA or WMCA) participates via API-only integration as a reference
- Zero MCA stack-replacement mandates
- Reference client SDK released before Private Beta

**Priority**: MUST_HAVE
**Stakeholder**: All 9 MCAs + GLA, SRO
**Traces to**: STKE SD-5, SD-6; Goals G-1, G-4; Outcome O-1

---

### BR-5: Outcomes-led data model aligned to Integrated Settlement trajectory

**Description**: The canonical data model treats outcomes and indicators as first-class entities. Scheme-level detail is optional for Tier-1 MCAs on the Integrated Settlement.

**Rationale**: Integrated Settlement policy trajectory [DFSN-C6]; future-proofs the model as 7+ MCAs join by April 2026 and onwards. PRIN P-3.

**Success Criteria**:

- Outcome / indicator entities present in logical data model before Alpha
- Tier-1 MCAs can publish outcomes without providing scheme-level data
- Tier-3 MCAs retain scheme-level workflow
- Schema published to `data.gov.uk` with stable URIs before Public Beta

**Priority**: MUST_HAVE
**Stakeholder**: HMT, NISTA, GMCA, WMCA, campaign groups
**Traces to**: STKE SD-2, SD-3, SD-5, SD-10; Goals G-1, G-3; Outcome O-3

---

### BR-6: Platform TCO contained within £3.0m–£5.5m (3-year) and proportional to grant throughput

**Description**: Deliver the platform within a 3-year TCO of £3.0m–£5.5m, representing < 0.04 % of the underlying £15.6bn grant throughput.

**Rationale**: Defensible VfM narrative to HMT / NAO [DFSN-C4]; PRIN P-23 (Financial proportionality).

**Success Criteria**:

- Quarterly cost tracking against target
- SOBC Economic Case includes proportionality ratio as a headline figure
- Scope additions are ratio-tested before commitment
- Audited actual TCO ≤ £5.5m at Year 3

**Priority**: MUST_HAVE
**Stakeholder**: SRO, HMT, DfT CDIO, NAO
**Traces to**: STKE SD-1, SD-2; Goal G-1; Outcome O-4

---

### BR-7: Service Standard and TCoP compliance across all service-assessment gates

**Description**: Pass GDS Service Assessments at Alpha and Beta; TCoP self-assessment returns Green across all 12 points at each CDDO spend-control submission.

**Rationale**: Mandatory for spend-control progression; anchors NAO-defensibility narrative (SD-9).

**Success Criteria**:

- Pass Alpha Service Assessment
- Pass Beta Service Assessment
- TCoP Green at SOC, OBC, FBC gates

**Priority**: MUST_HAVE
**Stakeholder**: CDDO, GDS, SRO
**Traces to**: STKE SD-11, SD-1; Goal G-7

---

### BR-8: Lawful multi-controller data handling across the federation

**Description**: All processing activities have documented UK-GDPR lawful basis; controller/processor/joint-controller roles explicitly mapped; Article 28 DPAs executed with every MCA and material sub-processor before personal data flows.

**Rationale**: Highest compliance risk on this programme [STKE SD-8]; PRIN P-12 (non-negotiable).

**Success Criteria**:

- DPIA approved before Private Beta (`ARC-001-DPIA-v1.0`)
- DPA register complete
- Subject-rights fulfilment tested
- ICO prior consultation where processing novel
- Zero notifiable personal-data breaches through first 24 months Live

**Priority**: MUST_HAVE
**Stakeholder**: DfT SIRO, MCA DPOs, ICO
**Traces to**: STKE SD-8; Goal G-6; Outcome O-5

---

## Functional Requirements

### User Personas

#### Persona 1: DfT Assurance Officer (Priya, Grade 7)

- **Role**: Programme assurance officer within the DfT Assurance Hub
- **Goals**: Run DP1–DP7 assurance gates efficiently; consolidate MCA submissions; produce ministerial-briefing packs on demand
- **Pain Points**: Scheme data arrives in 9 different formats; chasing MCAs for updates; no single pipeline view
- **Technical Proficiency**: Medium — confident with Power BI and Excel; new to APIs

#### Persona 2: MCA Portfolio Director (Daniel, WMCA)

- **Role**: Directs the CRSTS portfolio within a Tier-1 Integrated Settlement MCA
- **Goals**: Publish outcomes on time; avoid re-entering data into DfT systems; protect MCA-side tooling investment (Dynamics 365)
- **Pain Points**: Reporting duplication; DfT-specific formats not matching MCA systems
- **Technical Proficiency**: Medium — managed IT service; reliant on digital team for deep integration

#### Persona 3: MCA Scheme Officer (Aisha, EMCCA)

- **Role**: Day-to-day officer submitting schemes and claims in a Tier-3 MCA with less engineering capacity
- **Goals**: Submit a scheme with reasonable effort; know what DfT needs; get a quick decision
- **Pain Points**: Lack of capacity for bespoke integration; unfamiliarity with Green Book
- **Technical Proficiency**: Low–medium — spreadsheet-literate; uses forms and document portals

#### Persona 4: DfT TAG Analyst (Chen)

- **Role**: Analyst within the DfT TAG Unit producing and maintaining TAG guidance
- **Goals**: Ensure TAG Data Book versions are applied consistently; audit BCR calculations; publish TAG updates every May and November
- **Pain Points**: TAG applied inconsistently across MCA spreadsheets; no audit trail per run
- **Technical Proficiency**: High — quantitative analyst, R/Python-literate, API-ready

#### Persona 5: HMT Transport Desk Officer (Laila)

- **Role**: HMT spending-team officer responsible for DfT Transport business cases and drawdown profile
- **Goals**: Approve drawdowns against profile; see BCR evidence; respond to Chief Secretary briefings
- **Pain Points**: Drawdown data arrives late; BCRs produced inconsistently; OSCAR reconciliation manual
- **Technical Proficiency**: Medium — HMT Power BI dashboards; OSCAR user

#### Persona 6: NISTA Pipeline Analyst (Marco)

- **Role**: Analyst in NISTA tracking the 780-project / £530bn pipeline
- **Goals**: Receive structured pipeline-update feeds from DfT; flag pipeline risks for the NISTA board
- **Pain Points**: Schemas still emerging; inconsistent formats from departments; manual ingestion
- **Technical Proficiency**: Medium–high — data analyst

#### Persona 7: Public / campaigner (Ruth, Campaign for Better Transport)

- **Role**: External scrutineer of transport funding outcomes
- **Goals**: Access machine-readable outcomes data; compare across MCAs; cite in research
- **Pain Points**: Data in redacted PDFs; inconsistent indicator definitions
- **Technical Proficiency**: Medium — uses `data.gov.uk`, Python pandas

---

### Use Cases

#### UC-1: Submit a new CRSTS2 scheme for assurance

**Actor**: MCA Scheme Officer (Aisha)
**Preconditions**: User authenticated via GOV.UK One Login; authority already onboarded under MoC; scheme meets Integrated Settlement outcomes framework; access to Scheme Officer role for the authority.

**Main Flow**:

1. User selects "Create Scheme" from the authority home page
2. System presents a scheme form pre-populated with the Integrated Settlement outcomes framework for the authority
3. User enters scheme metadata (name, type, outcomes linked, indicators, estimated cost, start/end dates)
4. User attaches Green Book 5-case supporting documents (SOC/OBC/FBC uploads)
5. System invokes TAG-BCR microservice with scheme inputs
6. Microservice returns BCR, VfM category, and TAG Data Book version used
7. User reviews generated assurance pack and submits for DfT assurance
8. System records submission, assigns an assurance officer, notifies via GOV.UK Notify
9. System publishes scheme-created event on AsyncAPI channel for consuming MCAs and NISTA

**Postconditions**: Scheme in "Awaiting Assurance" state; BCR computed and stored; assurance officer assigned.

**Alternative Flows**:

- **Alt 1a**: Tier-1 MCA on Integrated Settlement may skip scheme-level creation and push only outcome updates via API

**Exception Flows**:

- **Ex 1**: TAG microservice unavailable — system saves draft; queues BCR computation for retry with exponential backoff (PRIN P-9)
- **Ex 2**: GOV.UK One Login session expired — re-authentication prompt

**Business Rules**:

- BCR must be computed using the current TAG Data Book version unless explicit waiver granted
- Schemes under the Integrated Settlement outcomes framework cannot be submitted if they do not link to at least one indicator
- Scheme cost cannot exceed the authority's remaining CRSTS2 envelope

**Priority**: CRITICAL

---

#### UC-2: Publish outcome update from Tier-1 MCA via API

**Actor**: MCA system (GMCA, WMCA) — unattended API call
**Preconditions**: Mutual-TLS handshake successful; service credential valid; authority onboarded for API-only integration.

**Main Flow**:

1. MCA system POSTs outcome update to the platform's outcomes endpoint per the published OpenAPI contract
2. Platform validates the payload against the JSON Schema
3. Platform stores the outcome update, correlating with indicators and the authority
4. Platform publishes an event to the outcomes AsyncAPI channel for consuming services (reporting, NISTA adapter)
5. Platform returns 201 Created with canonical representation

**Postconditions**: Outcome update stored; downstream services notified.

**Exception Flows**:

- **Ex 1**: Payload fails validation — 400 Bad Request with machine-readable error list
- **Ex 2**: Authentication failure — 401; event logged to security audit
- **Ex 3**: Conflicting concurrent update — 409 Conflict with ETag-based retry guidance

**Business Rules**:

- Outcome updates must be idempotent (retry-safe)
- Indicator values outside the published measurement range are flagged but accepted (with a warning) to preserve authority autonomy

**Priority**: CRITICAL

---

#### UC-3: Review DP1–DP7 assurance gate and record decision

**Actor**: DfT Assurance Officer (Priya)
**Preconditions**: Scheme submitted; assurance officer assigned; BCR computed.

**Main Flow**:

1. Officer opens scheme assurance view
2. Officer reviews the 5-case supporting pack, BCR output and TAG Data Book version
3. Officer selects the DP-N gate (DP1 through DP7) to record decision
4. Officer enters decision (Proceed / Proceed with conditions / Do not proceed) with free-text justification
5. System records the decision as an immutable audit entry (who, what, when, why, with signed record)
6. System notifies the submitting authority via GOV.UK Notify

**Postconditions**: Decision recorded; audit trail signed; authority notified.

**Business Rules**:

- Decisions signed with the officer's GOV.UK One Login identity
- "Proceed with conditions" requires at least one condition text and a condition target date
- Decisions can be amended with a new record; previous records are not deleted (append-only audit)

**Priority**: HIGH

---

#### UC-4: Publish outcomes dataset to `data.gov.uk`

**Actor**: Platform (scheduled) + Service Owner (manual override)
**Preconditions**: Publishing pipeline configured; `data.gov.uk` credentials provisioned; quarterly publication window reached.

**Main Flow**:

1. Scheduler triggers publication job quarterly (1 April, 1 July, 1 October, 1 January at 09:00 UTC)
2. Job extracts published outcomes and indicators filtered to OFFICIAL (public) data classification
3. Job validates dataset against published JSON Schema
4. Job publishes dataset to `data.gov.uk` with stable URI per indicator and per outcome
5. Job generates checksum and writes publication record
6. Job posts announcement to DfT statistics Twitter/X and internal newsletter (via Notify)

**Postconditions**: Dataset public; URI stable for citation; publication record stored.

**Exception Flows**:

- **Ex 1**: Schema validation fails — job halts; Service Owner notified; no partial publication
- **Ex 2**: `data.gov.uk` API failure — retry with exponential backoff for up to 24 hours before escalation

**Business Rules**:

- Only OFFICIAL-classified outcome/indicator data published
- URIs are stable across quarters (the same indicator receives the same URI in every release)
- Breaking schema changes require deprecation period (≥ 2 release cycles)

**Priority**: HIGH

---

#### UC-5: Schedule and report a quarterly drawdown to HMT OSCAR

**Actor**: DfT Finance Officer (supervisor)
**Preconditions**: Claims approved for the quarter; OSCAR integration active.

**Main Flow**:

1. Finance officer opens the drawdown scheduling view for the quarter
2. System presents all approved claims with drawdown timing
3. Officer reviews, adjusts profile if needed, and approves the scheduled drawdown
4. System transmits drawdown profile to OSCAR via the approved integration channel
5. OSCAR returns confirmation; system records confirmation ID

**Postconditions**: Drawdown profile submitted to OSCAR; confirmation stored.

**Business Rules**:

- Drawdown cannot exceed the authority's approved profile
- All drawdowns must be traceable to approved claims

**Priority**: HIGH

---

### Functional Requirements Detail

#### FR-1: Scheme intake and lifecycle management

**Description**: The platform must allow authorised MCA users to create, amend, submit, withdraw, and close CRSTS / TCR schemes through a web UI and equivalent API.

**Relates To**: BR-1, BR-4, UC-1

**Acceptance Criteria**:

- [ ] Given an authorised Scheme Officer, when they create a scheme, then the system stores scheme metadata including linked outcomes and indicators
- [ ] Given a scheme in Draft, when the officer saves, then the system persists without BCR computation
- [ ] Given a scheme with linked indicators, when submitted for assurance, then the system invokes the TAG-BCR microservice and stores the BCR result with Data Book version
- [ ] Edge case: Scheme exceeding remaining authority envelope is rejected with clear error message
- [ ] Edge case: Scheme without any linked indicator is rejected with validation error (Integrated Settlement alignment)

**Data Requirements**:

- Inputs: scheme metadata, linked indicator IDs, cost profile, start/end dates, supporting documents
- Outputs: scheme record with unique ID, BCR result, Data Book version
- Validations: referential integrity with authority, outcomes, and indicators; cost within envelope

**Priority**: MUST_HAVE
**Complexity**: HIGH
**Dependencies**: FR-4 (outcomes model), FR-9 (TAG-BCR microservice)
**Assumptions**: MCA onboarding is complete with role assignments

---

#### FR-2: API-first federation for all MCA integrations

**Description**: The platform must expose OpenAPI and AsyncAPI contracts for every integration surface (schemes, outcomes, indicators, claims, drawdowns, notifications, audit exports), versioned with backward compatibility.

**Relates To**: BR-4, PRIN P-2, PRIN P-14

**Acceptance Criteria**:

- [ ] OpenAPI 3.x and AsyncAPI 2.x contracts published in the repository and on the developer portal
- [ ] Contract conformance tests run in CI; builds fail on drift
- [ ] Breaking changes create a new major version; prior major version supported ≥ 12 months
- [ ] Mock servers generated from contracts and exposed to MCAs for client-side development
- [ ] At least one Tier-1 MCA integrates via API-only route as a reference

**Priority**: MUST_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-1, FR-4, FR-5, FR-6, FR-10

---

#### FR-3: Reference client SDK for MCAs

**Description**: The platform must provide a reference SDK (in at least Python and TypeScript) that wraps the federation API, handles authentication, pagination, retries, and idempotency, and is published under OGL v3.

**Relates To**: BR-4, PRIN P-2, PRIN P-4

**Acceptance Criteria**:

- [ ] SDK package published under OGL v3
- [ ] SDK provides authenticated client for every federation endpoint
- [ ] SDK handles idempotency keys and retry-with-backoff
- [ ] End-to-end integration example tested in CI
- [ ] Released before Private Beta

**Priority**: SHOULD_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-2

---

#### FR-4: Outcomes and indicators modelling

**Description**: The platform must represent Integrated Settlement outcomes and indicators as first-class versioned entities with measurement definitions, accepted value ranges, and stable URIs.

**Relates To**: BR-5, PRIN P-3

**Acceptance Criteria**:

- [ ] Outcome entity supports description, category, target value, measurement frequency, measurement method, and linked indicators
- [ ] Indicator entity supports units, value ranges, accepted methods, and stable URI
- [ ] Outcomes/indicators versioned with deprecation lifecycle
- [ ] Schema published to `data.gov.uk` with stable URIs

**Priority**: MUST_HAVE
**Complexity**: HIGH
**Dependencies**: FR-2, FR-12

---

#### FR-5: Claim capture and evidence management

**Description**: Authorised users can submit claims against approved schemes, attach supporting evidence, and track claim status through the approval lifecycle.

**Relates To**: BR-1, BR-4

**Acceptance Criteria**:

- [ ] Claim links to scheme, cost line items, and supporting evidence
- [ ] Claim supports amend, withdraw, resubmit lifecycle
- [ ] Approval workflow is configurable per authority tier (Tier-1 lighter, Tier-3 full)
- [ ] Audit trail append-only

**Priority**: MUST_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-1, FR-7

---

#### FR-6: Drawdown scheduling and OSCAR integration

**Description**: The platform must support quarterly drawdown scheduling against approved claims and submit drawdown profiles to HMT OSCAR via the approved integration.

**Relates To**: BR-1, UC-5

**Acceptance Criteria**:

- [ ] Drawdown schedule aggregates approved claims per quarter per authority
- [ ] Submission to OSCAR returns confirmation ID
- [ ] Reconciliation report produced quarterly
- [ ] Drawdowns traceable end-to-end to scheme and outcome

**Priority**: MUST_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-5, INT-3

---

#### FR-7: DP1–DP7 assurance gate workflow

**Description**: The platform must support the DfT DP1–DP7 decision-gate workflow for CRSTS2 schemes, with append-only decision records, condition tracking, and escalation.

**Relates To**: BR-1, UC-3

**Acceptance Criteria**:

- [ ] Each DP gate records decision (Proceed / Proceed with conditions / Do not proceed), justification, decision-maker identity, signed timestamp
- [ ] Conditions are tracked with target resolution dates and evidence of resolution
- [ ] History is append-only (corrections add new records without deleting prior ones)
- [ ] Escalation to SRO supported for "Do not proceed" decisions

**Priority**: MUST_HAVE
**Complexity**: HIGH
**Dependencies**: FR-1

---

#### FR-8: Integrated-Settlement outcomes reporting

**Description**: The platform must aggregate outcomes across authorities and produce reporting views for DfT, HMT, NISTA, and external publication.

**Relates To**: BR-1, BR-5, UC-4

**Acceptance Criteria**:

- [ ] Outcomes aggregated per authority, nationally, and per theme
- [ ] Reports generated on demand and quarterly
- [ ] Data published to `data.gov.uk` under UC-4

**Priority**: MUST_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-4, INT-7

---

#### FR-9: TAG-BCR microservice

**Description**: A microservice consuming the DfT TAG Data Book, computing BCR and VfM categorisation per scheme, and exposing results via OpenAPI. Source code owned by the DfT TAG Unit.

**Relates To**: BR-3, UC-1, PRIN P-13

**Acceptance Criteria**:

- [ ] Service consumes the current TAG Data Book version (May and November releases)
- [ ] BCR and VfM category computed for submitted scheme inputs
- [ ] Every API response includes the Data Book version used
- [ ] Every computation is persisted with inputs, outputs, and Data Book version for audit
- [ ] Repository public under OGL v3 before first non-dev deployment
- [ ] At least one TAG Unit embedded engineer or named code reviewer in commit history

**Priority**: MUST_HAVE
**Complexity**: HIGH
**Dependencies**: DR-8 (TAG Data Book records)

---

#### FR-10: NISTA pipeline-update feed

**Description**: The platform must publish a pipeline-update feed consumable by NISTA, per the NISTA ingest schema.

**Relates To**: BR-1, INT-2

**Acceptance Criteria**:

- [ ] Event stream or REST endpoint publishes scheme lifecycle events
- [ ] NISTA schema compatibility tested in CI
- [ ] Schema version negotiated and versioned

**Priority**: MUST_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-2

---

#### FR-11: Public open-data publication

**Description**: Quarterly publication of outcomes datasets to `data.gov.uk` with stable URIs per indicator.

**Relates To**: BR-5, UC-4

**Acceptance Criteria**:

- [ ] Publication pipeline scheduled quarterly
- [ ] Stable URIs per indicator maintained across releases
- [ ] Breaking changes deprecated over ≥ 2 release cycles

**Priority**: MUST_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-4

---

#### FR-12: Audit trail and signed decision records

**Description**: The platform must maintain a tamper-evident append-only audit trail for all decisions (assurance gates, claim approvals, drawdown approvals, configuration changes).

**Relates To**: BR-1, BR-8, PRIN P-5

**Acceptance Criteria**:

- [ ] Every decision record includes who, what, when, where, why, and result
- [ ] Audit records cryptographically signed and chained (hash linking)
- [ ] Audit retention ≥ 7 years
- [ ] NAO-friendly export format available

**Priority**: MUST_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-7, FR-5, FR-6

---

#### FR-13: Configuration, reference data and authority management

**Description**: Admin capability to manage authorities, indicator definitions, user roles, and reference data (e.g. TAG Data Book version register) with change-management workflow.

**Relates To**: BR-4, PRIN P-11

**Acceptance Criteria**:

- [ ] Authority records maintained with tier (Integrated Settlement tier, CRSTS envelope)
- [ ] Indicator-definition changes versioned and approved before becoming authoritative
- [ ] Role assignments auditable

**Priority**: SHOULD_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-4

---

#### FR-14: Notifications via GOV.UK Notify

**Description**: All transactional email and SMS notifications sent via GOV.UK Notify with templated, accessible content.

**Relates To**: PRIN P-1 (reuse), PRIN P-6 (accessibility)

**Acceptance Criteria**:

- [ ] All notifications templated in GOV.UK Notify
- [ ] User notification preferences respected
- [ ] Delivery receipts tracked
- [ ] No bespoke email infrastructure

**Priority**: MUST_HAVE
**Complexity**: LOW
**Dependencies**: INT-5

---

#### FR-15: Identity and access via GOV.UK One Login

**Description**: Human user authentication via GOV.UK One Login; service-to-service authentication via mutual TLS with signed tokens.

**Relates To**: BR-7, PRIN P-5, NFR-SEC-1

**Acceptance Criteria**:

- [ ] GOV.UK One Login integration before Public Beta (mandatory by end-2027)
- [ ] Service accounts managed via a hardened secret store
- [ ] RBAC enforced per authority and per role

**Priority**: MUST_HAVE
**Complexity**: MEDIUM
**Dependencies**: INT-4

---

#### FR-16: Cabinet Office Grants Function integration (Spotlight + GGIS)

**Description**: Due-diligence checks performed via Spotlight; grant records registered with the Government Grants Information System (GGIS).

**Relates To**: BR-1, BR-8

**Acceptance Criteria**:

- [ ] Spotlight due-diligence API called at scheme-creation gate
- [ ] GGIS records written per scheme and per award
- [ ] Failures in either do not block progression (degraded mode with notification)

**Priority**: SHOULD_HAVE
**Complexity**: MEDIUM
**Dependencies**: INT-8

---

#### FR-17: Geospatial visualisation of schemes and outcomes

**Description**: Map-based visualisation of scheme locations and outcome measurements using OS MasterMap under the Public Sector Geospatial Agreement.

**Relates To**: BR-1

**Acceptance Criteria**:

- [ ] Schemes can carry optional geospatial extent (GeoJSON)
- [ ] Map view displays schemes and outcomes aggregated by authority
- [ ] Accessible alternative representation for non-visual users (PRIN P-6)

**Priority**: COULD_HAVE
**Complexity**: MEDIUM
**Dependencies**: INT-6

---

#### FR-18: Evaluation-data capture for post-completion benefits realisation

**Description**: Post-completion benefit-realisation data can be captured per scheme and aggregated per authority for input into DfT Monitoring and Evaluation.

**Relates To**: BR-1, BR-5

**Acceptance Criteria**:

- [ ] Evaluation record linked to scheme and outcomes
- [ ] Supports quantitative indicators and qualitative narrative
- [ ] Export to DfT analysts

**Priority**: SHOULD_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-4

---

#### FR-19: Dashboards and reporting for DfT, HMT, NISTA

**Description**: Role-appropriate dashboards for the SRO, HMT desk officer, and NISTA analyst, displaying pipeline status, drawdown vs profile, and outcome progression.

**Relates To**: BR-1

**Acceptance Criteria**:

- [ ] Role-based dashboard views
- [ ] Data refreshed within 15 minutes of underlying change
- [ ] Export to CSV / JSON for offline analysis

**Priority**: SHOULD_HAVE
**Complexity**: MEDIUM
**Dependencies**: FR-8, FR-12

---

#### FR-20: Scheme archival and succession

**Description**: Completed schemes can be archived with evaluation data preserved; succession relationships tracked between schemes (e.g. CRSTS1 scheme continued under CRSTS2).

**Relates To**: BR-1, BR-5

**Acceptance Criteria**:

- [ ] Archived schemes remain queryable
- [ ] Succession relationship preserved
- [ ] Archived scheme data retained per retention policy

**Priority**: COULD_HAVE
**Complexity**: LOW
**Dependencies**: FR-1

---

## Non-Functional Requirements (NFRs)

### Performance Requirements

#### NFR-P-1: Response time

**Requirement**:

- User-facing read operations: p95 < 500 ms, p99 < 1 s
- User-facing write operations: p95 < 1 s, p99 < 2 s
- API reads (authenticated): p95 < 300 ms, p99 < 800 ms
- TAG-BCR computation per scheme: p95 < 5 s
- Outcomes bulk export: throughput ≥ 10 MB/s for authenticated downloads

**Measurement Method**: APM metrics instrumented per service (PRIN P-7); synthetic checks from representative user geographies within the UK

**Load Conditions**:

- Peak concurrent human users: 500
- Peak API requests: 200 req/s
- Quarterly claim submission peak: 2,000 claim submissions in a 4-hour window

**Priority**: HIGH

---

#### NFR-P-2: Throughput

**Requirement**: System must handle 200 req/s sustained at peak with capability to burst to 500 req/s for up to 15 minutes during claim deadlines. Scales horizontally (PRIN P-8).

**Priority**: HIGH

---

### Availability and Resilience Requirements

#### NFR-A-1: Availability target (core platform)

**Requirement**: Core platform availability 99.9 % (≤ 43 min/month downtime). Maintenance windows outside the quarter-end claim peak (last 10 working days of March, June, September, December excluded from planned maintenance).

**Priority**: CRITICAL

---

#### NFR-A-2: Availability target (tiered services)

**Requirement**:

- TAG-BCR microservice: 99.5 % (batch-friendly; async retry tolerated)
- Public outcomes feed: 99.9 %
- Internal reporting: 99.5 %

**Priority**: HIGH

---

#### NFR-A-3: Disaster recovery

**Requirement**:

- **RPO**: ≤ 15 min for transactional data; ≤ 24 h for analytics stores
- **RTO**: ≤ 4 h for core services; ≤ 24 h for full functionality
- Backup frequency: continuous for transactional data, daily for analytics
- Backup retention: 7 years for audit-relevant records
- Backup location: UK only (PRIN P-10)
- Automated failover tested at least annually

**Priority**: CRITICAL

---

#### NFR-A-4: Fault tolerance

**Requirement**: System must gracefully degrade when external dependencies fail (PRIN P-9).

**Resilience patterns**:

- [ ] Circuit breaker for external dependencies (MHCLG FS hosted instance, NISTA, OSCAR, Notify, Pay, Spotlight/GGIS, OS Data Hub)
- [ ] Retry with exponential backoff + jitter for transient failures
- [ ] Timeout on all network calls (default 5 s; configurable)
- [ ] Bulkhead isolation between public-facing read path and authenticated write path
- [ ] Degraded mode: outcomes publication and reporting read-only when write path recovering

**Priority**: HIGH

---

### Scalability Requirements

#### NFR-S-1: Horizontal scaling

**Requirement**: System must support horizontal scaling without code changes (PRIN P-8). Growth projections (driven by Integrated Settlement expansion):

- Year 1 (2026/27): 2 Tier-1 MCAs, scheme-level not required
- Year 2 (2027/28): 2 Tier-1 + 5 Tier-2 + 2 Tier-3 MCAs + GLA observer = up to 10 authorities
- Year 3 (2028/29): 9 authorities + GLA at full Integrated Settlement tier
- CRSTS2 covers 2027–2032, so throughput stable-to-growing across 5 years

**Scaling triggers**: Auto-scale on queue depth, request rate, and CPU

**Priority**: HIGH

---

#### NFR-S-2: Data volume scaling

**Requirement**: Handle data growth to ~5 TB over 5 years (schemes + documents + audit + outcomes history + evaluation). Hot storage for < 2 years, warm for 2–7 years, cold thereafter.

**Priority**: MEDIUM

---

### Security Requirements

#### NFR-SEC-1: Authentication

**Requirement**: Human authentication via **GOV.UK One Login** (mandatory by end of 2027). Best-in-class MFA until then. Service-to-service authentication via mutual TLS with signed tokens.

**Session management**:

- Session timeout: 30 minutes of inactivity
- Absolute session timeout: 8 hours
- Re-authentication for privileged operations (e.g. DP-gate decisions, drawdown submission)

**Priority**: CRITICAL

---

#### NFR-SEC-2: Authorisation

**Requirement**: RBAC with least privilege. Roles scoped per authority where applicable (e.g. GMCA Scheme Officer cannot see WMCA schemes).

**Core roles**: MCA Scheme Officer, MCA Portfolio Director, MCA Finance Approver, DfT Assurance Officer, DfT Finance Officer, DfT SRO, DfT TAG Analyst, HMT Desk Officer, NISTA Pipeline Analyst, Platform Administrator.

**Priority**: CRITICAL

---

#### NFR-SEC-3: Data encryption

**Requirement** (PRIN P-5):

- Data in transit: TLS 1.2 minimum, TLS 1.3 target, strong cipher suites
- Data at rest: AES-256 for all stores (primary, replicas, backups)
- Field-level encryption for commercial-confidence bid data (OFFICIAL-SENSITIVE)
- Keys managed in a hardened key-management service, UK-hosted
- Customer-managed keys for OFFICIAL-SENSITIVE scope

**Priority**: CRITICAL

---

#### NFR-SEC-4: Secrets management

**Requirement**: No secrets in code, configuration files, or repository. Secrets stored in hardened secret store with rotation every 90 days (privileged) / annually (service-account).

**Priority**: CRITICAL

---

#### NFR-SEC-5: Vulnerability management

**Requirement**:

- Dependency scanning in CI/CD — no critical or high unmitigated vulnerabilities permitted in production
- SAST and DAST in CI
- Annual CHECK / ITHC penetration testing
- SBOM generated per release
- Remediation SLAs: Critical 7 days, High 30 days, Medium 90 days (per NCSC guidance + project agreement)

**Priority**: CRITICAL

---

#### NFR-SEC-6: NCSC Secure by Design and GovAssure

**Requirement**: NCSC Secure by Design principles applied per-service. GovAssure CAF assessment scheduled for the core platform before Public Beta.

**Priority**: CRITICAL

---

### Compliance and Regulatory Requirements

#### NFR-C-1: UK GDPR / Data Protection Act 2018

**Requirement**:

- DPIA completed and approved before Private Beta
- Clear controller / processor / joint-controller roles documented per data flow (PRIN P-12)
- Article 28 DPAs executed with every MCA and material sub-processor
- Data subject rights (access, rectification, erasure, portability, restriction, objection) implemented and testable within statutory timelines
- Data breach notification within 72 hours to ICO where required
- ICO prior consultation for novel processing (including ML-assisted triage if scoped)

**Data residency**: UK only (PRIN P-10). Transfers outside UK-adequacy area require UK-GDPR transfer mechanism and explicit SIRO approval.

**Data retention**: 7 years for audit-relevant records; 6 years for grant-administration records post-scheme-closure; automated deletion after retention period.

**Priority**: CRITICAL

---

#### NFR-C-2: Audit logging

**Requirement**: Comprehensive tamper-evident audit trail for sensitive operations (PRIN P-5, FR-12). Audit logs retained 7 years, immutable storage. Cryptographic hash-chain for tamper evidence.

**Priority**: CRITICAL

---

#### NFR-C-3: Technology Code of Practice

**Requirement**: TCoP self-assessment returns Green across all 12 points at each CDDO spend-control gate (SOC, OBC, FBC) (BR-7).

**Priority**: CRITICAL

---

#### NFR-C-4: Cabinet Office Grants Function Minimum Requirements

**Requirement**: Spotlight due-diligence integration (FR-16), GGIS registration, compliance with Cabinet Office grants minimum standards at assurance and award stages.

**Priority**: MUST_HAVE

---

#### NFR-C-5: Official statistics obligations

**Requirement**: Outcome data published under the Code of Practice for Statistics where designated as official statistics. Advance notice of publication timings per Code.

**Priority**: MEDIUM

---

### Usability Requirements

#### NFR-U-1: User experience

**Requirement**:

- GOV.UK Design System for all user-facing components (PRIN P-1, P-6)
- Accessibility: WCAG 2.2 Level AA compliance (PRIN P-6)
- Browser support: current and previous major versions of Chrome, Edge, Safari, Firefox
- Mobile-responsive design for read operations (quarterly claim submission supported on desktop)
- Consistent with the MHCLG Funding Service user experience where the Funding Service is the underlying substrate

**Priority**: CRITICAL

---

#### NFR-U-2: Accessibility (NON-NEGOTIABLE — PRIN P-6)

**Requirement**: WCAG 2.2 Level AA compliance and Public Sector Bodies Accessibility Regulations 2018 compliance.

**Accessibility features**:

- [ ] Keyboard navigation for all functions
- [ ] Screen reader compatibility tested with NVDA and JAWS
- [ ] High contrast mode
- [ ] Adjustable font sizes
- [ ] Alt text on all images
- [ ] Accessible alternative for the geospatial map view
- [ ] No CAPTCHA that blocks assistive-technology users

**Testing**: Automated a11y checks in CI (axe-core or equivalent); manual audit by third-party accessibility consultant before Public Beta; published accessibility statement per service.

**Priority**: CRITICAL

---

#### NFR-U-3: Language and locale

**Requirement**: English (en-GB) primary. Welsh-language support SHOULD be available where the platform serves Welsh users (no MCA currently covers Wales, but the TAG microservice and open-data publishing may serve Welsh Government users). Date formats ISO 8601 internally; en-GB (`DD Month YYYY`) for display.

**Priority**: SHOULD_HAVE

---

### Maintainability and Supportability Requirements

#### NFR-M-1: Observability (PRIN P-7)

**Requirement**: Structured logging, metrics, and distributed tracing across all services.

- **Logging**: Structured JSON with correlation IDs, centralised aggregation
- **Metrics**: RED (Rate, Errors, Duration) + USE (Utilisation, Saturation, Errors) per service
- **Tracing**: OpenTelemetry-compatible distributed tracing
- **Alerting**: SLO-based alerts with actionable runbooks, not threshold-spam
- **Dashboards**: Real-time operational dashboards for core platform, TAG microservice, OSCAR integration, NISTA feed

**Log retention**:

- Security / audit logs: 7 years, immutable
- Application logs: 90 days
- Metrics: 13 months (year-on-year comparison)

**Priority**: CRITICAL

---

#### NFR-M-2: Documentation

**Requirement**: Maintain architecture docs (C4), API docs (OpenAPI / AsyncAPI), runbooks, ADRs, user manuals, admin guides, and MCA onboarding playbook. Documentation lives alongside code in version control; updated within 5 working days of code change.

**Priority**: HIGH

---

#### NFR-M-3: Operational runbooks

**Requirement**: Runbooks for deployment, rollback, backup/restore, incident response (per failure mode), scaling, DR drill, secret rotation, new-MCA onboarding, TAG Data Book release handling.

**Priority**: HIGH

---

#### NFR-M-4: Infrastructure as Code (PRIN P-20)

**Requirement**: All infrastructure declared in code, version-controlled, deployed via automated pipelines. Drift detection daily. No manual production changes.

**Priority**: HIGH

---

### Portability and Interoperability Requirements

#### NFR-I-1: API standards

**Requirement**: OpenAPI 3.x for synchronous HTTP; AsyncAPI 2.x for events; JSON Schema for payload validation; GeoJSON for spatial; ISO 8601 for dates. Consistent error response format. Versioned via URL path.

**Priority**: HIGH

---

#### NFR-I-2: Integration capabilities

**Requirement**: Platform integrates with MHCLG Funding Service, NISTA, OSCAR/Clear Line of Sight, GOV.UK One Login / Notify / Pay / Forms, OS Data Hub, Cabinet Office Spotlight + GGIS, and each MCA's chosen back-end (Dynamics 365, Salesforce, Power Platform, etc.) via API contracts.

**Integration SLAs**: 99 % success rate, latency appropriate per integration (see INT-x requirements).

**Priority**: CRITICAL

---

#### NFR-I-3: Data portability

**Requirement**: Users and administrators can export data in CSV, JSON, or PDF (per data type). Bulk import supported via AsyncAPI for authority-level migrations.

**Priority**: MEDIUM

---

#### NFR-I-4: Open-source and open-standards policy (PRIN P-4)

**Requirement**: All code published under OGL v3 unless SIRO-signed exception. Open standards for all data exchange. No vendor-proprietary formats for persistent storage.

**Priority**: HIGH

---

### Financial Requirements

#### NFR-F-1: Proportionality (PRIN P-23)

**Requirement**: Platform 3-year TCO ≤ £5.5m, representing ≤ 0.04 % of grant throughput. Quarterly cost tracking against target.

**Priority**: HIGH

---

## Integration Requirements

### External System Integrations

#### INT-1: MHCLG Funding Service (case-management substrate)

**Purpose**: Reuse MHCLG Funding Service as the case-management and form-builder foundation (BR-2).

**Integration Type**: Code reuse (fork + contribute) + runtime integration where shared services are hosted by MHCLG.

**Data Exchanged**: Scheme and claim records, form definitions, user context.

**Integration Pattern**: Library + hosted-service consumption per the joint engineering governance agreement.

**Authentication**: Federated via GOV.UK One Login; service-to-service via mutual TLS / signed tokens.

**Error Handling**: Local graceful degradation if hosted MHCLG instance unavailable (PRIN P-9).

**SLA**: Inherited from MHCLG hosted instance + local fallback.

**Owner**: MHCLG Digital — Funding Service team.

**Priority**: CRITICAL

---

#### INT-2: NISTA pipeline-update feed

**Purpose**: Publish CRSTS2/TCR pipeline events for NISTA assurance ingestion.

**Integration Type**: Event-driven (AsyncAPI) + REST endpoint fallback.

**Data Exchanged**: Scheme lifecycle events, DP-gate decisions, drawdown updates.

**Integration Pattern**: Publish to NISTA-consumed topic; REST pull endpoint for reconciliation.

**Authentication**: Mutual TLS with signed tokens.

**Error Handling**: Retries with exponential backoff; dead-letter with escalation.

**SLA**: Delivery within 15 minutes of source event for 99.9 % of events.

**Owner**: NISTA assurance engineering.

**Priority**: CRITICAL

---

#### INT-3: HMT OSCAR / Clear Line of Sight

**Purpose**: Submit drawdown profiles per quarter; reconcile actuals.

**Integration Type**: File-based / API per HMT spec.

**Data Exchanged**: Drawdown profile per quarter; confirmation receipts.

**Authentication**: Per HMT OSCAR approved mechanism.

**Error Handling**: Reconciliation reports produced automatically; manual intervention flagged within 1 hour.

**SLA**: Profile submitted within the quarterly reporting window (per HMT calendar).

**Owner**: DfT Finance / Clear Line of Sight team.

**Priority**: CRITICAL

---

#### INT-4: GOV.UK One Login

**Purpose**: Human user authentication (mandatory for central-government services by end-2027).

**Integration Type**: OIDC.

**Data Exchanged**: Authenticated identity, email, levels of verification.

**Authentication**: OIDC flows per GDS documentation.

**SLA**: Inherited from GOV.UK One Login.

**Owner**: GDS.

**Priority**: CRITICAL

---

#### INT-5: GOV.UK Notify

**Purpose**: All transactional notifications (email / SMS / letter).

**Integration Type**: REST API.

**Data Exchanged**: Notification payloads per templated messages.

**Owner**: GDS.

**Priority**: MUST_HAVE

---

#### INT-6: OS Data Hub (OS MasterMap, PSGA)

**Purpose**: Geospatial base mapping and authority boundaries for scheme visualisation.

**Integration Type**: REST/tile API.

**Owner**: Ordnance Survey.

**Priority**: SHOULD_HAVE

---

#### INT-7: `data.gov.uk` publishing

**Purpose**: Open-data publication of outcomes datasets.

**Integration Type**: CKAN API / publishing pipeline.

**Owner**: GDS.

**Priority**: MUST_HAVE

---

#### INT-8: Cabinet Office Spotlight + GGIS

**Purpose**: Due-diligence (Spotlight) and cross-government grants register (GGIS) integration.

**Integration Type**: REST API.

**Owner**: Cabinet Office Grants Function.

**Priority**: SHOULD_HAVE

---

#### INT-9: MCA federation endpoints (9 authorities + GLA observer)

**Purpose**: Inbound and outbound data exchange with MCA systems (Dynamics 365, Salesforce, etc.).

**Integration Type**: OpenAPI + AsyncAPI federation per FR-2, FR-3.

**Data Exchanged**: Schemes, claims, outcomes, indicators, drawdowns.

**Authentication**: Federated identity (OIDC) + mutual TLS service accounts.

**SLA**: Per MCA MoC; minimum 99 % delivery success for outcome updates.

**Owner**: Each MCA's digital lead.

**Priority**: CRITICAL

---

#### INT-10: DfT TAG Data Book service

**Purpose**: Consume TAG Data Book releases (May and November) as the authoritative input to BCR computations.

**Integration Type**: File ingestion + signed-version API.

**Owner**: DfT TAG Unit.

**Priority**: CRITICAL

---

## Data Requirements

### Data Entities

#### DR-1: Authority

**Description**: A Mayoral Combined Authority (or Combined County Authority, or the GLA as observer) participating in CRSTS / TCR.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| id | UUID | Yes | Internal identifier | Primary key |
| name | String(255) | Yes | Authority name | Not null |
| authority_type | Enum | Yes | `MCA` / `CCA` / `GLA` | Not null |
| integrated_settlement_tier | Enum | Yes | `TIER_1` / `TIER_2` / `TIER_3` / `OBSERVER` | Not null |
| crsts2_envelope_gbp | Numeric(15,2) | No | Allocated envelope | |
| onboarded_at | Timestamp | Yes | Date of onboarding | |

**Data Volume**: ~10 records (9 MCAs + GLA)
**Data Classification**: OFFICIAL
**Retention**: Permanent (with archival on status change)

---

#### DR-2: Scheme

**Description**: A CRSTS / TCR scheme submitted by an authority.

**Attributes**: id, authority_id, name, description, scheme_type, status, outcomes (link table), estimated_cost, actual_cost, start_date, end_date, geospatial_extent (GeoJSON), created_at, updated_at, superseded_by_scheme_id, etc.

**Data Volume**: ~500 records Year 1; ~3,000 records Year 5
**Data Classification**: OFFICIAL (OFFICIAL-SENSITIVE for commercial-confidence attributes)
**Retention**: 7 years post-closure

---

#### DR-3: Outcome

**Description**: An Integrated Settlement outcome.

**Attributes**: id, stable_uri, category, description, measurement_method, version, deprecated_at.

**Data Volume**: ~50 outcomes nationally
**Data Classification**: OFFICIAL (Public when published)
**Retention**: Permanent (versioned)

---

#### DR-4: Indicator

**Description**: A measurable indicator linked to outcomes.

**Attributes**: id, stable_uri, outcome_id, name, unit_of_measure, accepted_range_min, accepted_range_max, measurement_frequency, version.

**Data Volume**: ~200 indicators
**Data Classification**: OFFICIAL (Public when published)
**Retention**: Permanent (versioned)

---

#### DR-5: Indicator measurement

**Description**: A value reported by an authority for an indicator at a point in time.

**Attributes**: id, indicator_id, authority_id, scheme_id (optional), period_start, period_end, value, source, quality_flag.

**Data Volume**: Hundreds of thousands over lifetime
**Data Classification**: OFFICIAL (Public when published as aggregate)
**Retention**: Permanent (for longitudinal analysis)

---

#### DR-6: Claim

**Description**: A claim submitted against an approved scheme.

**Attributes**: id, scheme_id, amount_gbp, period_start, period_end, status, supporting_evidence_refs.

**Data Volume**: ~5,000 claims/year once at steady state
**Data Classification**: OFFICIAL (with OFFICIAL-SENSITIVE for commercial attributes)
**Retention**: 7 years

---

#### DR-7: Drawdown

**Description**: A drawdown submitted to HMT OSCAR against approved claims.

**Attributes**: id, authority_id, quarter, profile_amount_gbp, actual_amount_gbp, oscar_confirmation_id.

**Data Volume**: 4 per authority per year
**Data Classification**: OFFICIAL
**Retention**: 7 years

---

#### DR-8: TAG run

**Description**: A recorded invocation of the TAG-BCR microservice with inputs, outputs, and Data Book version used.

**Attributes**: id, scheme_id, invoked_at, tag_data_book_version, inputs_hash, bcr_result, vfm_category, calculation_signature.

**Data Volume**: ~10,000+ runs over lifetime
**Data Classification**: OFFICIAL
**Retention**: Permanent (audit-critical)

---

#### DR-9: Assurance decision

**Description**: A DP1–DP7 decision record.

**Attributes**: id, scheme_id, gate (DP1..DP7), decision (Proceed / Proceed with conditions / Do not proceed), decision_maker_id, decision_justification, signed_at, hash_chain_prev, hash_chain_current.

**Data Volume**: ~7 per scheme over lifetime
**Data Classification**: OFFICIAL (OFFICIAL-SENSITIVE for pre-decision content)
**Retention**: Permanent (audit-critical)

---

#### DR-10: Audit log entry

**Description**: Append-only tamper-evident log of significant operations.

**Attributes**: id, timestamp, actor_identity, action, resource, request_id, outcome, prev_hash, current_hash.

**Data Volume**: Many millions over lifetime
**Data Classification**: OFFICIAL
**Retention**: 7 years immutable

---

#### DR-11: User and role assignment

**Description**: Users and their role assignments per authority.

**Attributes**: id, one_login_subject_id, email, role, authority_id (optional — DfT roles have no authority), assigned_at, revoked_at.

**Data Volume**: ~2,000 users
**Data Classification**: OFFICIAL (personal data — PRIN P-12)
**Retention**: 6 years post-revocation

---

### Data Quality Requirements

**Accuracy**: Validation rules at ingest (schema, cross-field, referential integrity). Error rate target < 0.5 % of records requiring manual correction.

**Completeness**: Required fields enforced at write; optional fields flagged if absent at reporting time.

**Consistency**: Reconciliation between platform and OSCAR quarterly; between platform and MCA systems per MoC cadence.

**Timeliness**: Outcomes refresh within 15 minutes of authority submission; published open-data refreshed quarterly; NISTA feed within 15 minutes.

**Lineage**: Every record traceable to source system (e.g. authority's MCA system) via correlation ID and ingest timestamp.

---

### Data Migration Requirements

**Migration scope**: CRSTS1 mid-life scheme, claim and drawdown data from DfT spreadsheets and MCA systems (where authorities consent) to the platform, for continuity into CRSTS2.

**Migration strategy**: Phased per authority; parallel run for the first quarter per authority.

**Validation**: Total-sum reconciliation against HMT OSCAR and authority-submitted totals.

**Rollback**: Platform records mark `migrated_from` source; rollback = mark records inactive, authorities continue in legacy tooling.

---

## Constraints and Assumptions

### Technical Constraints

- **TC-1**: Must integrate with MHCLG Funding Service (BR-2, INT-1) — architectural and technology choices bounded by the Funding Service stack (Python/Flask/Aurora Postgres at time of writing)
- **TC-2**: Must use GOV.UK One Login for human authentication by end-2027 (INT-4)
- **TC-3**: UK-only data hosting for all personal data (PRIN P-10)
- **TC-4**: OGL v3 publication for DfT-written code (PRIN P-4)
- **TC-5**: WCAG 2.2 AA and PSBAR 2018 compliance mandatory (PRIN P-6, NFR-U-2)
- **TC-6**: GOV.UK Design System for user-facing components (NFR-U-1)

---

### Business Constraints

- **BC-1**: Platform 3-year TCO ≤ £5.5m (BR-6, NFR-F-1)
- **BC-2**: Public Beta must be operational before the April 2027 Tier-2 Integrated Settlement start for at least 5 MCAs (STKE Goal G-1)
- **BC-3**: Procurement route must comply with Procurement Act 2023; G-Cloud 14 window closes ~March 2026 and is succeeded by G-Cloud 15 under new rules [DFSN-C7]
- **BC-4**: Must reuse MHCLG Funding Service unless an SRO-signed exception exists (BR-2)
- **BC-5**: No forced MCA stack replacement (BR-4, PRIN P-2)
- **BC-6**: All changes subject to CDDO spend controls at SOC / OBC / FBC

---

### Assumptions

- **A-1**: MHCLG Digital has capacity to partner on Funding Service extension from Q2 2026 onward (if not, R-1 materialises)
- **A-2**: NISTA data schema stabilises sufficiently for stable integration by OBC submission (Q3 2026) — if not, R-3 materialises
- **A-3**: GOV.UK One Login can support high-assurance roles for DfT and MCA officials (currently provided but verify at Alpha)
- **A-4**: All 9 MCAs agree to participate via MoCs by Requirements Freeze (STKE Goal G-4)
- **A-5**: TAG Data Book release cadence remains twice-yearly (May and November)
- **A-6**: ICO does not mandate a position blocking novel processing before Private Beta (requires early engagement)
- **A-7**: CRSTS2 funding profile as announced at SR25 is not reduced materially mid-programme

**Validation plan**: A-1 validated at technical fit workshop in first 30 days (STKE G-5); A-2 validated at NISTA technical engagement; A-3 tested at Alpha; A-4 tracked via MoC register.

---

## Success Criteria and KPIs

### Business Success Metrics

| Metric | Baseline | Target | Timeline | Measurement Method |
|--------|----------|--------|----------|--------------------|
| MCAs on platform | 0 | ≥ 5 | April 2027 | Platform onboarding register |
| CRSTS2 scheme throughput on platform | 0 % | ≥ 90 % | End Year 2 post-Public Beta | Platform vs HMT reporting reconciliation |
| 3-year platform TCO | n/a | ≤ £5.5m | End Year 3 | Quarterly cost reporting |
| Platform cost ratio to grant throughput | n/a | ≤ 0.05 % | Annual | Platform cost / grant value throughput |
| Time to first drawdown post-FBC | > 6 months (CRSTS1) | < 3 months | End Year 2 | Platform audit trail |
| Cross-gov reuse adopters of TAG microservice | 0 | ≥ 1 department | March 2028 | Cross-department technical-partnership log |

---

### Technical Success Metrics

| Metric | Target | Measurement Method |
|--------|--------|--------------------|
| Core platform availability | 99.9 % | Synthetic + APM |
| Public outcomes feed availability | 99.9 % | Synthetic checks |
| TAG-BCR microservice availability | 99.5 % | Synthetic + APM |
| API response time p95 | < 300 ms (reads), < 1 s (writes) | APM |
| Error rate | < 0.5 % | Log aggregation |
| Deployment frequency | ≥ weekly per service | CI/CD metrics |
| MTTR | < 4 h for core; < 30 min for minor | Incident tracking |
| Automated-accessibility CI pass rate | 100 % (zero critical) | axe-core in CI |

---

### User Adoption Metrics

| Metric | Target | Timeline | Measurement Method |
|--------|--------|----------|--------------------|
| Authorised users across authorities | ≥ 500 | 6 months post-Public-Beta | User register |
| Schemes submitted via platform (vs email/SharePoint) | ≥ 80 % | End Year 2 | Platform metrics |
| User satisfaction (MCA officers, DfT assurance) | ≥ 7/10 | Annual survey | User survey |
| Open-data downloads (`data.gov.uk`) | ≥ 500 unique downloads/quarter | End Year 2 | `data.gov.uk` analytics |

---

## Dependencies and Risks

### Dependencies

| Dependency | Description | Owner | Target Date | Status | Impact if Delayed |
|------------|-------------|-------|-------------|--------|-------------------|
| MHCLG Funding Service engagement | Joint Engineering Governance agreement signed (BR-2, G-5) | MHCLG Digital + SRO | End Q1 2026 | At Risk | HIGH |
| SRO appointment | Director-level SRO in post | DG Rail / Places / Local Transport | End Q1 2026 | At Risk | HIGH |
| NISTA schema | Pipeline-update schema stable for integration (INT-2) | NISTA | Q3 2026 | At Risk | MEDIUM |
| TAG Data Book API access | Authoritative TAG Data Book consumable by microservice (INT-10) | DfT TAG Unit | Q3 2026 | On Track | HIGH |
| MCA MoCs | ≥ 5 MCA MoCs signed (BR-4, G-4) | SRO office | Q2 2026 | At Risk | HIGH |
| GOV.UK One Login onboarding | Service account provisioned, OIDC tested | GDS | Alpha | On Track | HIGH |
| DPIA | Approved before Private Beta (BR-8, G-6) | DfT SIRO + DPOs | Q1 2027 | On Track | HIGH |
| OSCAR integration access | Approval and test credentials | HMT + DfT Finance | OBC | On Track | HIGH |

---

### Risks

(Full risk register in `/arckit:risk` output — key requirement-driving risks shown here; referenced against STKE R-x.)

| Risk ID | Description | Probability | Impact | Mitigation Strategy | Owner |
|---------|-------------|-------------|--------|---------------------|-------|
| R-1 | MHCLG Funding Service immaturity delays MVP (STKE R-1) | MEDIUM | HIGH | Technical fit workshop; joint engineering governance; documented commercial-SaaS fallback | SRO |
| R-2 | Tier-1 MCA publicly rejects the platform (STKE R-2) | MEDIUM | CRITICAL | Federated-design principle; Mayoral correspondence; API-only option | SRO |
| R-3 | NISTA schema churn forces rework (STKE R-3) | HIGH | MEDIUM | Embed NISTA analyst; anti-corruption layer; monthly schema review | Enterprise Architect |
| R-4 | SRO not appointed before SOC (STKE R-4) | MEDIUM | HIGH | DG commitment; interim sponsor | DG Rail / Places |
| R-5 | Joint-controller ambiguity with MCAs on DPIA (STKE R-5) | HIGH | MEDIUM | Early DPIA; Cabinet Office data-sharing templates; ICO prior consultation | SIRO |
| R-6 | TAG Unit rejects externalising BCR logic (STKE R-6) | LOW-MEDIUM | HIGH | Source-code ownership to TAG; embedded engineers | Chief Analyst |
| R-7 | Procurement Act 2023 transition (G-Cloud 14 → 15) timing gap (STKE R-7) | MEDIUM | MEDIUM | Book G-Cloud 14 window; or commit to G-Cloud 15 in SOC | DfT Commercial |
| R-8 | NAO publishes critical report mid-build (STKE R-8) | MEDIUM | MEDIUM | Pre-publication engagement with NAO; position platform as answer | Perm Sec, SRO |

---

## Requirement Conflicts & Resolutions

### Conflict C-1: HMT / NISTA visibility vs MCA Integrated Settlement autonomy

**Conflicting Requirements**:

- **Requirement A**: BR-1 + FR-8 + FR-19 (consolidated pipeline view with scheme-level detail)
- **Requirement B**: BR-4 + BR-5 + PRIN P-2 + PRIN P-3 (federation without centralising; outcomes-first for Tier-1 Integrated Settlement authorities)

**Stakeholders Involved**:

- **HMT / NISTA / NAO** (SD-2, SD-3, SD-9): want scheme-level data with near-real-time visibility
- **GMCA / WMCA** (SD-5): fought for outcomes-level accountability; scheme-level visibility to DfT is perceived as regression of Integrated Settlement autonomy

**Nature of Conflict**: A consolidated scheme-level pipeline view — if made available to HMT/NISTA at the same granularity for every MCA — re-imposes the pre-Integrated-Settlement regime that the Tier-1 Mayors fought against.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Full scheme-level visibility mandated for all MCAs | ✅ Simplifies HMT/NISTA model | ❌ Breaks Integrated Settlement policy; Mayoral rejection risk; PRIN P-2 violation | HMT/NISTA happy; Tier-1 MCAs withdraw |
| **Option 2**: Outcomes-only for all MCAs | ✅ Protects autonomy | ❌ Breaks CRSTS1 and Tier-3 workflow needs | Tier-1 MCAs happy; HMT/NISTA under-informed; Tier-3 MCAs confused |
| **Option 3**: Two-plane data design — outcomes mandatory for Tier-1, scheme-level for Tier-3, tiered access controls | ✅ Balances; aligns to IS policy; satisfies PRIN P-2/P-3 | ❌ More complex data model; two reporting views | Both parties reasonably satisfied |

**Resolution Strategy**: INNOVATE / COMPROMISE

**Decision**: Option 3 — **two-plane data design** (per STKE Conflict 1 resolution).

**Rationale**: Aligns to HMG Integrated Settlement policy; satisfies non-negotiable PRIN P-2 (federated) and P-3 (outcomes-first); provides HMT/NISTA with the outcomes view they fundamentally need and which is published under statutory outcomes reporting; does not require Tier-1 MCAs to expose scheme-level data to DfT.

**Decision Authority**: SRO with DG sign-off; ratified as an ADR (`ARC-001-ADR-001-v1.0` — to be written in `/arckit:adr`).

**Impact on Requirements**:

- **Modified**: BR-1 success criteria changed — "90 % of CRSTS2/TCR scheme throughput visible in a single pipeline view" qualifies outcome-level for Tier-1 and scheme-level for Tier-3
- **Confirmed**: BR-4, BR-5 and PRIN P-2, P-3 protected
- **Added**: FR-19 dashboard views differentiated by authority tier

**Stakeholder Management**:

- **HMT / NISTA (partially lost scheme-level visibility for Tier-1)**: Outcome-level data is the HMG Integrated Settlement design; supplied on richer cadence than any existing arrangement
- **GMCA / WMCA (gained autonomy protection)**: Written principle commitment; API-only participation option; Mayoral correspondence

**Future Consideration**: If Integrated Settlement scope rolls back (unlikely under current HMG policy), re-evaluate.

---

### Conflict C-2: Reuse MHCLG Funding Service vs speed pressure from SRO / HMT

**Conflicting Requirements**:

- **Requirement A**: BR-2 + PRIN P-1 (reuse MHCLG Funding Service)
- **Requirement B**: STKE G-1 (≥ 5 MCAs live by April 2027), BR-6 (TCO ≤ £5.5m)

**Stakeholders Involved**:

- **CDDO / MHCLG Digital** (SD-4, SD-11): reuse is the default and the validation milestone
- **SRO / HMT** (SD-1, SD-2): need predictable delivery against the April 2027 Integrated Settlement milestone; MHCLG Funding Service immaturity (2 grants at launch) is a risk factor

**Nature of Conflict**: MHCLG Funding Service reuse reduces long-term risk and aligns to TCoP, but its short-term maturity may not match DfT's April 2027 milestone.

**Trade-off Analysis**:

| Option | Pros | Cons |
|--------|------|------|
| **Option 1**: Reuse MHCLG FS fully, accept some delivery risk | ✅ TCoP compliant | ❌ Funding Service maturity risk |
| **Option 2**: Commercial SaaS (Flexi-Grant / Salesforce GovGrants) as primary | ✅ Faster certainty | ❌ TCoP non-compliant without strong justification |
| **Option 3**: Fork + contribute, with time-boxed SaaS fallback gate at OBC | ✅ Reuse path with risk mitigation | ❌ Two-track investment (upstream contrib + integration) |

**Resolution Strategy**: PHASE / INNOVATE

**Decision**: Option 3 — **Fork + contribute MHCLG FS, with documented SaaS fallback gated at OBC**.

**Rationale**: Preserves the non-negotiable reuse stance (PRIN P-1) and the defensive SRO posture; time-boxing gives a credible off-ramp if the fit workshop and first sprints show > 6 months to onboard CRSTS-scale use cases.

**Decision Authority**: SRO with CDIO and CDDO consult; ratified as an ADR.

**Impact on Requirements**:

- **Confirmed**: BR-2 (reuse as default)
- **Added**: OBC-gate fallback decision criteria documented as part of G-5 governance agreement
- **Added**: Shadow SaaS assessment (not live procurement) to keep fallback credible

**Stakeholder Management**:

- **SRO / HMT**: Explicit gated fallback; governance risk visible, not hidden
- **MHCLG Digital**: Joint engineering governance board; upstream contribution commitment

---

### Conflict C-3: TAG Unit ownership of BCR logic vs vendor "BCR-as-a-service" simplicity

**Conflicting Requirements**:

- **Requirement A**: BR-3 + PRIN P-13 (TAG Unit owns microservice source; Data Book version transparent)
- **Requirement B**: Operational pressure for a SaaS that "does BCR" with push-button UX

**Stakeholders Involved**:

- **DfT TAG Unit / Chief Analyst** (SD-7): professional accountability for Green Book/TAG integrity
- **Operational leads** (efficiency-driven): want the simplest user experience

**Resolution Strategy**: PRIORITIZE

**Decision**: TAG Unit ownership is non-negotiable; vendor SaaS may integrate via API (consume the microservice) but **not replace** it.

**Rationale**: Green Book / TAG integrity is a statutory and professional obligation; opaque calculations cannot survive NAO audit. UX can be built on top of the microservice without opaquing the calculation.

**Impact on Requirements**:

- **Confirmed**: FR-9, PRIN P-13
- **Added**: NFR-SEC / audit requirements for calculation-level signing on microservice outputs

---

### Conflict C-4: Transparency / open data vs commercial confidentiality of sponsor bids

**Conflicting Requirements**:

- **Requirement A**: BR-5 + FR-11 (open-data publication)
- **Requirement B**: OFFICIAL-SENSITIVE handling of commercial-confidence bid data (NFR-C-1)

**Stakeholders Involved**:

- **Campaign groups / public** (SD-10): want transparency
- **MCAs / delivery contractors**: some commercial data genuinely confidential during tender stages

**Resolution Strategy**: PHASE / PRIORITIZE

**Decision**: Two-tier publication — outcomes / indicators open from the start; scheme-level financial detail restricted until FBC confirmation, at which point it becomes public per the data classification rules.

**Impact on Requirements**:

- **Added**: Data-classification tagging at field level for commercial-confidence attributes
- **Confirmed**: FR-11 publishes only OFFICIAL-classified data

---

### Conflict C-5: GOV.UK One Login readiness vs pre-2027 launch

**Conflicting Requirements**:

- **Requirement A**: BR-7 + FR-15 (GOV.UK One Login mandated by end-2027)
- **Requirement B**: Earlier Alpha / Private Beta launch (2026) before mandate

**Resolution Strategy**: PHASE

**Decision**: Alpha / Private Beta may use best-in-class MFA; Public Beta (April 2027) onward uses GOV.UK One Login. Integration readiness tested at Alpha.

**Impact on Requirements**:

- **NFR-SEC-1** updated to reflect phased identity-provider adoption

---

## Timeline and Milestones

### High-Level Milestones

| Milestone | Description | Target Date | Dependencies |
|-----------|-------------|-------------|--------------|
| Requirements Approval | Stakeholder sign-off on REQ v1.0 | 2026-05 | This document, STKE, PRIN |
| SOC submission | Strategic Outline Case | 2026-06 | BR-2 decision (MHCLG reuse), SRO appointment |
| Requirements Freeze | Requirements baselined | 2026-06 | ≥ 5 MCA MoCs signed |
| MHCLG Joint Engineering Governance | Agreement signed | 2026-06 | SOC |
| OBC submission | Outline Business Case | 2026-09 | NISTA + OSCAR integration tested; DPIA drafted |
| HLD approval | High-level design approved | 2026-09 | OBC |
| Alpha Service Assessment | GDS Alpha pass | 2026-11 | HLD |
| FBC submission | Full Business Case | 2026-12 | TAG-BCR microservice in alpha |
| DLD approval | Detailed design approved | 2027-01 | FBC |
| DPIA approval | Multi-controller DPIA signed off | 2027-02 | All 9 MCAs engaged |
| Private Beta | Invited MCA pilot (Tier-1) | 2027-03 | DPIA, Security assurance |
| Beta Service Assessment | GDS Beta pass | 2027-04 | Private Beta feedback |
| Public Beta | ≥ 5 MCAs live | 2027-04 | Integrated Settlement Tier-2 start |
| Live | All 9 MCAs + GLA observer | 2028-04 | Tier-2 onboarding complete |

---

## Budget

(Indicative; refined in SOBC / `/arckit:sobc` — based on discovery research [DFSN-C4].)

### Cost Estimate (3-year delivery window)

| Category | Estimated Cost (£) | Notes |
|----------|--------------------|-------|
| Development (fork + contribute FS, TAG microservice, federation, NISTA / OSCAR integration) | 2,200,000 – 3,200,000 | ~8–12 FTE over 24 months |
| Infrastructure (UK-hosted, cloud-based, IaC) | 400,000 – 700,000 | Incl. DR and observability |
| GOV.UK platform usage (Notify, Pay) | 30,000 – 60,000 | Pay-per-use |
| Third-party services (pen testing, accessibility audits, compliance assurance) | 150,000 – 250,000 | Annual |
| Training and change management (DfT + MCAs) | 100,000 – 200,000 | Including MCA onboarding capacity |
| Contingency (15 %) | ~ 450,000 – 800,000 | |
| **Total (3-year)** | **£3,000,000 – £5,500,000** | Target band per PRIN P-23 |

### Ongoing Operational Costs (Year 4+)

| Category | Annual Cost (£) | Notes |
|----------|------------------|-------|
| Infrastructure | 150,000 – 250,000 | |
| Maintenance and support | 400,000 – 700,000 | 3–5 FTE sustained |
| GOV.UK platform usage | 20,000 – 50,000 | Growing with users |
| Compliance and assurance | 100,000 – 200,000 | Annual |
| **Total (annual)** | **£670,000 – £1,200,000** | |

---

## Approval

### Requirements Review

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| SRO | Business Sponsor | [ ] Approved | PENDING | |
| Product Owner / Service Owner | Product Owner | [ ] Approved | PENDING | |
| Enterprise Architect | Technical | [ ] Approved | PENDING | |
| DfT SIRO | Security / information risk | [ ] Approved | PENDING | |
| DfT CDIO | Digital spend controls | [ ] Approved | PENDING | |
| DfT Chief Analyst | TAG appraisal | [ ] Approved | PENDING | |
| MHCLG Digital liaison | Reuse partnership | [ ] Reviewed | PENDING | |
| MCA Digital Reps Forum | Federation representation | [ ] Reviewed | PENDING | |

### Sign-Off

| Stakeholder | Signature | Date |
|-------------|-----------|------|
| SRO | PENDING | |
| DG Rail / Places / Local Transport | PENDING | |
| DfT CDIO | PENDING | |

---

## Appendices

### Appendix A: Glossary

| Term | Definition |
|------|------------|
| CRSTS | City Region Sustainable Transport Settlements |
| CRSTS1 | First CRSTS settlement, 2022/23–2026/27, £5.7bn |
| CRSTS2 / TCR | Second CRSTS (SR25), 2027–2032, £15.6bn across 9 MCAs |
| MCA | Mayoral Combined Authority |
| CCA | Combined County Authority (e.g. EMCCA) |
| Integrated Settlement | Single-pot devolved-outcome settlement from HMG to Tier-1/Tier-2 MCAs |
| DP1–DP7 | DfT CRSTS assurance decision gates |
| TAG | Transport Analysis Guidance (DfT) |
| BCR | Benefit–Cost Ratio |
| VfM | Value for Money category (derived from BCR per Green Book) |
| NISTA | National Infrastructure and Service Transformation Authority (IPA + NIC merger, 2025) |
| OSCAR | HMT Online System for Central Accounting & Reporting |
| GGIS | Government Grants Information System (Cabinet Office) |
| MHCLG FS | MHCLG Funding Service |
| OGL v3 | Open Government Licence v3 |
| PSGA | Public Sector Geospatial Agreement |
| TCoP | Technology Code of Practice |
| CAF | Cyber Assessment Framework (NCSC) |
| GovAssure | Centrally-run CAF assurance for UK Gov services |
| PSBAR | Public Sector Bodies Accessibility Regulations 2018 |

### Appendix B: Reference Documents

- `projects/000-global/ARC-000-PRIN-v1.0.md` — Architecture Principles
- `projects/001-dft-crsts-funding-platform/ARC-001-STKE-v1.0.md` — Stakeholder Analysis
- `projects/000-global/external/dft-funding-strategy-notes-v1.0.md` — Strategy notes
- `projects/000-global/external/dft-transforming-city-regions-research-v1.0.md` — Discovery research
- HMT Integrated Settlement policy (gov.uk)
- DfT TAG Unit Data Book (dft.gov.uk)
- MHCLG Funding Service repository (`github.com/communitiesuk/funding-service`)
- Cabinet Office Minimum Requirements for Grants
- NCSC Secure by Design principles
- GOV.UK Service Standard 14-point list

### Appendix C: Wireframes and Mockups

Not in scope for v1.0 — will be produced during Alpha / Beta design sprints and captured as `/arckit:diagram` artifacts.

### Appendix D: Data Models

High-level entities enumerated in Data Requirements section above. Full entity-relationship model to be produced via `/arckit:data-model` in a subsequent step.

---

**Document History**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-04-20 | ArcKit AI (Claude Opus 4.7) | Initial draft generated from STKE + PRIN + discovery research |

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| STKE | ARC-001-STKE-v1.0.md | Stakeholder Analysis | 001-dft-crsts-funding-platform/ | Stakeholder drivers, goals, outcomes, conflicts |
| PRIN | ARC-000-PRIN-v1.0.md | Architecture Principles | 000-global/ | 23 principles governing this programme |
| DFSN | dft-funding-strategy-notes-v1.0.md | Strategy | 000-global/external/ | Discovery-phase strategy brief |
| DTCR | dft-transforming-city-regions-research-v1.0.md | Research | 000-global/external/ | Discovery-phase market and landscape research |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| DFSN-C1 | DFSN | §5 Headline Numbers | Business Requirement | "Scale of underlying grant relationship: £15.6bn / 5 years / 9 MCAs (CRSTS2 + TCR)." |
| DFSN-C2 | DFSN | §1 + §9 NAO | Risk Factor | "The NAO has already flagged the fragmentation cost in bus funding: 13 separate streams, 19% of BSIP capital delivered by December 2024, capacity-to-manage cited as a root cause." |
| DFSN-C3 | DFSN | §3 Build-vs-buy + §4 Bet 2 | Design Decision | "MHCLG's new Funding Service went live in December 2025 … published under the Open Government Licence v3 at github.com/communitiesuk/funding-service … explicitly designed to be reused across government." |
| DFSN-C4 | DFSN | §5 Headline Numbers | Design Decision | "Programme administrative platform indicative 3-year TCO: £3m–£6m (hybrid: reuse MHCLG FS + bespoke TAG/BCR layer + GOV.UK platforms)." |
| DFSN-C5 | DFSN | §4 Bet 4 | Design Decision | "A microservice that consumes the DfT TAG Data Book … Make this the DfT flagship reusable component — it is valuable to non-DfT programmes too." |
| DFSN-C6 | DFSN | §4 Bet 1 + §2 | Stakeholder Need | "The Integrated Settlement trajectory means DfT's role is shifting from 'approver of each scheme' to 'steward of outcomes'." |
| DFSN-C7 | DFSN | §4 Bet 5 | Procurement Constraint | "The Procurement Act 2023 came into force 24 February 2025 and G-Cloud 15 (the first framework under it) launches March 2026." |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| dft-transforming-city-regions-research-v1.0.md | 000-global/external/ | Main research document reviewed. Vendor comparisons will be referenced formally in `/arckit:evaluate`. |
| vendors/*.md (6 profiles) | 000-global/external/vendors/ | Vendor-specific; referenced in `/arckit:evaluate` and `/arckit:sow`. |
| tech-notes/*.md (3 notes) | 000-global/external/tech-notes/ | Referenced in `/arckit:wardley` and `/arckit:hld-review`. |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-04-20
**ArcKit Version**: 4.8.0
**Project**: DfT CRSTS Funding Platform (Project 001)
**AI Model**: Claude Opus 4.7 (1M context)
**Generation Context**: Seeded from STKE (ARC-001-STKE-v1.0), PRIN (ARC-000-PRIN-v1.0), and discovery research / strategy notes in 000-global/external/
