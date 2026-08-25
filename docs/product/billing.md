# Billing

**Status: Partial.** An entitlement **hook** exists for Security Engine.
A payment processor is **not shipped**. Do not say subscriptions are live.

## What exists (shipped as a hook)

- Entitlement flag for Security Engine
- Enforcement switch on the provisioner so billing can gate creates
  later **without rewriting** async resume/lock logic

Marketing prices on [akinsec.com/Pricing](https://akinsec.com/Pricing)
are a **commercial** surface. They are not evidence that card charges
already run through AskAkin.

## What does not exist

- Stripe (or other) subscription capture in the product
- Metered Cloud Tools hours
- Seat invoices as an implemented billing engine

## Direction (**Proposed**)

- Org-shared stacks + seat RBAC (viewer / analyst / admin)
- Cloud Tools SKUs with idle sleep, disk quotas, GPU add-on
- Phase 6 of the labs RFC: org sharing + RBAC + per-hour meters

See [cost-model.md](../operations/cost-model.md) (design estimates only)
and [cloud-tools/phases.md](../cloud-tools/phases.md).

## Abuse control even without payments

Provisioning still has **locks**, **attempt caps**, and **one stack per
principal** in v1. Cost abuse is a threat even when billing is a hook.
[threat-model.md](../security/threat-model.md).
