# Risk Engine

> The analytical core that translates raw macro data into structured diagnostic signals.

---

## Purpose

The Risk Engine is the quantitative foundation of this system. It:

1. Collects daily macro indicator data.
2. Applies threshold rules and weighting to produce a Risk Score.
3. Maps the Risk Score to a Risk State.
4. Evaluates Alert Rules to identify Golden Signal conditions.
5. Outputs a structured diagnosis for the owner to review.

The Risk Engine does not predict. It diagnoses. It characterizes the current state of the financial system based on observable evidence.

---

## Risk Score

The Risk Score is a composite numerical measure (0–100) representing the current level of systemic stress in the global financial system.

- **0–20:** Healthy
- **21–40:** Watch
- **41–60:** Fragile
- **61–75:** Pre-Crisis
- **76–90:** Critical
- **91–100:** Deleveraging

Scores are calculated from weighted indicator readings. Weights are configurable in `/config/risk-score/weights.json`. Thresholds are configurable in `/config/thresholds/default-thresholds.json`.

**No threshold or weight is hardcoded in application logic.** All are externally configurable.

---

## Risk States

### Primary Risk States

| State | Risk Score Range | Description |
|---|---|---|
| `HEALTHY` | 0–20 | All indicators within normal ranges. System functioning as expected. |
| `WATCH` | 21–40 | One or more indicators showing mild elevation. Monitor closely. |
| `FRAGILE` | 41–60 | Multiple indicators elevated. System under strain. Risk accumulating. |
| `PRE_CRISIS` | 61–75 | Significant multi-indicator stress. Pattern consistent with pre-crisis conditions. |
| `CRITICAL` | 76–90 | Acute systemic stress. System in or approaching an acute event. |
| `DELEVERAGING` | 91–100 | Forced position unwinding in progress. Cascade dynamics possible. |

### Macro Cycle States

The Risk Engine also maintains macro cycle context alongside the primary risk state:

| State | Description |
|---|---|
| `NORMAL` | Stable macro environment. Growth sustainable. |
| `LATE_CYCLE` | Signs of late-cycle dynamics — rising rates, tightening financial conditions. |
| `FRAGILE` | Financial conditions fragile. Vulnerable to external shock. |
| `PRE_CRISIS` | Pre-crisis configuration across multiple macro dimensions. |
| `ACCELERATION_DELEVERAGING_RISK` | Deleveraging dynamics beginning to accelerate. |
| `PRE_DELEVERAGING_ACCELERATION_PHASE` | System approaching the threshold where deleveraging becomes self-reinforcing. |

---

## Key Indicators

Each indicator is a vital sign in the financial medical record:

| Indicator | Category | Medical Analogue | Stress Signal |
|---|---|---|---|
| SOFR | Funding / Liquidity | Blood Pressure | Elevated rate or spike |
| DXY | Dollar Strength | Oxygen Demand | Above 105, accelerating |
| US 30Y Treasury Yield | Long-term Rates | Heart Function | Breakout above key levels |
| Gold | Confidence | Fear Response | Sustained breakout |
| MOVE Index | Bond Volatility | Volatility Symptom | Above 130 |
| VIX | Equity Volatility | Volatility Symptom | Above 25 sustained |
| Treasury Auction Results | Sovereign Demand | Blood Chemistry | Weak bid-to-cover, tail |
| Yen / Dollar (USDJPY) | Carry Trade | Carry Stress | Rapid move above 155 |
| Credit Spreads | Credit Risk | Immune Response | Widening sharply |

Full indicator registry: `/config/indicators/indicator-registry.json`

---

## Golden Signal

The Golden Signal is a specific configuration of multiple indicators firing simultaneously. It represents a high-confidence systemic stress signal.

```
SOFR Stress (funding pressure elevated)
  + Treasury Auction Weak (sovereign demand faltering)
  + US 30Y Breakout (long-term rate stress)
  + Gold Breakout (confidence stress)
  + Volatility Rising (MOVE and/or VIX elevated)
```

When the Golden Signal fires, all five conditions are present simultaneously. This is not a casual event. Historically, configurations resembling the Golden Signal have preceded significant financial stress episodes.

The Golden Signal does not instruct the owner to act. It instructs the owner to pay careful attention and conduct a deep diagnostic review.

---

## Alert Rules

Alert Rules define specific threshold-crossing or pattern-matching conditions that produce structured notifications for the owner's review.

Alert Rules are:
- Defined in configuration (not hardcoded).
- Named and categorized by diagnostic significance.
- Associated with specific indicator thresholds.
- Grouped into composite rules (such as the Golden Signal) where multiple conditions must be met.

Alert Rules do not produce panic alerts in the UI. They produce calm diagnostic items in the owner's review queue.

---

## Diagnosis States

The Risk Engine outputs a structured diagnosis combining:

1. **Current Risk Score** — the numerical measure.
2. **Current Risk State** — the categorical health state.
3. **Current Macro Cycle State** — the cycle context.
4. **Active Alerts** — which specific rules are currently firing.
5. **Golden Signal Status** — whether the Golden Signal is active.
6. **Trend Direction** — is the score improving, stable, or deteriorating?
7. **Duration** — how long has the current state persisted?

The diagnosis is the owner's starting point for each daily review. It is a structured summary, not a conclusion. The owner interprets the diagnosis within the context of the Living Knowledge System.

---

## What the Risk Engine Does Not Do

- It does not predict future asset prices.
- It does not generate trading signals.
- It does not send push notifications demanding immediate action.
- It does not connect to real-time data feeds.
- It does not run continuously — it updates once per day.

---

## Technical Notes

- Risk Engine business logic lives in `/packages/risk-engine/`.
- All logic is pure TypeScript — no framework dependencies.
- All logic is fully unit testable.
- Configuration is externalized to `/config/`.
- State machine governs valid state transitions.

See [docs/08-architecture.md](./08-architecture.md) for full technical details.

---

*Last updated: 2026-06-27*
