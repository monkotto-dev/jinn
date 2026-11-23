# 🛍️ Delhi → Imphal Marketplace

**Discover more. Shop closer to home.**

A mobile-first, multi-vendor shopping and personalized sourcing platform connecting Delhi merchants with customers in Imphal through centralized warehouse fulfillment.

**🚧 Status:** Pre-implementation  
**⚙️ Stack:** Expo · React Native · TypeScript · Next.js · Firebase · Neon PostgreSQL

---

## 🌏 Overview

The marketplace bridges the gap between product availability in Delhi and shopping accessibility in Imphal. Merchants manage their own catalogs and deliver sold goods to a Delhi warehouse. The platform verifies, consolidates and dispatches orders to Imphal. Customers can also request products that are not listed and approve a personalized sourcing quotation.

> **Project status:** Architecture and product specification prepared. Phase 0 verification is next. Features below describe planned scope, not implemented functionality. The project name is a working identifier, not a final brand name.

## ✨ Core experiences

| Experience | Planned capabilities |
| :--- | :--- |
| 📱 Customer app | Guest browsing, search, categories, cart, checkout, order tracking and notifications |
| 🔎 Special sourcing | Photo or link upload, requirements, quotation approval and payment |
| 🏪 Merchant portal | Approved merchant accounts, product images, prices, inventory and fulfillment |
| 🎛️ Admin console | Product moderation, banners, recommendations, featured products and support |
| 📦 Warehouse | Receiving, inspection, consolidation, dispatch and discrepancy management |
| 🔔 Communication | Push notifications, persistent inbox and meaningful order milestones |

## 🏗️ Architecture

```text
📱 Customer app ─────────────┐
🏪 Merchant portal ──────────┼──→ TypeScript Commerce API
🎛️ Admin & warehouse console ─┘            │
                                          ├── Firebase Auth (identity verification)
                                          ├── Neon PostgreSQL
                                          ├── Object storage
                                          ├── Payment gateway
                                          └── Durable jobs → Push notifications
```

Firebase is the sole identity provider. Neon PostgreSQL is the commerce system of record. Privileged operations pass through the API; clients never receive database credentials. Neon Functions and Object Storage are candidates subject to Phase 0 runtime, quota and security verification.

| Layer | Selected direction |
| :--- | :--- |
| Mobile | Expo, React Native, Expo Router, TypeScript |
| Mobile UI | NativeWind, gluestack-ui, selective Expo UI; compatibility verified before pinning |
| Media and motion | expo-image, FlashList, Reanimated, Lottie, expo-linear-gradient |
| Web | Next.js, shadcn/ui, Tailwind CSS |
| Identity | Firebase Authentication |
| Backend | TypeScript API, Neon PostgreSQL, storage adapter |
| Notifications | expo-notifications, Expo Push Service, persistent inbox |
| Tooling | pnpm, GitHub, Google Antigravity |

## 🎨 Design system

**Plum Atelier** — Nordic Lagom minimalism with editorial commerce styling, generous whitespace, restrained gradients and almost-square corners.

| Token | Light | Dark |
| :--- | :--- | :--- |
| Background | `#F7F7FA` | `#151219` |
| Surface | `#FFFFFF` | `#242029` |
| Text | `#25232A` | `#F7F2F8` |
| Primary | `#49304E` | `#D8B3DB` |
| Border | `#E5E0E8` | `#39313F` |
| Hero gradient | `#49304E` → `#94618F` | `#392141` → `#704276` |

- Light, Dark and System appearance; System is the default.
- Predominantly 0–4 px corner radius; spacing scale of 4, 8, 12, 16, 24 and 32.
- Native splash with optional short Lottie reveal; three skippable Manipur–Delhi onboarding screens.
- One local shopping-bag placeholder, replaced by valid merchant imagery; admin controls promotional content through approved layouts.
- Accessible contrast, scalable text, reduced-motion support and consistent interaction states.

See [design specification](docs/design/DESIGN_SYSTEM.md) and [machine-readable tokens](packages/design-tokens/tokens.json).

## 🚚 Fulfillment journey

**🛒 Customer order → 🏪 Merchant suborders → 📦 Delhi warehouse → ✅ Verification & consolidation → 🚚 Dispatch to Imphal → 🏠 Customer delivery**

