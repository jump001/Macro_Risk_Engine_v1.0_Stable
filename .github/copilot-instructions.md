# Copilot Instructions for Living Knowledge System

---

## Before Writing Any Code

> Before writing any code, remember why this project exists.
>
> This project is a quiet place where its owner can understand the world more deeply.
>
> It must never become another noisy financial dashboard.

---

## Required Reading Order

Before making any code change or suggestion, consult these documents in order:

1. **[docs/00-philosophy.md](../docs/00-philosophy.md)** — Why this project exists. Read this first. Always.
2. **[docs/01-manifesto.md](../docs/01-manifesto.md)** — The principles that govern every decision.
3. **[docs/08-architecture.md](../docs/08-architecture.md)** — The technical architecture. Read this before writing any code.
4. **[docs/11-development-guide.md](../docs/11-development-guide.md)** — The rules for building this system.

If a proposed change conflicts with the philosophy or manifesto, the philosophy wins.

---

## What This Project Is

This is a **Living Knowledge System** — a quiet personal research studio for understanding the global financial system.

Its analytical core is the **Macro Risk Engine**.

Its diagnostic framework is the **Financial Medical Record** — the global financial system understood as a patient.

Its conceptual map is the **Tree of Understanding**.

---

## What This Project Is NOT

**Do not turn this into a trading dashboard.**

**Do not add noisy feeds or panic-style alerts.**

**Do not add real-time data streaming.**

**Do not add social media-style features.**

**Do not add AI prediction or market forecasting.**

If a feature would make this feel like Bloomberg Terminal, a financial news feed, or a trading platform — it does not belong here.

---

## Philosophy Constraints (Non-Negotiable)

### Preserve the Living Knowledge System Philosophy
Every feature must serve the owner's understanding. Information that does not deepen understanding is noise. Noise does not belong here.

### Protect the Intent Before Writing Code
Ask: *Does this help the owner understand the world more clearly?* If the answer is "it helps them react faster," that is not sufficient. Understanding is the goal, not reaction speed.

### Silence Is a Feature
When the financial system is healthy, the application should be calm and quiet. Do not add indicators, alerts, or features that fill silence with noise.

### Daily Update Only
This system updates once per day. Do not introduce real-time data, polling, or WebSocket connections. The daily cadence is a deliberate constraint that supports reflective thinking over reactive thinking.

### No Hardcoded Thresholds
All threshold values and weights must live in `/config/`. Never write numeric thresholds as constants in application code.

---

## Technical Constraints

### Angular 22 + Signals
Use Angular Signals for state management. Use RxJS only for genuine event streams or HTTP operations. Do not use RxJS as a default pattern.

### Risk Engine Is Pure
The `/packages/risk-engine/` package must remain framework-free. No Angular, no Express, no Prisma inside the risk engine. It receives data and returns results.

### Architecture Layers Must Be Respected
```
Web (Angular) → API (Express) → packages/ (Business Logic) → Database (Prisma)
```
Do not mix layers. The web layer does not contain business logic. The risk engine does not contain HTTP handling.

### Business Logic Must Be Testable
Every risk calculation, state transition, and alert rule must have a corresponding unit test. Coverage target: > 90% for `/packages/risk-engine/`.

---

## Vocabulary

Use the system's vocabulary consistently:

- **สุขภาพระบบ** (System Health) — not "Risk Level" or "Score"
- **การวินิจฉัย** (Diagnosis) — not "Alert" or "Warning"
- **สัญญาณชีพ** (Vital Signs) — not "KPIs" or "Metrics"
- **ระบบภูมิคุ้มกัน** (Financial Immune System) — not "Correction Mechanism"
- **The Tree** metaphor — Soil, Roots, Sap, Trunk, Branches, Leaves
- **Medical** metaphor — Patient, Vital Signs, Diagnosis, Treatment, Prognosis

---

## The Final Check

Before submitting any code change, ask:

1. Does this make the owner understand the world more clearly?
2. Does this feel like something that belongs in a quiet research room?
3. Does this create urgency, noise, or distraction?
4. Is this consistent with the Medical Record and Tree metaphors?
5. Is this consistent with the philosophy in `docs/00-philosophy.md`?

If any answer raises concern — stop. Return to the philosophy documents before proceeding.
