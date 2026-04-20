# CLAUDE.md

## Project: DfT Transforming City Regions

UK Department for Transport Transforming City Regions funding system. A test project repository for ArcKit enterprise architecture governance, covering the design of a funding management platform that tracks bids, awards, conditions, and outcomes for investment into transport infrastructure across English city regions.

## Architecture Toolkit

This project uses the **ArcKit plugin** (v4.8.0) for enterprise architecture governance. All commands are provided by the plugin. No local command files are needed.

### Key Commands

- `/arckit.principles` - Architecture principles (start here)
- `/arckit.stakeholders` - Stakeholder analysis
- `/arckit.requirements` - Requirements specification
- `/arckit.sobc` - Strategic Outline Business Case
- `/arckit.adr` - Architecture Decision Records
- `/arckit.diagram` - Architecture diagrams (C4, sequence, etc.)

### Project Structure

- `projects/000-global/` - Cross-project artifacts (principles, standards)
- `projects/001-*/` - Numbered project directories with architecture documents
- `docs/` - Documentation and guides

### Document Naming Convention

All documents follow: `ARC-{PROJECT_ID}-{TYPE_CODE}-v{VERSION}.md`

- Example: `ARC-001-REQ-v1.0.md` (Requirements for project 001)
- Multi-instance types (ADR, DIAG): `ARC-001-ADR-001-v1.0.md`
