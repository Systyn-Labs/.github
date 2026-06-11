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
| 🌐 Live MVP | _coming soon — deployed on Render_ |
| 📚 API docs | _coming soon — OpenAPI + runnable collection_ |
| 🎬 Demo video | _coming soon (2–3 min)_ |
| 🔑 Judge access | Test credentials in the submission — or open an issue and we'll send a key |

**Stack:** Go (core service, webhook ingestor, reconciliation worker) · TypeScript (docs & dashboard) · PostgreSQL (Neon) · Redis (Upstash) · GitHub Actions CI

**The proof we care about most:** our CI runs a reconciliation harness on every push — 50 synthetic transfers with deliberately duplicated webhook deliveries and a simulated outage, asserting every transfer posts exactly once and the ledger balances to zero.

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
