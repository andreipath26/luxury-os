# Phase 2 — Front of House and PMS
Window: Months 4–6 (original target 2027-Q1; provisional). Goal: useful FOH workflow with one authorized PMS path.

## Work
- Host-stand/floor-pad reservation, party, table/seat map, arrival, preferences and allergy workflow.
- Define seat-aware CRM schema, provenance, access scope, audit, retention and deletion before real guest data.
- Build one PMS connector first. Investigate Oracle OPERA through OHIP where applicable; confirm product/version, partner access, sandbox, contract, scope, rate limits, pricing and support. Add Mews/Infor only after demand and access are confirmed.
- Implement reconciliation, idempotency, retry, sync status, conflict queue, manual correction and read-only/degraded fallback.
- Assess SevenRooms/Resy/OpenTable migration and live API paths separately; do not imply unsupported access.
- Validate VIP identity masking, role access and post-visit retention/deletion.
- Add valet, coat check and car retrieval only if discovery confirms they belong in the pilot.
- Assign edge-server operations: venue IT, managed service or project support, including escalation.

## Exit evidence
Authorized sandbox path; end-to-end create/update/reconcile with test data; no duplicate booking or silent divergence under failure/replay; staff usability results; privacy review.

Gate: one partner workflow operates in supported and degraded modes. No reverse engineering or unsupported API dependency.
