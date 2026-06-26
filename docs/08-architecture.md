# System Architecture

> Technical foundation of the Living Knowledge System.

---

## Design Principles

The architecture reflects the project's philosophy:

- **Daily update only.** This is not a high-frequency system. Data flows once per day.
- **Simplicity over complexity.** Each component does one thing well.
- **Business logic is pure and portable.** The risk engine does not depend on the framework.
- **Configuration over hardcoding.** All thresholds, weights, and rules are externalized.
- **No real-time infrastructure.** No WebSocket servers, no streaming data pipelines.

---

## System Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                        Daily Update Cycle                        │
│                                                                  │
│  External Data Sources                                           │
│       │                                                          │
│       ▼                                                          │
│  Worker (BullMQ Job)                                             │
│       │  - Fetch raw data                                        │
│       │  - Validate and normalize                                │
│       │  - Run Risk Engine                                       │
│       │  - Persist results                                       │
│       │                                                          │
│       ▼                                                          │
│  PostgreSQL + TimescaleDB                                        │
│       │                                                          │
│       ▼                                                          │
│  API Server (Express)                                            │
│       │                                                          │
│       ▼                                                          │
│  Web Frontend (Angular)                                          │
│  The Research Studio                                             │
└─────────────────────────────────────────────────────────────────┘
```

---

## Technology Stack

### Frontend — Angular 22
- **Framework:** Angular 22
- **State Management:** Angular Signals
- **Reactivity:** RxJS (where genuinely needed — not as default)
- **Language:** TypeScript
- **Design Philosophy:** Calm, minimal, Thai-first UI

Angular Signals are the primary state management mechanism. RxJS is used only where event streams or complex async composition genuinely benefit from it — not as a default pattern for all state.

### Backend — Node 24 + Express
- **Runtime:** Node.js 24
- **Framework:** Express
- **Language:** TypeScript
- **Architecture:** REST API

The backend is intentionally straightforward. No GraphQL complexity. No microservices overhead. A clean Express REST API serving the Angular frontend.

### Database — PostgreSQL + TimescaleDB
- **Primary Database:** PostgreSQL
- **Time-Series Extension:** TimescaleDB
- **ORM:** Prisma

TimescaleDB extends PostgreSQL with efficient time-series storage and query capabilities. This is appropriate for the daily macro indicator data that accumulates over years. Prisma provides a type-safe database access layer.

### Queue / Worker — BullMQ + Redis
- **Queue:** BullMQ
- **Broker:** Redis
- **Worker:** Node.js background process

BullMQ manages the daily data update job. The worker process is triggered once per day. Redis is the BullMQ job broker. There is no real-time queue — only a scheduled daily job.

---

## Repository Structure

```
Macro-Risk-Engine/
├── apps/
│   ├── api/              — Express REST API server
│   ├── worker/           — BullMQ worker (daily update job)
│   └── web/              — Angular 22 frontend
│
├── packages/
│   ├── risk-engine/      — Pure business logic (no framework deps)
│   ├── database/         — Prisma client and DB utilities
│   └── shared/           — Shared TypeScript types and utilities
│
├── config/
│   ├── indicators/       — Indicator registry and metadata
│   ├── risk-score/       — Weighting configuration
│   └── thresholds/       — Threshold configuration
│
├── knowledge/            — Living Knowledge System artifacts
├── prisma/               — Prisma schema and migrations
├── scripts/              — Dev, setup, and migration scripts
├── docker/               — Docker service configs (nginx, postgres, redis)
├── docker-compose.yml    — Local development environment
└── docs/                 — All documentation
```

---

## Data Flow

### Daily Update (Once Per Day)

```
1. Scheduler triggers BullMQ job
2. Worker fetches raw data from external sources
3. Worker normalizes and validates data
4. Risk Engine calculates new Risk Score
5. Risk Engine evaluates Alert Rules
6. Risk Engine determines Risk State
7. Results persisted to PostgreSQL/TimescaleDB
8. API serves updated data on next request
```

There is no streaming, no WebSocket push, no real-time update. The owner visits the application once per day (or as needed) and reviews the latest diagnosis.

### API Endpoints (Read-Mostly)

The API is primarily read-only for the frontend. Write operations occur only through the worker job.

Core API resources:
- `/api/diagnosis/current` — Current risk score, state, and alerts
- `/api/indicators` — Latest indicator readings
- `/api/history` — Historical time-series data
- `/api/alerts` — Active and recent alerts

Full API specification: `docs/technical/03-api-spec.md`

---

## Security Principles

- **Input validation at all API boundaries.**
- **No sensitive data in frontend code.**
- **Environment variables for all secrets** (see `.env.example`).
- **Parameterized queries only** (Prisma enforces this).
- **No public endpoints** — this is a single-user personal system.

---

## What This Architecture Deliberately Avoids

- **No real-time data streaming.** Daily updates only.
- **No WebSocket server.** The owner refreshes manually.
- **No microservices.** Monorepo with clear package boundaries.
- **No GraphQL.** REST is simpler and sufficient.
- **No AI/ML pipeline.** Pure rule-based analysis.
- **No automated trading integration.** This is not a trading system.
- **No third-party analytics or telemetry.** This is a private personal system.

---

*Last updated: 2026-06-27*
