# Consolidated Roadmap (Phases 1–6, 18 Months)

2026-Q4 2027-Q1 2027-Q2 2027-Q3 2027-Q4 2028-Q1
│ │ │ │ │ │
▼ ▼ ▼ ▼ ▼ ▼
[PHASE 1] ──► [PHASE 2] ──► [PHASE 3] ──► [PHASE 4] ──► [PHASE 5] ──► [PHASE 6]
Local mesh, Palace FOH, BOH brigade, Cellar, yields Supply chain, AI co-pilot,
edge shield, PMS sync, PDR & butler & micro-cost IoT & A2A gateway,
Dark OLED UI spatial map, in-suite engine & 3D MICHELIN Key global scale
& ingestion data ingestion dispatch & KDS bin visuals QA auditing & voice AI UX
core (SevenRooms, UX plating dashboards
Resy) guides

### Phase 1 — Local-First Core, Edge Resilience, Legal Shield, Dark OLED UI (Months 1–3)
- **Month 1:** Embedded SQLite/RxDB setup; P2P Wi-Fi 6E/BLE CRDT mesh engine.
- **Month 2:** Dual-redundant Mac Studio / NUC edge gateway server in Rust; hardware security binding (TPM 2.0 / Apple Secure Enclave).
- **Month 3:** Dark OLED UI token engine (`#000000`, 2-Tap rule, 60pt touch targets); French **NF525**, German **TSE**, **PCI-DSS v4.0** compliance isolation. Build 3-Tier Data Ingestion Engine foundation.

### Phase 2 — Front-of-House, Palace PMS, Spatial UX, Vendor Ingestion (Months 4–6)
- **Month 4:** Bi-directional PMS connectors (Oracle OPERA, Mews, Infor); spatial radial floor map; seat-aware CRM allocation.
- **Month 5:** Role-based VIP identity obfuscation; ephemeral post-visit GDPR purging; SevenRooms/Resy/OpenTable API migration connectors.
- **Month 6:** Valet arrival synchronization, digital coat-check, automated car retrieval dispatch.

### Phase 3 — Kitchen Brigade, Butler Dispatch, KDS UX, Labor Compliance (Months 7–9)
- **Month 7:** Non-verbal Course Hold & Fire countdown matrix; BLE haptic smartwatch alerts (*1 Pulse: Fired; 2 Taps: Sommelier; 3 Pulses: VIP*).
- **Month 8:** Penthouse/Villa In-Suite Butler Dispatch; high-contrast KDS with glove-friendly drivers; 3D plating render popups.
- **Month 9:** EU Working Time directive time-card and stagiaire hour enforcement; automated BEO event builder.

### Phase 4 — Sommelier Cellar, Precision Yields, Micro-Costs (Months 10–12)
- **Month 10:** 3D Cellar Bin visual finder (*Bin 42, Shelf B, Bottle 3*); vintage auto-substitution; Coravin Argon cartridge accounting.
- **Month 11:** Gram-level trim loss accounting (caviar, truffles, Wagyu); IoT dry-aging logs; non-alcoholic fermentation ledger.
- **Month 12:** Kitchen waste scale telemetry; sommelier flight builder; guest digital tasting journals.

### Phase 5 — Supply Chain, IoT Cold-Chain, MICHELIN Key Compliance (Months 13–15)
- **Month 13:** Reservation-driven par-level procurement; FEFO dispatch; OCR supplier invoice parsing.
- **Month 14:** Live GPS tracking for air-freighted luxury imports; instant mobile-bank payouts for local foragers and small organic farms.
- **Month 15:** Continuous MICHELIN Key QA Audit Tracker; Bluetooth HACCP thermal probe logging; predictive appliance failure diagnostics.

### Phase 6 — Autonomous AI, A2A Agentic Gateway, Global Scale (Months 16–18)
- **Month 16:** Multi-lingual autonomous voice AI concierge (20+ languages); Agent-to-Agent (A2A) booking gateway.
- **Month 17:** Generative Engine Optimization (GEO) metadata stream; post-shift executive debrief summaries; contribution margin matrixing.
- **Month 18:** Global multi-property VIP profile sync; multi-currency enterprise consolidation.

## Open Technical Questions (Must Resolve Before Code)

These are unresolved and block clean implementation. Decide and record in `docs/`.

### 6.1 Rust-only or Rust + C++?
Section 1.1 of the master spec describes a C++/Rust native core. Mixing both in a security-critical engine adds two toolchains, two FFI layers, and two memory-safety stories for no clear gain. **Recommendation: Rust-only.** Rust can deliver everything the spec describes (TPM/Secure Enclave binding, CRDT mesh, sub-5ms hot path). Resolve before any native code is committed.

### 6.2 BLE cannot deliver sub-5ms state sync
BLE minimum connection interval is ~7.5 ms. The "sub-5ms latency" principle is achievable over Wi-Fi 6E and on-device local writes, but **not** over BLE. **Resolution:** BLE is for haptic alerts only. All state sync runs over Wi-Fi 6E or local IPC.

---

## Supplemental planning guidance retained from the review

The following material is retained from the prior roadmap review. It supplements the exact chat roadmap above and does not replace, shorten, or redefine its phase/month deliverables.

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

