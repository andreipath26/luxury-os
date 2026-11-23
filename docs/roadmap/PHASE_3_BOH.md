# Phase 3 — Kitchen Brigade, Butler Dispatch and KDS
Window: Months 7–9 (original target 2027-Q2; provisional). Goal: safe, legible order lifecycle and optional non-verbal pacing.

## Work
- Define ticket/item/course states, valid transitions, permissions, timestamps, correction and audit flows.
- Show FOH allergy context at relevant KDS items with acknowledgment and stale/missing-data indication.
- Build station routing, item timers, course pacing, hold/fire controls and pass overview; use KDS references for feature discovery.
- CRDT may synchronize data; a validated domain state machine must enforce workflow transitions.
- Prototype optional BLE haptics; measure delivery, acknowledgment, duplicates, misses and reconnects. KDS stays source of truth.
- Add butler dispatch, plating renders, BEO generation and labor/time tracking only after user and legal validation.
- Provide glove-friendly/high-contrast UI and manual fallback for device, battery or network failure.

## Exit evidence
Kitchen staff validate lifecycle, routing, allergy visibility and corrections. Invalid transitions rejected/audited; replay cannot regress tickets. Report haptic results per device/OS; missed haptics never hide KDS state. Recovery drill documented.

Gate: selected service workflow remains safe when wearables or connectivity fail.
