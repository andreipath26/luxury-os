# Prior Art and Reuse Evaluation

This register captures leads, search terms and exclusions from the shared DeepSeek chat. All named products/repos are unverified leads, not endorsements, architecture decisions, licensing clearance or proof of current availability. Verify source, status, maintenance, security, licence, dependencies, vendor access and fit. Benchmark before adoption. Record adopt/adapt/reference-only/reject with evidence in an ADR.

## Candidate leads

| Lead | Potential use | Due diligence |
|---|---|---|
| Aether-Core / aether-zta / @nishantbhatte/aether-core | Local-first relay, CRDT, encryption and LAN-discovery ideas | Verify source/package identity, protocol, security, licence, maturity, Rust/TS fit, offline semantics and domain workflow constraints |
| Sietch | Offline replication/ACL approach | Verify source/licence, maturity, post-quantum claims, transport, complexity and data-model fit |
| RxDB; SQLite | Local database and replication candidates | Compare runtime, durability, replication, licence, latency, migration, recovery and conflict behavior |
| Yjs, Automerge, Gun, OrbitDB, Fluid Framework, ElectricSQL, Jazz, Ditto | Local-first/realtime prior art | Compare persistence, transport, auth, maintenance, licence, commercial terms and state-machine integration; Ditto is commercial |
| Oracle OHIP | OPERA PMS integration path | Confirm product/version, partner approval, sandbox, contract, scopes, costs, rate limits and support |
| Mews Connector API; Infor HMS API | Other PMS integration paths | Confirm official access and partner terms; no reverse engineering |
| SevenRooms/PolyAI Voice Agent API | Voice booking integration/pattern | Verify current official API, authorization, terms, data processing and booking write permissions |
| Rasa, Vapi, Bland AI, LiveKit Agents, Voiceflow | Voice pipeline/framework leads | Compare multilingual STT/LLM/TTS, tool calling, hosting, privacy, cost and fallback |
| Google A2A; MCP | Existing agent/tool protocol specifications | Verify current versions and fit; use established protocol where applicable rather than inventing one |
| dev-3bdulrahman/kds (Laravel); KitchenOwl; KDS variants | Station routing, item timers and ticket lifecycle references | Inspect source and licence; behavior reference unless stack/quality justify reuse |
| URY on ERPNext (navariltd/ury) | POS/KDS/table/course/recipe/offline feature reference | Verify source, licence, deployment assumptions, activity and claims |
| SambaPOS-3 | Touch ergonomics and order-flow reference | Study rapid ticket entry, state transitions and degraded mode; no assumed dependency |
| Home Assistant, ThingsBoard, Node-RED | Edge temperature/probe ingestion and HACCP flow leads | Check local operation, device support, auditability, calibration, export and licensing |
| Tesseract, PaddleOCR, docTR, Surya | Invoice/menu OCR candidates | Benchmark by supplier/document, language, table extraction, confidence and human correction |
| Winnow, Leanpath; smart-scale vendors | Waste measurement and scale integration | Commercial API availability, data ownership, costs and hardware support |
| Apicbase, MarginEdge, xtraCHEF | Recipe/BOM/yield costing references or integrations | Verify API, regional support, granularity, export and commercial terms |
| Generic QA/audit checklist apps | Offline audit forms, photos and evidence | Check offline sync, export, data ownership and configurable criteria |
| Adyen, Stripe Terminal | Payment SDKs / P2PE path | Confirm local/offline modes, supported devices and scope with payment provider; use provider SDK and do not build payment security from scratch |

## Focused search checklist from the chat

Search by technical primitive and workflow rather than broad “restaurant” queries. These exact phrases are starting points, not completed diligence.

