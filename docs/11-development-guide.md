# Development Guide

> Rules and practices for building this system correctly.

---

## Philosophy First

Before writing any code, read:

1. `docs/00-philosophy.md` — Why this exists.
2. `docs/01-manifesto.md` — What principles guide it.
3. `docs/08-architecture.md` — How it is structured.

Every code decision must be consistent with the project philosophy. If a feature or implementation approach conflicts with the philosophy, the philosophy wins.

---

## Documentation-First Development

Documentation precedes implementation.

Before writing a new feature:
1. Document what the feature is and why it belongs in this system.
2. Document how it fits the philosophical intent.
3. Document the data model and API changes required.
4. Write tests that describe the expected behavior.
5. Implement.

This order is not optional. Code written before understanding is documented tends to encode the wrong understanding permanently.

---

## Architecture Before Coding

Before implementing any system component:
1. Read the relevant section of `docs/08-architecture.md`.
2. Understand where the component lives in the architecture.
3. Confirm the component does not violate the layering rules (see below).

### Layering Rules

```
Web (Angular) → API (Express) → Packages (Business Logic)
                                      ↓
                               Database (Prisma)
```

- **Web** knows only about the API contract.
- **API** knows about packages and database.
- **Packages/risk-engine** knows nothing about HTTP, Angular, or the database schema.
- **Packages/risk-engine** receives data — it does not fetch data.

Violating these layers creates tight coupling that makes the system brittle and untestable.

---

## Protect Philosophy First

When a feature request arrives (from any source), evaluate it against these questions before implementation:

1. Does this make the owner *understand* better, or does it just add more information?
2. Does this feel like something that belongs in a quiet research room?
3. Does this create urgency, noise, or distraction?
4. Is this consistent with the Medical Record and Tree metaphors?

If the answer to question 1 is "just more information," or questions 2–4 raise concerns — stop and re-evaluate.

---

## Business Logic Must Be Pure and Testable

All risk engine business logic in `/packages/risk-engine/` must be:

- **Pure functions** where possible. Given the same inputs, always produce the same outputs.
- **Framework-independent.** No Angular, no Express, no Prisma inside the risk engine.
- **Fully unit-testable.** Every calculation, state transition, and alert rule must have corresponding unit tests.
- **Deterministic.** There must be no randomness or non-determinism in risk scoring.

This is not a convention — it is a constraint. The risk engine is the analytical heart of this system. It must be trustworthy.

---

## Thresholds Must Not Be Hardcoded

All threshold values, weights, and rule parameters must be externalized to configuration files in `/config/`.

```
/config/
├── indicators/indicator-registry.json   — Indicator metadata and sources
├── risk-score/weights.json              — Indicator weights for score calculation
└── thresholds/default-thresholds.json  — Threshold values for alert rules
```

**Never** write numeric thresholds as constants in application code.

**Why:** The owner's understanding of appropriate thresholds evolves. If thresholds are hardcoded, every adjustment requires a code change, a test run, and a deployment. If thresholds are in config files, they can be adjusted, reviewed, and tracked as knowledge artifacts.

---

## Angular Signals for UI State

Angular Signals are the primary state management mechanism for the Angular frontend.

Use Signals for:
- All component state.
- Shared application state (via signal-based services).
- Derived / computed values.

Use RxJS for:
- Event streams that are genuinely streams (e.g., user input debouncing).
- HTTP requests (Angular's `HttpClient` returns Observables).
- Cases where complex async composition genuinely benefits from observable operators.

**Do not** use RxJS as a default pattern for all state management. Signals are simpler, more readable, and sufficient for most cases.

---

## Daily Update Only

This system updates once per day. The architecture enforces this at the worker level.

Do not introduce:
- WebSocket connections for real-time data.
- Polling mechanisms in the frontend.
- Real-time data subscriptions.
- High-frequency background jobs.

If a future requirement seems to need real-time data, question whether it is consistent with the project philosophy before designing a solution.

---

## Testing Standards

### Unit Tests (`/tests/unit/`)
- All risk engine logic must have unit tests.
- Tests use fixture data from `/tests/fixtures/`.
- Target coverage: > 90% for `/packages/risk-engine/`.

### Integration Tests (`/tests/integration/`)
- API endpoint tests.
- Worker job tests with a test database.
- Run against Docker compose test environment.

### Test Naming
Test names must read as specifications:
```
✓ should return FRAGILE state when SOFR stress and DXY above threshold
✓ should fire Golden Signal when all five conditions are present
✓ should not transition from HEALTHY to CRITICAL without intermediate states
```

---

## Code Style

- TypeScript strict mode enabled.
- ESLint configured via workspace standard.
- No `any` types without explicit justification.
- No unused variables or imports.
- No magic numbers — all constants are named and explained.

---

## Commit Discipline

Commits should be:
- Atomic — one logical change per commit.
- Descriptive — the commit message explains *why*, not just *what*.
- Prefixed by type: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `config:`.

Example:
```
docs: add financial medical record framework
feat: add SOFR threshold evaluation to alert rules
config: raise US30Y breakout threshold from 4.8 to 5.0
```

---

## What Not to Build

A standing list of features that do not belong in this system:

- Real-time market data feeds.
- Trading signals or buy/sell recommendations.
- Social or sharing features.
- Push notification systems.
- Machine learning or AI prediction models.
- Automated trading integration.
- Public-facing web interface.

If any of these are proposed, return to `docs/00-philosophy.md` and `docs/01-manifesto.md` before responding.

---

*Last updated: 2026-06-27*
