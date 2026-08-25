# ADR-0018: Selective upstream sync

- **Status:** accepted
- **Date:** 2026

## Context

LibreChat moves quickly (agents, MCP, CVEs). A freeze-fork dies. A
wholesale merge overwrites AkinSec workspace chrome, tenancy, and
provisioning. Locize/community i18n automation and upstream branding
CI are high-churn and low-value for this product.

## Decision

Port **selectively**:

- Security fixes (including CVEs)
- Authz / tenancy-relevant fixes
- MCP client/server fixes
- Billing idempotency fixes

Skip: Locize/community i18n automation, upstream branding, CI that
assumes the LibreChat org.

Preserve AkinSec surfaces via a manifest (~120 paths in the private
tree — **not listed here**). Lineage: v0.8.6 era; in-tree reported as
v0.8.7 during a 2026 sync.

## Consequences

- Requires engineering time every upstream release.
- Public tracking fork may lag; private overlay is the source of truth.
- Docs must not copy LibreChat’s entire feature list as if AkinSec
  invented it.

## Related

[ADR-0001](0001-librechat-as-upstream.md) ·
[upstream-librechat.md](../architecture/upstream-librechat.md)
