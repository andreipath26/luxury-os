### Phase 1 — Local-First Core, Edge Resilience, Legal Shield, Dark OLED UI (Months 1–3)
- **Month 1:** Embedded SQLite/RxDB setup; P2P Wi-Fi 6E/BLE CRDT mesh engine.
- **Month 2:** Dual-redundant Mac Studio / NUC edge gateway server in Rust; hardware security binding (TPM 2.0 / Apple Secure Enclave).
- **Month 3:** Dark OLED UI token engine (`#000000`, 2-Tap rule, 60pt touch targets); French **NF525**, German **TSE**, **PCI-DSS v4.0** compliance isolation. Build 3-Tier Data Ingestion Engine foundation.

---

## Supplemental implementation guidance retained from the review

The following material supplements the exact chat roadmap above; the phase/month deliverables above remain the roadmap baseline.

### Phase 1 — Core and Pilot Foundation
Window: Months 1–3 (original target 2026-Q4; rebaseline capacity). Goal: prove a narrow local-first workflow, not the full platform.

## Work
1. Validate reservation → seat → allergy update → kitchen visibility → acknowledgment with FOH and kitchen staff at a design partner.
2. Write ADRs for deployment topology, supported OS/devices, schema, event log, identity, offline/conflict semantics, backup/update and Rust-only vs Rust+C++ choice. Rust-only is a candidate default pending hardware/API proof.
3. Compare SQLite and RxDB for the chosen runtime; specify durable writes, IDs/idempotency, audit, migration and export.
4. Spike sync candidates in PRIOR_ART_EVALUATION.md. Keep BLE for haptic signaling unless evidence supports another use; use LAN/Wi-Fi or local IPC for state sync.
5. Threat model device enrollment/keys/revocation, role boundaries, encrypted transport/storage, retention/deletion and incident recovery. Hardware-backed protection is defense in depth; do not promise binaries self-destruct or cannot be extracted from memory.
6. Prototype dark OLED tokens, high-contrast kitchen mode, 2-tap goal and 60pt touch-target goal; test accessibility, gloves and low light.
7. Specify three-tier migration: direct API, structured import/export, assisted/manual migration; include validation, reconciliation, rollback and provenance.
8. Prove installation, forced restart, network outage, restore, update rollback and support runbook with venue IT/operator.

## Exit evidence
Staff demonstrate the workflow; report task completion/errors/feedback. Test power cuts, partitions/rejoin, duplicate/reordered events, stale client, disk full and restore. No acknowledged critical update is silently lost; conflicts are visible and resolved by domain rules. Report latency percentiles separately for local write, UI and peer sync. Demonstrate device revocation, synthetic-data deletion, UI/touch targets and operator recovery.

Gate: a venue can run the slice through interruption/recovery, understand stale/conflicting data and restore service. Re-plan if unmet.



## Technology fit update (supplementary; exact roadmap bullets above are unchanged)
- Resolve SQLite versus RxDB as a runtime-specific choice before building. For a first edge pilot, favor a local SQLite store owned by one service with an outbox; WAL does not provide peer replication and must not be shared over network filesystems.
- Limit CRDTs to data with safe merge semantics. Use versioned, authorized commands and explicit conflict handling for allergy, booking, order and ticket state.
- Start with managed venue LAN and one edge appliance. Define latency separately for durable local commit, UI, LAN propagation, vendor API and watch alert.
- Bluetooth Core 6.2 adds sub-millisecond connection intervals only on compatible endpoints; the earlier blanket BLE impossibility claim is outdated, but end-to-end smartwatch delivery still requires measurement.
- Prefer Rust for new native/core logic unless a concrete dependency requires C++. Treat TPM/Secure Enclave as key-protection mechanisms; define enrollment, revocation, signed updates and recovery.
- Rebaseline phase dates against the scaffold and pilot. The root README currently needs to state the same pre-alpha/no-application-code status as .github/README.md.
