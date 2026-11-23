# Prior Art and Reuse Evaluation

Leads below came from the shared DeepSeek chat. They are unverified leads, not endorsements, architecture decisions, licensing clearance or evidence of current availability. Verify source, maintenance, security, license, dependencies, vendor access and fit; benchmark before adopting. Record adopt/adapt/reference-only/reject decisions in an ADR.

| Lead | Possible time saving | Required diligence |
|---|---|---|
| Aether-Core / aether-zta / @nishantbhatte/aether-core | Local-first relay/CRDT and LAN discovery ideas | Verify identity/source, protocol, security, license, maturity, Rust/TS fit, offline semantics and workflow limits |
| Sietch | Offline replication/ACL approach | Verify source/license, maturity, post-quantum claims, transport, complexity and data-model fit |
| RxDB | Local-first DB/replication candidate | Compare runtime, replication, license, latency, recovery, migration and conflict behavior with SQLite |
| Yjs, Automerge, Gun, OrbitDB, Fluid Framework | CRDT/realtime prior art surfaced in search | Compare persistence, transport, authorization, maintenance, license and domain state-machine integration |
| Oracle OHIP | Official OPERA integration path to investigate | Confirm product/version, partner approval, sandbox, contract, API scopes, pricing and support |
| SevenRooms/PolyAI voice API | Voice booking integration/pattern lead | Verify official/current API, authorization, terms, processing and booking permissions |
| dev-3bdulrahman/kds (Laravel) | KDS scope reference: station routing, timers, lifecycle | Inspect source/license; reference behavior unless stack/quality justify reuse |
| URY on ERPNext (navariltd/ury) | POS/KDS/table/course/recipe/offline feature reference | Inspect source/license, deployment assumptions, activity; verify claims |
| SambaPOS-3 | Touch ergonomics and order-flow reference | Study ticket entry, state transitions and degraded mode; no assumed dependency |

## Search findings and remaining searches
Broad “Restaurant” searches mainly surfaced tutorials, templates and marketing sites; search by technical primitive/workflow, not star count. The chat judged chayxana/Restaurant-App a cloud-microservices contrast, not a local-first reuse choice. It also excluded generic web templates, tutorial repos, taxi super-app, unrelated projects, limited wine-cellar plugins and unrelated PMS samples as poor fits.

Still investigate: wine cellar inventory/location; cold-chain sensors/calibration/offline buffer; HACCP/food-safety records/export; wearable/BLE alerting. Add only source-reviewed results. No claim that the open-source landscape is empty should be treated as market proof based on broad searches.

## Checklist
Does cited source exist and match description? Compatible license for proprietary distribution/modification? Maintained and secure? Works on-prem/offline? Supports auth, tenant isolation, audit, retention/export? Preserves allergy and KDS invariants? Measured time saved vs integration/fork/operations cost? What if source/vendor disappears? Record evidence and decision; this register adopts nothing.
