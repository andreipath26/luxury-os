# Technology Fit Review — 2026-11-23

This review evaluates the exact six-phase, month-by-month roadmap preserved above against the shared DeepSeek chat, the current repository, and available primary product/technical documentation. It is supplementary research. It does not replace or edit the chat roadmap.

## Executive assessment

The product thesis is coherent: local operation, reliable handoffs between front-of-house and kitchen, and controlled handling of guest information. The present roadmap, however, schedules a distributed core, six operational product areas, many vendor integrations, multiple regulatory regimes, hardware and sensors, and autonomous AI in 18 months before a pilot or application implementation is evidenced.

The best next proof is one design-partner workflow: reservation/seat update → allergy update → kitchen visibility and acknowledgment → network interruption → recovery with an auditable outcome. Keep the broader roadmap intact, but gate breadth and vendor commitments on this proof.

## Repository state and execution risks

At review time the repository is a scaffold with planning documents and empty/placeholder app/package paths, not a working implementation. The root README’s “Phase 1 in progress” status conflicts with .github/README.md, which says no application code has been committed. docs/COMPLETE_MASTER_DOCUMENT.md is a placeholder asking for the missing 29-part master document. The planned path names in .github/README.md do not consistently match the actual tree. The contributor guide says pnpm while CI uses npm ci; no lockfile is present in the tree. CI also invokes build/test/lint/typecheck against empty package scaffolds and pins Trivy to a mutable master branch.

Before inviting contributors, align the status, package manager and lockfile, directory map, CI scope, license/CLA/IP wording, and security-contact placeholder. SECURITY.md points to an empty architecture document and states eBPF detection and tamper-triggered lockout without evidence that these controls exist. Label planned controls as goals and define an actual threat model before making security claims.

## Technology and product evaluation