### Priority 1 — biggest possible time savings
1. CRDT/local-first sync: “CRDT local-first sync”; “offline-first database CRDT”; “p2p mesh sync CRDT”; “mDNS LAN peer discovery”; inspect Yjs, Automerge, ElectricSQL, RxDB, Jazz, Ditto, Aether-Core and Sietch.
2. Hotel PMS: “Oracle OPERA Cloud API”; “OHIP”; “Oracle Hospitality Integration Platform”; “Mews API”; “Mews Connector API”; “Infor HMS API”; “hotel PMS open source”.
3. Wine/beverage: “wine cellar inventory management open source”; “beverage inventory API”; “BinWise”; “CellarTracker”; “Wine Owners”; “sommelier software”; “restaurant beverage costing”.
4. KDS: “kitchen display system open source”; “KDS restaurant github”; “restaurant order state machine”; “ticket routing kitchen”; inspect KitchenOwl, dev-3bdulrahman/kds and SambaPOS-3.

### Priority 2 — possible savings of weeks
5. Cold chain: “cold chain monitoring open source”; “IoT temperature sensor logging”; “Bluetooth temperature probe”; “HACCP temperature logging”; “walk-in cooler monitoring”; “ESP32 temperature sensor”.
6. Haptics: “BLE haptic wearable”; “smartwatch haptic API”; “Wear OS notification API”; “BLE GATT notification”; “watchOS haptic patterns”; “haptic pattern library”.
7. Voice booking: “voice AI booking API”; “conversational reservation agent”; “multi-lingual voice agent open source”; assess PolyAI, Rasa, Voiceflow, Vapi, Bland AI and LiveKit Agents.
8. Agent protocol: “A2A protocol”; “agent-to-agent”; “Google A2A”; “MCP”; “agent booking API”; “agentic commerce protocol”.
9. Invoice/menu OCR: “invoice OCR open source”; “document AI open source”; “menu parsing”; “wine list OCR”; compare Tesseract, PaddleOCR, docTR and Surya.
10. Waste scales: “smart scale API”; “kitchen waste tracking”; “food waste measurement”; “IoT scale integration”; inspect Winnow/Leanpath API availability.
11. Recipe/yield cost: “recipe costing software open source”; “yield management food”; “BOM food costing”; “gram-level costing”; inspect Apicbase, MarginEdge and xtraCHEF.
12. QA: “audit checklist open source”; “QA inspection app”; “hotel QA audit software”; “service standard checklist”; “compliance audit mobile”.

### Priority 3 — adjacent
13. “valet parking software”; “coat check app”; “concierge dispatch”.
14. “restaurant CRM open source”; “guest profile management”; “seat-level guest data”.
15. “dark OLED design system”; “amber on black UI”; “low-light UI kit”; “candlelight UI”.
16. “P2PE payments open source”; “PCI-DSS local payment SDK”; “Adyen local SDK”; “Stripe Terminal SDK”.

### Search workflow and keep criteria
- Suggested GitHub filters from the chat: “CRDT local-first stars:>100”; “kitchen display language:Rust”; “cold chain pushed:>2024-01-01”; “wine cellar topic:inventory”. Treat star count and recent commits as filters, not quality proof.
- Search Hacker News/Algolia for CRDT, local-first and cold chain; inspect awesome-local-first, awesome-crdt and awesome-restaurant-tech lists; use Product Hunt for commercial tools/APIs; inspect Open Food Facts and GS1 for ingredient/inventory data standards.
- Keep candidates that are maintained, API-accessible or embeddable, solve a primitive rather than duplicate the product, and have a licence/terms compatible with proprietary commercial distribution. Review copyleft obligations with counsel; do not assume all AGPL software is unusable.
- Measure actual integration time and behavior; verify source. A result from chat/search is not “confirmed” merely because it was described as official or suitable.

## Search findings and exclusions
Broad GitHub “Restaurant” searches surfaced tutorials, templates and marketing sites and were too noisy to establish market absence. The chat assessed chayxana/Restaurant-App as a cloud-microservices contrast, not local-first reuse. Generic web templates, teaching repos, taxi super-app, unrelated repositories, limited wine-cellar WordPress plugins and unrelated PMS samples were excluded as poor fits. SambaPOS-3 was kept for interface/state-flow study, not adoption.

Remaining areas to research include bottle-level cellar inventory, sensor calibration/offline buffering, HACCP records/export and haptic notification. No candidate is adopted by this register.


## Research findings and dispositions — 2026-11-23

