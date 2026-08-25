# ADR-0007: Async provision + resume, not a 30-second HTTP call

- **Status:** accepted
- **Date:** 2026

## Context

A Wazuh indexer (OpenSearch + security plugin) does not boot like a
static file server. Health waits are **minutes**. A synchronous
“create stack” request that holds a browser connection until ready
will time out, retry, and **double provision**.

Cloud projects also disappear (manual delete, PaaS recycle). Naive
create-always logic leaks money.

## Decision

Provisioning is **asynchronous** with an explicit state machine:
`idle` → `running` → `succeeded` | `failed`. Cancel returns toward
`idle`. Properties: atomic lock, resume-on-existing-id, stale-lock
recovery, attempt cap, deleted-project detection, indexer-first boot
order, poll until gateway health.

Do **not** create duplicate projects.

## Consequences

- UI is a poller, not a spinner that assumes 3 seconds.
- Attempt cap + lock are the v1 cost-abuse controls even before billing.
- Cloud Tools must copy resume/idempotency or it will spawn lab VMs
  on every refresh.

## Related

[provisioning.md](../architecture/provisioning.md) ·
[essay 02](../essays/02-provisioning-as-a-product.md)