| Choice or product | Assessment | Recommended disposition |
|---|---|---|
| SQLite | Good candidate for local persistence at the edge. WAL is designed for processes on the same host and does not work over a network filesystem. | Keep for a pilot if one local service owns writes. Use a transactional outbox and explicit sync. Do not share one database file across devices. |
| RxDB | Good option for a TypeScript client that needs local persistence and replication. It is a separate data abstraction and needs deliberate conflict handling. | Do not schedule “SQLite/RxDB” as if they were one choice. Select one persistence model per runtime after a small workflow spike. |
| CRDTs | Good for data with genuinely safe merge semantics, such as notes or drafts. Automatic merging is unsafe for allergies, bookings, ticket lifecycle, payments, and stock counts. | Use domain commands, version checks, valid transitions, idempotency, audit and visible conflicts for critical records. Evaluate Yjs or Automerge only for a specific collaborative editing need. |
| Aether-Core | The linked project describes a Python relay and explicitly says it is client-server rather than peer-to-peer; it is not a drop-in Rust hospitality domain core. | Reference or experiment only. Verify exact package, source, license, threat model, maintenance and recovery before adoption. |
| Sietch | The exact project behind the shared chat’s Yjs/libp2p/post-quantum database description could not be verified; same-name search results are ambiguous. | Do not count it as a candidate until its exact URL/package and claims are confirmed. |
| Wi-Fi 6E, BLE, mDNS | A managed venue LAN and local edge service are a simpler pilot topology than a custom P2P mesh. mDNS discovers peers; it is not a replication protocol. Bluetooth Core 6.2 adds Shorter Connection Intervals down to 375 microseconds when both endpoints support the feature, so the old blanket “BLE cannot be sub-5ms” claim is too broad. That does not prove smartwatch or end-to-end application latency. | Measure local durable commit, UI response, LAN propagation, vendor API round-trip, and watch alert/ack separately on named hardware. Keep haptics secondary and optional. |
| Rust and C++ | Rust-only is a reasonable default for new core logic with a TypeScript UI. Adding C++ creates FFI/build complexity without a named requirement. Rust alone is not a security guarantee. | Choose Rust unless a concrete SDK or driver requires C++; record the exception in an ADR. |
| Mac Studio / NUC redundancy | Two machines without leader fencing, consistent replication and tested failover are not high availability. The roadmap does not define these. | Start with one supportable appliance, UPS, backup/restore and replacement procedure. Add HA only when pilot downtime evidence justifies it. |
| TPM / Apple Secure Enclave | Useful for protecting device keys and cryptographic operations on supported hardware. Neither makes arbitrary binaries impossible to copy or inspect. | Specify enrollment, key lifecycle, attestation, revocation, signed updates and recovery. Avoid self-destructing/extraction-proof binary claims. |
| OPERA/OHIP, Mews, Infor | Real integration targets, but distinct partner paths, scopes and access gates. OHIP requires app/API registration and property approval; Mews production credentials follow certification; Infor has its own integration configuration. | Select the PMS at the design partner. Confirm sandbox, partner approval, fees, scopes and supported operations before promising any connector. Ship one narrow adapter first. |
| SevenRooms, Resy, OpenTable | Separate reservation/guest platforms, not interchangeable PMS APIs. API access should not be inferred from integration marketing. | Treat each as partner-gated. Define field-level source of truth, retries, idempotency, event gaps, deletion and human reconciliation before bi-directional writes. |
| Spatial floor map | A configurable 2D table/section map is practical. “Spatial radial map” is not a testable requirement yet. | Start with 2D canvas/SVG, table status, capacity and staff workflow tests. |
| Valet, coat check, car retrieval, butler dispatch | Useful only if a partner has a demonstrated gap; these add physical-service, liability and vendor workflow. Existing hotel operations products may already handle task dispatch. | Integrate existing systems or defer bespoke dispatch until a pilot confirms demand. |
| KDS and course pacing | Mature product category; common capabilities include stations, routing, timers and course firing. | Build only the venue-specific value: offline recovery, allergy provenance, audit and cross-surface state. Keep KDS as source of truth. |
| BLE smartwatch haptics | Plausible as a discreet secondary cue, but background execution, pairing, permissions, battery and hardware make delivery uncertain. | Alert + acknowledgment + escalation, with a visible non-haptic fallback. Never let a missed pulse hide KDS state. Test exact devices. |
| Cellar/bin mapping | Commercial tools such as BinWise already serve restaurant/hotel beverage inventory. 3D mapping adds data-entry and maintenance cost. | Compare integration/import first. Start with searchable 2D locations and barcode/mobile scanning; add 3D only if task testing proves it faster. |
| Coravin cartridge accounting | Consumable usage is trackable as inventory, but reviewed public materials do not establish a supported integration API. | Treat as a consumables ledger/manual input unless vendor access confirms an API. |
| Gram-costing and waste scales | Accurate costing depends on recipe units, batch yield, prep loss, portion weight and staff capture. Waste capture products already exist. | Validate the capture workflow on a small set of dishes; compare integrations such as Winnow/Leanpath before building sensors or vision. |
| Procurement, FEFO and invoice OCR | FEFO needs accurate lot and expiry capture. OCR needs human correction and reconciliation; it cannot be the accounting source of truth by itself. | Begin with receiving, supplier/lot/date records, review queue and manual override. Integrate accounting/AP systems where possible. |
| HACCP sensors and logging | EU hygiene rules place HACCP procedures on food operators. Software can record monitoring/evidence but cannot certify the operator as compliant. | Compare commercial probes/logging systems (for example JRI/Telsen) and integrate where useful. Test calibration, clock, offline buffering, corrective action and export. |
| MICHELIN Key QA | MICHELIN Keys are qualitative inspector awards based on five criteria, not a formal compliance checklist. | Use configurable hospitality/service QA language; do not imply MICHELIN endorsement or “Key compliance.” |
| NF525, German TSE, PCI DSS | Separate obligations whose scope depends on country, product functions, checkout and payment-data flow. France’s 2026 guidance permits either an accredited certificate or editor attestation for covered cash-register functions. | Decide whether Luxury OS records payments or integrates with a certified POS/payment provider. Map legal scope per module/country before scheduling compliance work. |
| A2A and MCP | A2A is an open agent-to-agent interoperability protocol; it does not authorize booking actions or supply PMS integrations. MCP is a tool/context interface, not a reason to add agents. | Build permissioned booking APIs and audit first. Add A2A only if customers or partner agents need interoperability. Use MCP only for a concrete internal/tooling need. |
| Voice AI, 20+ languages | Language count does not show booking correctness, noisy-room accuracy, accent coverage or safe handoff. Relevant EU AI Act transparency obligations apply from 2 August 2026. | Pilot a few demanded languages and bounded intents. Disclose AI interaction, require confirmation for consequential changes, measure success/escalation and provide a human fallback. |
| GEO metadata stream | Google’s current guidance says standard SEO quality practices continue to matter and many GEO “hacks” are unsupported. | Defer as a marketing experiment, measured through referral/conversion data and editorial review; not an engineering milestone. |
| VIP and multi-property sync | “Post-visit purging” is too blunt: data categories can have different purposes and retention requirements. Global sync adds tenant, residency, consent, access and deletion complexity. | Define purpose, lawful basis, retention by category, access, tenant isolation, subject rights and deletion propagation before importing real VIP data. |
| Multi-currency consolidation | Not just display formatting; requires defined accounting ownership, FX source/timing, rounding, reconciliation and audit. | Integrate with the finance/accounting source of truth and specify reconciliation before building consolidated reporting. |

