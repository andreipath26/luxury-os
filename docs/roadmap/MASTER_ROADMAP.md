# Luxury OS Master Roadmap

## Purpose and planning status
Local-first operations software for luxury hotels and fine-dining venues: FOH, BOH, cellar, supply and optional AI workflows.

Baseline: 2026-11-23. The 18-month sequence below is provisional, inherited from the original proposal, and is not a claim of implementation progress. Re-estimate after a design-partner pilot, capacity plan, vendor-access checks and architecture decisions.

## Product sequence
Prove one workflow at one design partner before broadening scope. Candidate first workflow: reservation/seat and allergy update reaches kitchen, survives a venue-network interruption, and remains auditable. Validate with FOH and kitchen staff before locking MVP scope.

| Phase | Original window | Outcome |
|---|---|---|
| 1. Core and pilot foundation | Months 1–3, 2026-Q4 | Architecture, local data/event core, security model, UI foundation and pilot slice |
| 2. FOH and PMS | Months 4–6, 2027-Q1 | Host/floor workflow and one authorized PMS integration |
| 3. BOH and pacing | Months 7–9, 2027-Q2 | KDS lifecycle, course pacing, optional haptics and recovery |
| 4. Cellar and yield | Months 10–12, 2027-Q3 | Inventory, yield and costing with practical onboarding |
| 5. Supply and venue operations | Months 13–15, 2027-Q4 | Procurement, receiving, traceability and validated sensor workflows |
| 6. AI and multi-property | Months 16–18, 2028-Q1 | Human-supervised concierge/booking and enterprise capabilities |

Dates are targets only. Move a phase when its exit gate is unmet.

## Cross-phase release criteria
Each phase needs an owner, acceptance evidence, rollback plan and operational pilot.
- Correctness: no acknowledged critical event silently lost in defined power-cut/partition tests; valid, auditable state transitions; restore demonstrated.
- Latency: report p50/p95/p99 for local durable write, UI response and peer sync separately on named hardware/load. Keep sub-5 ms only for a precisely defined local operation; do not apply it to BLE, mesh sync or vendor APIs.
- Offline: define duration, queue limits, stale-data indicators, conflict policy and resynchronization. Critical allergy/order changes cannot silently overwrite.
- Usability: verify the 2-tap and 60pt touch-target goals on named devices with staff; record exceptions, errors and recovery.
- Security/privacy: threat model, enrollment/revocation, least privilege, audit, retention/deletion and incident/recovery procedures before real guest data.
- Operations: installation, monitoring, update/rollback, backup/restore, venue IT ownership and support escalation documented.

## Critical gates
- Before coding: ADRs for runtime (Rust-only is a candidate pending proof of concept), schema/event semantics, deployment topology, supported devices, privacy/security, vendor/regulatory discovery and reuse evaluation.
- Phase 1: pilot workflow demonstrated; no silent loss of acknowledged events; outage and restore drills pass.
- Phase 2: one supported PMS method and sandbox confirmed; reconciliation and human exception flow demonstrated.
- Phase 3: kitchen validates state machine/pacing; wearable failure cannot hide KDS state.
- Phase 4: inventory onboarding effort, stock accuracy and costing variance measured on representative data.
- Phase 5: sensor calibration, traceability and records export/recovery demonstrated; market-specific review complete.
- Phase 6: AI actions permission-checked and auditable, with consent and human fallback; cross-property sync privacy-reviewed.

Baseline numeric thresholds with the pilot before judging implementation. Record hardware, dataset, load and evidence.

## Phase plans and reuse register
- [Phase 1 — Core and pilot foundation](PHASE_1_CORE.md)
- [Phase 2 — FOH and PMS](PHASE_2_FOH.md)
- [Phase 3 — BOH and pacing](PHASE_3_BOH.md)
- [Phase 4 — Cellar and yield](PHASE_4_CELLAR.md)
- [Phase 5 — Supply and venue operations](PHASE_5_SUPPLY.md)
- [Phase 6 — AI and multi-property](PHASE_6_AI.md)
- [Prior art and reuse evaluation](PRIOR_ART_EVALUATION.md)

## Scope boundaries
French beachhead assumptions, target lists, competition, pricing, ARR and hiring assumptions belong in a sourced commercial plan, not engineering commitments. Avoid absolute promises such as 100% AI-handled inquiries or unrestricted global VIP-profile sync. Preserve consent, human escalation and property controls.

NF525, German TSE, PCI DSS and GDPR are not one platform-wide certification. Map obligations to product function, jurisdiction, operator and deployment model with qualified review. Resolve cash-register/payment scope before implementation.