Special requests enter the same fulfillment pipeline after quotation approval and verified payment. Stock reservations, payment idempotency, item-level receiving and exception handling are explicit domain requirements.

## 🗺️ Roadmap

| Milestone | Deliverable | Status |
| :--- | :--- | :--- |
| Phase 0 | Compatibility, provider feasibility, security and workspace setup | Next |
| Phase 1 | Merchant upload → admin approval → customer discovery | Planned |
| Phase 2 | Multi-merchant checkout and sourcing quotations in sandbox | Planned |
| Phase 3 | Warehouse, shipment, notifications, refunds and pilot readiness | Planned |

Live payments and commercial launch require operational, legal, hosting and payment-provider approval. Free-first development does not imply zero-cost commercial operation.

## 📁 Repository structure

Target layout after scaffolding (the handover archive contains documentation and agent configuration, not runnable apps):

```text
.
├── AGENTS.md
├── .agents/
│   ├── rules/
│   └── skills/
├── apps/
│   ├── customer/          # Expo mobile app
│   └── console/           # Next.js role-based console
├── backend/
│   ├── api/
│   ├── db/
│   └── jobs/
├── packages/
│   ├── design-tokens/
│   ├── domain/
│   ├── api-client/
│   └── validation/
├── docs/
└── tests/
```

## 🚀 Getting started

1. Extract the handover into the repository root, preserving `.agents/`.
2. Open the root in Google Antigravity.
3. Read [AGENTS.md](AGENTS.md) and the [master specification](docs/handover/MASTER_SPEC.md).
4. Paste the [Antigravity kickoff prompt](docs/handover/ANTIGRAVITY_KICKOFF.md) into the agent.
5. Complete the [Phase 0 evidence checklist](docs/quality/PHASE_0_CHECKLIST.md) before scaffolding Phase 1.

Runtime installation and start commands must be documented after dependency versions and workspace scripts are verified. The `.env.example` is illustrative; never commit real secrets.

## 🤖 Agent workflow

**Specify → Plan → Implement → Verify → Review → Merge**

Workspace skills cover Plum Atelier design, marketplace commerce, warehouse fulfillment, safe database changes and quality release gates. Inspect official skill sources before installation. Work in bounded vertical slices; require test evidence before merging. Production deployments, destructive migrations and real payment operations require explicit approval.

## 📚 Documentation

| Document | Purpose |
| :--- | :--- |
| [Master specification](docs/handover/MASTER_SPEC.md) | Product requirements and scope |
| [Architecture](docs/architecture/ARCHITECTURE.md) | System boundaries |
| [Data model](docs/architecture/DATA_MODEL.md) | Domain entities and constraints |
| [State machines](docs/architecture/STATE_MACHINES.md) | Order and fulfillment transitions |
| [User flows](docs/flows/USER_FLOWS.md) | Customer and operator journeys |
| [Design system](docs/design/DESIGN_SYSTEM.md) | Visual standards |
| [Delivery plan](docs/roadmap/DELIVERY_PLAN.md) | Milestones and acceptance gates |
| [Skills and tools](docs/workspace/SKILLS_AND_TOOLS.md) | Agent setup |
| [Engineering workflow](docs/workflows/ENGINEERING_WORKFLOW.md) | Development process |
| [Test strategy](docs/quality/TEST_STRATEGY.md) | Verification requirements |
| [Notifications and support](docs/operations/NOTIFICATIONS_AND_SUPPORT.md) | Operational communication |
| [Open decisions](docs/decisions/OPEN_DECISIONS.md) | Business and provider approval gates |
| [Architecture decision](docs/decisions/ADR-0001-FOUNDATION.md) | Technical rationale |

## 🔐 Security and quality

Enforce role and merchant isolation, server-side price and stock validation, signed payment webhooks, idempotency, audit logs, secret management, isolated test environments and migration review. Validate both themes and real-device behavior. Do not accept live orders until the release gates pass.

## 📄 License

No open-source license has been selected for this project. Review third-party licenses and obtain owner approval before public distribution.

---

**Built around a simple idea: bring Delhi's choices closer to Imphal.**
