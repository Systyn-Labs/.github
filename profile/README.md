<div align="center">

<img src="https://raw.githubusercontent.com/systyn-labs/.github/main/profile/assets/systyn-banner-1280x640.png" alt="Systyn Labs — Dedicated virtual accounts, reconciled to the kobo" width="100%" />

# Systyn Labs

**We build the payment plumbing other teams shouldn't have to rebuild.**

`Σ DR = Σ CR`

</div>

---

## Who we are

Systyn Labs is a two-engineer infrastructure team building reusable payment primitives for Nigerian fintech. We believe the hard parts of money movement — provisioning, reconciliation, idempotency, edge-case lifecycle handling — should be solved once, rigorously, and consumed as an API.

Our work follows three rules:

1. **The ledger is the truth.** Every movement is a balanced double-entry posting. Balances are derived, never stored. Corrections are compensating entries — history is never rewritten.
2. **At-least-once in, exactly-once effect out.** Webhooks get duplicated, services cold-start, networks fail. We design so that none of it can double-post or lose a kobo.
3. **The API is the product.** Idempotency keys, cursor pagination, RFC 9457 errors, signed webhooks, and docs a stranger can integrate against in under 30 minutes.

## 🏗️ Current build — DevCareer × Nomba Hackathon 2026

**[VaultNUBAN](https://github.com/systyn-labs/vaultnuban)** — Dedicated Virtual Account infrastructure on [Nomba](https://nomba.com), built for the Infrastructure Track.

Every customer gets a persistent, identity-bound NUBAN. Every inbound transfer is reconciled exactly once — verified by webhook signature, deduplicated, posted to a double-entry ledger, and backstopped by a Transactions-API sweep that recovers anything missed during an outage. Renames, closures, KYC tier changes, and misdirected payments all have explicit, audited paths.

| | |
|---|---|
| 🌐 Live API | [vaultnuban.onrender.com](https://vaultnuban.onrender.com) |
| 🖥️ Dashboard | [vaultnuban-client.pages.dev](https://vaultnuban-client.pages.dev) |
| 📚 API docs | [vaultnuban-docs.pages.dev](https://vaultnuban-docs.pages.dev) |

### 🔑 Judge access

Sign in with any of the roles below to explore the platform from that perspective.

| Role | Sign-in URL | Email | Password |
|---|---|---|---|
| Admin Operations | [/admin/login](https://vaultnuban-client.pages.dev/admin/login) | `operator@systyn.io` | `Admin1234!` |
| Tenant Operations | [/login](https://vaultnuban-client.pages.dev/login) | `bisi@acme.io` | `Ops1234!` |
| Tenant Developer | [/login](https://vaultnuban-client.pages.dev/login) | `ada@acme.io` | `Dev1234!` |

**Stack:** Go (core service, webhook ingestor, reconciliation worker) · TypeScript (docs & dashboard) · PostgreSQL (Neon) · Redis (Upstash) · GitHub Actions CI

**The proof we care about most:** on every push, CI runs a 9-scenario reconciliation harness (`go test ./harness/...`) against an in-memory provider and ledger. The headline scenario drives **50 randomized transfers** through both delivery channels at once — a random subset delivered 2–3× to exercise duplicate-delivery idempotency, and a random "outage" subset dropped from the webhook stream and recovered by the Transactions-API sweep — asserting **every transfer posts exactly once**. Alongside it, targeted scenarios cover suspense routing (closed and unmatched accounts), reversals, and KYC tier-limit caps. Every scenario ends by asserting the double-entry invariant: Σ debits == Σ credits, to the kobo.

## The team

| | Focus |
|---|---|
| [@kellslte](https://github.com/kellslte) — Max | Core service: provisioning, ledger, reconciliation, developer API |
| [@cn-techlite](https://github.com/cn-techlite) - JP | Developer experience: docs site, OpenAPI, dashboard, test harness |

## Why "Systyn"?

Systems, tested. Our mark is two congruent interlocked blocks — rotate it 180° and it maps onto itself. That's double-entry bookkeeping made visible: every debit answered by its credit. The books always balance.

---

<div align="center">
<sub>Enugu, Nigeria · Built in the open · DevCareer × Nomba Hackathon 2026</sub>
</div>
