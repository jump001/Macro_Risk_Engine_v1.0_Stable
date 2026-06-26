# UI Guidelines

> The interface is not a financial terminal. It is a quiet research room.

---

## Design Philosophy

Every UI decision must serve one purpose: helping the owner understand the world more clearly, in a state of calm focus.

The design philosophy can be summarized in three words: **Zen. Minimal. Calm.**

---

## Core Design Principles

### 1. Zen
The interface should create mental stillness. Clutter creates anxiety. Space creates clarity. Every element on the screen must earn its place. If a piece of information does not help the owner understand the system's state, it should not be on the screen.

### 2. Minimal
Less is more. One piece of information understood deeply is worth more than ten pieces of information skimmed. The interface should resist the temptation to display everything available. It should display what is currently most relevant to understanding.

### 3. Calm
Urgency is the enemy of understanding. The interface must not create urgency where urgency is not warranted. Color, typography, layout, and interaction design all work together to communicate: *"You are in a safe space. Think carefully. There is no rush."*

---

## Visual Design

### Color Palette
**Warm neutral tones.** Not the aggressive greens and reds of financial terminals. Not the clinical blues of corporate dashboards.

Colors should evoke:
- Warm paper, aged parchment.
- Natural wood and stone.
- Morning light in a quiet room.
- The covers of well-used research books.

State colors (for health indicators) should be:
- **Healthy:** Soft sage or muted warm green — not aggressive bright green.
- **Watch:** Warm amber — not alarming yellow.
- **Fragile:** Muted orange — not blaring orange.
- **Pre-Crisis:** Dusty rose or muted red — not emergency red.
- **Critical / Deleveraging:** Considered use of deep red or charcoal — present but not panicking.

### Typography
- Readable typefaces with generous line spacing.
- No font sizes fighting for attention.
- Thai script must be rendered with equal visual quality as Latin script.
- Headers should feel authoritative but not aggressive.
- Body text should feel like reading a calm research document.

### Spacing and Layout
- Generous whitespace. Space is not wasted — it is thinking room.
- Information grouped into clear, logical sections.
- No information density for its own sake.
- Comfortable reading width. Not edge-to-edge data tables.

---

## Language and Terminology

### Thai-First
The primary language of the interface is Thai. The owner's native language is Thai, and technical financial concepts are more deeply processed in one's primary language.

English terms are used where they are established conventions (SOFR, DXY, VIX) but are accompanied by Thai explanations.

### Medical and Tree Metaphors
The vocabulary of the interface should reflect the system's conceptual metaphors:

- **สุขภาพระบบ** (System Health) not **ระดับความเสี่ยง** (Risk Level).
- **การวินิจฉัย** (Diagnosis) not **สัญญาณเตือน** (Warning Signal).
- **สัญญาณชีพ** (Vital Signs) not **ตัวชี้วัด** (Indicators / KPIs).
- **ระบบภูมิคุ้มกัน** (Immune System) not **กลไกการแก้ไข** (Correction Mechanism).

These are not just translations — they are the conceptual vocabulary of the system.

---

## Interaction Design

### No Flashing Alerts
When the system identifies elevated risk, it does not flash, blink, or produce urgent visual effects. It presents the diagnosis clearly and calmly. The owner decides how to respond.

### No Push Notifications
The system does not push notifications to the owner. The owner visits the system when they want to review the diagnosis. The system is always waiting, never demanding.

### No News Feed
There is no scrollable feed of information. The owner navigates to specific analytical views, not a stream of updates.

### Deliberate Navigation
The owner navigates deliberately to the information they want. The interface does not auto-advance, auto-refresh, or draw the owner's attention to unrelated items. 

### Depth on Demand
The top-level view shows the essential summary. Deeper information is available on request — not displayed by default. The owner digs as deep as their current inquiry requires.

---

## What This Interface Is NOT

| Avoid | Why |
|---|---|
| Flashing alerts | Creates panic, not understanding |
| Real-time tickers | Encourages micro-reaction |
| Financial terminal density | Overwhelms cognition |
| Red/green color dominance | Conditions reflexive emotional response |
| Social feed patterns | Creates urgency and distraction |
| Trading terminal aesthetics | Wrong mental model entirely |
| Aggressive notifications | Interrupts reflective thinking |

---

## The Screen as a Room

Think of each screen as a room in a research library.

- The **Dashboard** is the reading room — where you get a calm overview.
- The **Diagnosis view** is the consultation room — where you examine the current state carefully.
- The **Indicators view** is the instrument room — where you examine individual vital signs.
- The **History view** is the archive — where you look back through time.
- The **Knowledge view** is the personal library — where you access journals, reflections, and case studies.

Each room has a character. Each room serves a purpose. You move between rooms deliberately.

---

## Implementation Notes

- Use Angular 22 with Angular Signals for all reactive state.
- No reactive clutter — do not create observables for things that are not event streams.
- Responsive design — the owner may use this on a laptop or desktop. Mobile is secondary.
- Accessibility: sufficient color contrast even for desaturated palette. Text remains readable.
- Performance: fast initial load. No unnecessary data fetching on page load.

---

*Last updated: 2026-06-27*
