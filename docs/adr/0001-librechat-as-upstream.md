# ADR-0001: LibreChat as upstream, not brand

- **Status:** accepted
- **Date:** 2026

## Context

AskAkin needed a serious multi-user chat surface: streaming, agents,
MCP client behavior, multi-provider routing, artifacts, files, and an
ACL lineage that is not a weekend prototype. LibreChat already is that
chassis. Rebuilding it would delay Security Engine and tenancy work
that is the actual product.

The risk of a fork is brand collapse: hiring managers and customers
see “ChatGPT clone” and miss the SIEM gateway, provisioner, and MCP
write audit.

## Decision

AkinSec treats LibreChat as an **upstream patch source**, not as the
product name. AskAkin remains a standalone security product. During
merges, a preserve-manifest of AkinSec-specific surfaces is kept.
Upstream branding and i18n automation that fight the AkinSec brand are
skipped. Security, authz, MCP, and billing-idempotency fixes are
ported. See [ADR-0018](0018-selective-upstream-sync.md).

Public [LibreChat-akinsec](https://github.com/dfalt0/LibreChat-akinsec)
may track upstream; it is **not** the private overlay.

## Consequences

- Credits must stay loud ([NOTICE.md](../../NOTICE.md)).
- Sync cost is real; selective port is the mitigation.
- Docs in this repo describe **AkinSec deltas**, not a copy of
  librechat.ai.
- Customers never log into “LibreChat” as the product brand.

## Related

[upstream-librechat.md](../architecture/upstream-librechat.md) ·
[essay 05](../essays/05-librechat-chassis-not-the-car.md)
