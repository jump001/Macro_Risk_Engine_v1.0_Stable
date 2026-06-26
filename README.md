# Living Knowledge System

> A quiet personal research studio for understanding the global financial system.

---

## Why This Exists

The world produces an overwhelming amount of financial data, commentary, analysis, and noise every day. Most tools built for this world are designed to accelerate reaction — to surface more information, faster.

This project takes the opposite path.

This is a **Living Knowledge System** — a private, personal research environment where one mind can sit with the complexity of the global financial system and slowly, carefully, come to understand it.

It is not designed to help its owner trade.

It is not designed to predict markets.

It is not a noisy financial dashboard.

It is a quiet place where understanding grows over time.

---

## What This System Does

### Macro Risk Engine — The Analytical Core

The system uses a **Macro Risk Engine** to produce a daily diagnosis of the global financial system. The engine:

- Monitors key macro indicators (SOFR, DXY, US30Y, Gold, Volatility, Treasury Auction results).
- Calculates a **Risk Score** and assigns a **Risk State** (Healthy, Watch, Fragile, Pre-Crisis, Critical, Deleveraging).
- Evaluates **Alert Rules** to detect specific stress configurations.
- Identifies the **Golden Signal** — a multi-indicator condition historically associated with systemic stress.

### Financial Medical Record — The Diagnostic Framework

The global financial system is treated as a **patient with vital signs**. The application presents the state of the system through a medical lens:

- Vital signs, not market data.
- Diagnosis, not predictions.
- Health states, not trading signals.

This metaphor is not decorative — it shapes how the owner thinks about what they are observing.

### Living Knowledge System — The Intellectual Infrastructure

Beyond the quantitative engine, the system provides space for the owner's own intellectual work:

- **Journals** — Dated personal reflections on the system's state.
- **Observations** — Short timestamped notices of notable conditions.
- **Reflections** — Deeper analytical writing.
- **Hypotheses** — Formally stated beliefs under testing.
- **Case Studies** — Historical analyses through this system's lens.

The knowledge grows over time. It is never deleted. It is the record of the owner's evolving understanding.

---

## The Conceptual Map

Understanding this system means understanding three metaphors:

**The Tree of Understanding** — The financial system as a tree. Soil (central banks), Roots (credit), Sap (liquidity), Trunk (global funding), Branches (capital flows), Leaves (asset markets). Do not chase the moving leaves. Understand the roots.

**The Financial Medical Record** — The financial system as a patient. Vital signs. Diagnosis. Treatment. Prognosis. The owner is the doctor, not the investor.

**The Research Studio** — The application as a quiet room. No news feed. No urgency. No noise. A space for thinking.

---

## Technology

- **Frontend:** Angular 22 (Signals-based state)
- **Backend:** Node 24 + Express + TypeScript
- **Database:** PostgreSQL + TimescaleDB
- **ORM:** Prisma
- **Queue:** BullMQ + Redis
- **Update Frequency:** Once per day (by design)

---

## Documentation

Start here:

| Document | Purpose |
|---|---|
| [docs/00-philosophy.md](docs/00-philosophy.md) | Why this project exists |
| [docs/01-manifesto.md](docs/01-manifesto.md) | The principles that govern it |
| [docs/02-living-knowledge-system.md](docs/02-living-knowledge-system.md) | The knowledge system concept |
| [docs/03-research-studio.md](docs/03-research-studio.md) | The UI philosophy |
| [docs/04-financial-medical-record.md](docs/04-financial-medical-record.md) | The medical metaphor |
| [docs/05-tree-of-understanding.md](docs/05-tree-of-understanding.md) | The tree metaphor |
| [docs/06-macro-framework.md](docs/06-macro-framework.md) | The macro transmission framework |
| [docs/07-risk-engine.md](docs/07-risk-engine.md) | The risk engine specification |
| [docs/08-architecture.md](docs/08-architecture.md) | System architecture |
| [docs/09-ui-guidelines.md](docs/09-ui-guidelines.md) | UI design guidelines |
| [docs/10-roadmap.md](docs/10-roadmap.md) | Development roadmap |
| [docs/11-development-guide.md](docs/11-development-guide.md) | Development rules |
| [docs/glossary.md](docs/glossary.md) | Project glossary |

---

## Getting Started (Development)

> **Note:** This project is currently in Phase 0 (Documentation Foundation). The development environment setup is part of Phase 1.

Prerequisites (planned):
- Docker and Docker Compose
- Node.js 24
- pnpm

```bash
# Clone and install dependencies
pnpm install

# Start development environment
docker-compose up -d

# Run database migrations
pnpm run migrate

# Start development servers
pnpm run dev
```

---

## Current Status

**Phase 0 — Foundation and Documentation** — In Progress

See [docs/10-roadmap.md](docs/10-roadmap.md) for the full development roadmap.

---

*Owner: Jirasak KK — Built for understanding, not for trading.*