## Suggested decision sequence

1. Rebaseline the dates against the actual scaffold and pilot access.
2. Secure one design partner and choose one supported PMS.
3. Define domain records and ownership: hotel stay, restaurant cover/table/seat, guest identity, order/check, allergy, and inventory are distinct entities.
4. Specify a local command/event path with idempotency, audit, retry, stale-data markers and human conflict resolution.
5. Build the smallest FOH → allergy → KDS slice and run interruption/recovery drills.
6. Measure actual latency and staff task completion before deciding on mesh, redundant hosts, 3D maps or haptics.
7. Only then expand by customer evidence; integrate commodity subsystems where a supported API and contract make integration cheaper than rebuilding.
8. Create ADRs and a decision register with source/date, version, license, access terms, deployment fit, measured behavior, integration effort and adopt/adapt/reference/reject decision.

## Primary references

- SQLite [WAL](https://www.sqlite.org/wal.html) and [synchronous/durability modes](https://sqlite.org/pragma.html)
- RxDB [replication](https://rxdb.info/replication.html); Yjs [offline persistence](https://docs.yjs.dev/getting-started/allowing-offline-editing); Automerge [sync concepts](https://automerge.org/docs/reference/concepts/)
- Aether-Core [repository](https://github.com/IronFighter23/aether-core)
- Bluetooth SIG [Core 6.2 shorter connection intervals](https://www.bluetooth.com/bluetooth-core-6-2-feature-overview/)
- Apple [Secure Enclave key protection](https://developer.apple.com/documentation/security/protecting-keys-with-the-secure-enclave)
- Oracle [OHIP documentation](https://docs.oracle.com/en/industries/hospitality/integration-platform/ohipu/c_preface.htm); Mews [authentication](https://docs.mews.com/connector-api/guidelines/authentication) and [certification](https://docs.mews.com/connector-api/your-journey/certification); SevenRooms [API docs](https://api-docs.sevenrooms.com/)
- Toast [kitchen configuration/course pacing](https://support.toasttab.com/en/article/Basic-Kitchen-Configuration); BinWise [hotel beverage management](https://home.binwise.com/hotel-beverage-inventory-management)
- EU [Regulation 852/2004](https://eur-lex.europa.eu/eli/reg/2004/852); MICHELIN [hotel selection criteria](https://guide.michelin.com/en/everything-to-know-hoteliers-hotel-selection)
- France [tax authority cash-register scope](https://www.impots.gouv.fr/professionnel/questions/quel-est-le-champ-dapplication-de-lobligation-de-detenir-un-logiciel-de); BOFiP [2026 update](https://bofip.impots.gouv.fr/bofip/10691-PGP.html/identifiant%3DBOI-TVA-DECLA-30-10-30-20260325)
- European Commission [AI Act Article 50 guidance](https://digital-strategy.ec.europa.eu/en/library/guidelines-transparency-obligations-providers-and-deployers-ai-systems); Google [AI search guidance](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide)
