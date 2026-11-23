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
