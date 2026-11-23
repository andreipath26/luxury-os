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
