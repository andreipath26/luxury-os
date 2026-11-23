# Phase 1 — Core and Pilot Foundation
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
