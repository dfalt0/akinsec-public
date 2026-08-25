# ADR-0017: No Wazuh Dashboard exposure

- **Status:** accepted
- **Date:** 2026

## Context

Wazuh ships a Dashboard (Kibana-like). Exposing it would duplicate
AskAkin, bypass workspace ACL/MCP audit, and pull a second identity
story into production. It would also tempt operators to open indexer
admin from a browser.

## Decision

**AskAkin is the UI.** Discover, Devices, Threats, Ops, Cloud, Config
are first-party. The Dashboard is not a product surface.

## Consequences

- Feature gaps vs upstream Dashboard must be closed in AskAkin or
  accepted as v1 limits — not papered over with “just open Kibana.”
- Gateway allowlists stay small.
- Customers who insist on vendor UI are not the v1 ICP.

## Related

[workspace.md](../product/workspace.md)
