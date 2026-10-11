# Luxury OS

**The Unified Luxury & Palace OS** — a local-first operating system for 3- to 5-star palace hotels, 3-MICHELIN-Key properties, and world-class fine-dining venues.

> **Status: Pre-alpha.** This repository currently contains the monorepo skeleton only. No application code has been committed. See [Roadmap](#roadmap) for the build sequence.

---

## Table of Contents

- [Overview](#overview)
- [Design Principles](#design-principles)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Security](#security)
- [License](#license)

---

## Overview

Luxury hospitality operators today run a fragmented stack — a hotel PMS, a reservation CRM, a cellar manager, a back-office costing tool, and a KDS — stitched together with APIs and middleware. Guest allergies logged at the host stand don't reach the kitchen line. Wine inventory is reconciled after service, not during it. Course pacing is coordinated by shouting across the pass.

Luxury OS replaces that fragmentation with a **single native core**: one database, one event log, one real-time state machine spanning front-of-house, back-of-house, cellar, supply chain, and in-suite butler service.

The system is built **local-first**. All live service operations execute on-premises, on redundant edge gateways, over a peer-to-peer mesh — with no cloud dependency during service.

### Intended scope

- **Front of house:** seat-aware guest CRM, bi-directional palace PMS sync (Opera, Mews, Infor), valet and coat-check dispatch.
- **Back of house:** non-verbal haptic course pacing, in-suite butler dispatch, kitchen pass plating guides, stagiaire labor compliance.
- **Cellar & yield:** 3D bin mapping, Coravin argon overhead accounting, gram-level trim-loss costing.
- **Supply chain & compliance:** reservation-driven procurement, cold-chain IoT monitoring, HACCP logging, MICHELIN Key QA auditing.
- **AI & discovery:** multi-lingual voice concierge, Agent-to-Agent (A2A) booking gateway, generative engine optimization feeds.

---

## Design Principles

These constraints govern every architectural decision in this repository.

| Principle | Meaning |
|---|---|
| **Local-first** | 100% of live service executes on-premises. Cloud sync is asynchronous and non-blocking. |
| **Sub-5ms latency** | Transaction round-trips on-device must stay under 5 ms during live service. |
| **The 2-Tap Rule** | No in-service action requires more than 2 taps from the primary screen. |
| **Visual silence** | Dark OLED UI (`#000000` base, amber `#FFB000` and red `#E53935` accents) to eliminate glare in candle-lit rooms. |
| **Non-verbal pacing** | Haptic smartwatch alerts and KDS state replace spoken calls across the pass. |
| **Zero-trust by default** | mTLS 1.3 on every device; no inbound open ports; air-gapped operational fallback. |
| **Privacy by design** | Role-based obfuscation and post-visit ephemeral purging for VIP and diplomatic guests. |

---

## Repository Structure
luxury-os/
├── apps/ # Deployable surfaces (host stand, floor pad, KDS pass, dashboards)
├── packages/ # Shared libraries (core, UI tokens, compliance, integrations)
├── infrastructure/ # Edge gateway provisioning, IaC, deployment
├── tools/ # Build, migration, and developer tooling
├── tests/ # Cross-package and end-to-end test suites
├── docs/ # Architecture decision records, specifications, runbooks
└── .github/ # CI workflows, issue templates, security policy

Planned application surfaces:

| App | Role |
|---|---|
| `apps/host-stand` | Maître d' spatial floor canvas |
| `apps/floor-pad` | Waitstaff and sommelier mobile interface |
| `apps/kds-pass` | Kitchen display system for the pass and station lines |
| `apps/gm-dashboard` | Executive command center — pacing heatmap, margin tracking |
| `apps/back-office` | Procurement, costing, compliance, and configuration |

Planned core packages:

| Package | Purpose |
|---|---|
| `packages/core-native` | Rust/C++ native engine — CRDT mesh, event sourcing, haptic pacing |
| `packages/core` | TypeScript bindings and application-facing API |
| `packages/ui-tokens` | Dark OLED design system and the 2-Tap interaction primitives |
| `packages/compliance` | NF525, TSE, PCI-DSS v4.0, GDPR boundary logic |
| `packages/integrations` | PMS connectors (Opera, Mews, Infor) and data migration adapters |

> Directories listed above are planned. Consult the repository tree for what is currently scaffolded.

---

## Getting Started

### Prerequisites

- **Node.js** — version pinned in `.nvmrc`
- **pnpm** — workspace package manager
- **Rust toolchain** — required once `packages/core-native` lands

### Setup

# Clone the repository
git clone git@github.com:andreipath26/luxury-os.git
cd luxury-os

# Install the pinned Node version
nvm use

# Install dependencies
pnpm install

# Build all packages
pnpm build

# Run the test suite
pnpm test

Root scripts are orchestrated by Turborepo via turbo.json.


Roadmap

Development runs across six phases over an 18-month window.

Phase	Window	Focus
1	2026-Q4	Local-first core, edge resilience, hardware security, Dark OLED UI core
2	2027-Q1	Palace FOH, PMS sync, spatial floor canvas, one-handed mobile ergonomics
3	2027-Q2	Kitchen brigade, PDR and butler dispatch, KDS UX, labor compliance
4	2027-Q3	Sommelier cellar, precision yields, micro-cost engine, visual dashboards
5	2027-Q4	Supply chain, IoT cold-chain, logistics, MICHELIN Key QA auditing
6	2028-Q1	Autonomous AI co-pilot, A2A agent gateway, global enterprise scale

Full phase-by-phase specifications live in docs/.
Contributing

Please read CONTRIBUTING.md before opening a pull request. All contributors must sign the project's Contributor License Agreement and are bound by the CODE_OF_CONDUCT.md.
Security

Security issues must not be reported through public GitHub issues. See SECURITY.md for the disclosure process and the project's threat model.
License

See LICENSE for terms. All intellectual property rights in the codebase are assigned to the corporate entity; see CONTRIBUTING.md for the assignment terms.
