# Roadmap

> The development path for building and evolving the Living Knowledge System.

---

## Guiding Principle

Each phase builds on the previous. No phase begins until the previous phase is complete and stable.

Documentation precedes implementation. Architecture precedes coding. Philosophy precedes architecture.

---

## Phase 0 — Foundation and Documentation

**Goal:** Establish the project's philosophical and documentary foundation.

**Status:** In Progress

### Deliverables

- [x] `docs/00-philosophy.md` — Project philosophy
- [x] `docs/01-manifesto.md` — Project manifesto
- [x] `docs/02-living-knowledge-system.md` — Living Knowledge System concept
- [x] `docs/03-research-studio.md` — Research Studio UI concept
- [x] `docs/04-financial-medical-record.md` — Financial Medical Record framework
- [x] `docs/05-tree-of-understanding.md` — Tree of Understanding metaphor
- [x] `docs/06-macro-framework.md` — Macro transmission chain framework
- [x] `docs/07-risk-engine.md` — Risk Engine specification
- [x] `docs/08-architecture.md` — System architecture
- [x] `docs/09-ui-guidelines.md` — UI design philosophy
- [x] `docs/10-roadmap.md` — This document
- [x] `docs/11-development-guide.md` — Development rules
- [x] `docs/glossary.md` — Project glossary
- [x] `.github/copilot-instructions.md` — Copilot guidance
- [x] `README.md` — Repository introduction
- [x] `knowledge/` folder structure

### Acceptance Criteria
- All documents are written and reviewed.
- The philosophical foundation is clear.
- The technical direction is documented.
- Any contributor (human or AI) can read the docs and understand what this project is and is not.

---

## Phase 1 — Technical Setup

**Goal:** Establish the working development environment and project skeleton.

**Status:** Not Started

### Deliverables

- [ ] Monorepo workspace configuration (`package.json`, `tsconfig.base.json`)
- [ ] `apps/api/` — Express server skeleton
- [ ] `apps/worker/` — BullMQ worker skeleton
- [ ] `apps/web/` — Angular 22 project scaffold
- [ ] `packages/risk-engine/` — Pure TypeScript package scaffold
- [ ] `packages/database/` — Prisma client package
- [ ] `packages/shared/` — Shared types package
- [ ] `prisma/schema.prisma` — Initial database schema
- [ ] `docker-compose.yml` — PostgreSQL, TimescaleDB, Redis
- [ ] CI/CD pipeline (basic)
- [ ] All unit test scaffolding

### Acceptance Criteria
- `docker-compose up` starts all services.
- All packages build without errors.
- Test frameworks are running.
- A basic health-check API endpoint responds.

---

## Phase 2 — Risk Engine

**Goal:** Implement the core Risk Engine business logic.

**Status:** Not Started

### Deliverables

- [ ] Indicator data model and registry
- [ ] Risk Score calculator
- [ ] Risk State machine
- [ ] Alert Rule engine
- [ ] Golden Signal detection
- [ ] Configuration loading (thresholds and weights from files)
- [ ] Full unit test coverage of all business logic
- [ ] Worker job: fetch, validate, run engine, persist

### Acceptance Criteria
- Risk Engine produces correct scores given test fixture data.
- State machine correctly transitions between all states.
- Golden Signal fires correctly given appropriate test input.
- All thresholds and weights are read from config — nothing hardcoded.
- Unit test coverage > 90% for risk-engine package.

---

## Phase 3 — Financial Medical Record UI

**Goal:** Build the Angular frontend — the Research Studio interface.

**Status:** Not Started

### Deliverables

- [ ] Application shell (routing, layout, theme)
- [ ] Dashboard — current diagnosis overview
- [ ] Vital Signs view — individual indicators
- [ ] Diagnosis view — current risk state and active alerts
- [ ] History view — time-series charts
- [ ] Thai language throughout
- [ ] Calm, minimal, warm visual design

### Acceptance Criteria
- Owner can open the app and immediately understand the current state of the financial system.
- All text is in Thai (with English technical terms where appropriate).
- No flashing elements, no urgent color palette, no news feed.
- Design review: does this feel like a quiet research room?

---

## Phase 4 — Knowledge System

**Goal:** Integrate the Living Knowledge System into the application.

**Status:** Not Started

### Deliverables

- [ ] Journal entry UI (create, view, browse by date)
- [ ] Reflection UI (longer form writing, categorized)
- [ ] Observation log UI
- [ ] Hypothesis tracker (create, update, mark as confirmed/revised/rejected)
- [ ] Case Study viewer
- [ ] Knowledge search
- [ ] Knowledge-to-diagnosis linkage (observations connected to specific dates/states)

### Acceptance Criteria
- Owner can write and retrieve journal entries associated with specific dates.
- Owner can view how their hypotheses have evolved over time.
- Case studies are accessible from within the diagnostic context.

---

## Phase 5 — Scenario Lab and Case Studies

**Goal:** Enable structured historical analysis and scenario exploration.

**Status:** Not Started

### Deliverables

- [ ] Historical episode library (2008, 2020, 2022 tightening cycle, etc.)
- [ ] Pattern comparison — current state vs. historical analogues
- [ ] Scenario explorer — "what if" analysis using configurable parameters
- [ ] Case study authoring tools
- [ ] Knowledge evolution timeline

### Acceptance Criteria
- Owner can compare current indicator configuration against historical crisis episodes.
- Scenario explorer allows the owner to test threshold sensitivity.
- Knowledge evolution timeline shows how owner's understanding has changed.

---

## Future Considerations (Unscoped)

These are ideas that may emerge from the owner's evolving understanding. They are not planned — they are noted for awareness:

- Multi-country diagnosis (not just US-centric)
- Sector-specific stress analysis
- Integration with personal investment records (for contextual awareness, not trading)
- Voice-to-journal entry capability
- Collaboration/sharing tools (if this ever moves beyond personal use)

---

*Last updated: 2026-06-27*
