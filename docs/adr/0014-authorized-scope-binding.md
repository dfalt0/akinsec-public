# ADR-0014: Authorized-scope binding for offensive-capable tools

- **Status:** proposed
- **Date:** 2026

## Context

ZAP, Burp-class proxies, Nuclei-class scanners, and RE tools can be
pointed at **anyone**. A SaaS that hosts them without a scope object is
a botnet with invoices.

## Decision

Every Cloud Tools session binds to an **asset inventory** the tenant
declared: CIDRs, domains, uploaded binaries, uploaded pcaps, staging
URLs they own. **Default deny** egress. Attempts to reach off-scope
targets fail at the broker. Product ToS forbid third-party attacks.
Kill switch ends the session.

SIEM MCP in v1 is already scoped by **which engine the user owns**.
Labs must be similarly bound — more strictly, because the tool can
initiate outbound traffic.

## Consequences

- Scope is a **control-plane object**, not a prompt instruction
  ([essay 09](../essays/09-authorized-scope-control-plane.md)).
- “Continuous red team” if ever offered is a **separate engagement
  mode** with contracts and humans — never unsolicited third parties.
- Prompt injection cannot be the only control ([ADR-0016](0016-ai-copilot-hitl.md)).

## Related

[authorized-use.md](../security/authorized-use.md)