These findings refine the earlier chat-derived leads. They do not amend the exact roadmap. See [Technology Fit Review](TECHNOLOGY_FIT_REVIEW.md) for full rationale and sources.

### Core and networking
- **SQLite — retain as a pilot candidate.** Suitable for a local edge store; WAL is host-local and is not a multi-device/network-filesystem sync mechanism. Pair with an explicit transactional outbox and sync protocol.
- **RxDB — conditional client-side candidate.** Appropriate only if TypeScript/browser/device clients need their own offline database. Select conflict handling deliberately; do not treat it as an automatic match for SQLite.
- **CRDT tools — narrow use only.** Yjs/Automerge are collaboration primitives, not the domain workflow or authorization layer. Do not auto-merge orders, allergies, payments, ticket lifecycle or stock counts.
- **Aether-Core — reference/experiment only.** Its linked repository describes a Python relay and states it is client-server, not peer-to-peer. Verify license, security, maintenance, recovery and runtime fit before reconsidering.
- **Sietch — unverified.** The exact package/repository behind the chat’s Yjs/libp2p/post-quantum description is not established; do not count it as a qualified candidate.
- **Bluetooth latency claim — update the technical understanding, not the preserved roadmap.** Bluetooth Core 6.2 adds a shorter-connection-interval feature down to 375 μs when supported by both endpoints. This is not proof of watch-level application latency; keep KDS authoritative and measure device/OS behavior.
- **Rust — preferred default for new core code unless a concrete SDK requires C++.** TPM/Secure Enclave protect platform-supported keys/operations; they do not make arbitrary binaries extraction-proof.
- **Edge HA — defer.** One appliance plus UPS, backups and tested replacement is a simpler baseline than an undefined dual-host design.

### Hospitality integrations and workflow software
- **OHIP, Mews Connector API and Infor HMS — qualify independently.** Confirm partner/property access, production approval, fees, API scope and version before scheduling. One design-partner adapter is the first useful deliverable.
- **SevenRooms/Resy/OpenTable — partner-gated reservation systems.** Do not infer public API access or treat them as equivalent to a hotel PMS.
- **Toast KDS — feature reference, not a dependency decision.** Station routing and course pacing are established functions; differentiation should focus on local-first operation, recovery and allergy/audit behavior.
- **BinWise — existing wine/beverage inventory alternative.** Test integration/import and staff workflow before rebuilding cellar inventory. Prefer searchable 2D bins and scanning before 3D navigation.
- **Aether/Sietch, KDS-for-Laravel, URY, KitchenOwl and SambaPOS — inspect selectively.** Treat as source/feature references until current maintenance, license, architecture and deployment fit are verified.

### Operations, safety and AI
- **HACCP — software supports operator evidence; it does not confer compliance.** Compare existing sensor/logging systems and verify calibration, corrective actions, export and offline mode.
- **MICHELIN Key QA — rename the concept in product language.** Keys are qualitative inspector awards, not a software compliance checklist; use configurable hospitality QA without implying endorsement.
- **Invoice OCR and waste measurement — buy/integrate before building.** Benchmark confidence, correction effort, accounting reconciliation and supplier-specific accuracy; use source-linked human review.
- **FEFO — only after lot and expiry capture is dependable.** Start with receiving, traceability, alerts and human override.
- **Payments/payouts — use authorized provider integrations.** Decide payment scope before NF525/TSE/PCI work; do not build payment rails or claim broad certification prematurely.
- **A2A — optional interoperability layer.** Implement a permissioned booking API and audit first; add agent-to-agent support only for a customer/partner requirement.
- **Voice AI — bounded pilot with disclosure and handoff.** Test real languages, noise, accents, booking correctness, consent, escalation and recovery before increasing language count or autonomy.
- **GEO — experiment only.** Keep standard SEO and useful content as baseline; measure referral/conversion rather than treating metadata hacks as a committed product feature.
- **VIP sync — privacy architecture gate.** Define purpose, retention, tenant isolation, access, residency and deletion propagation before cross-property profile sharing.

No candidate in this register is adopted by these findings. Record tested version/date, license, access terms, measured fit, integration effort and rationale in an ADR before adding a dependency.
