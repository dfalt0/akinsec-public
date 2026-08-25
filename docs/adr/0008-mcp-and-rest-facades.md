# ADR-0008: MCP for AI-to-SIEM, REST for the first-party UI

- **Status:** accepted
- **Date:** 2026

## Context

Agents need typed tools. The SPA needs predictable JSON for Discover,
Devices, and Config. Implementing SIEM twice (once for the model, once
for the UI) guarantees filter drift and a write the model can do that
the UI cannot audit — or the reverse.

## Decision

One **operations layer**. Two facades:

- **REST** — first-party workspace
- **MCP** (streamable HTTP) — bound to the signed-in user

MCP tools are the product catalog in
[agents-mcp-skills.md](../product/agents-mcp-skills.md). REST is
described conceptually (status, enable, stop, discover) without a
private route inventory.

## Consequences

- New SIEM capability ships to both facades or it is incomplete.
- Cloud Tools should add MCP adapters **and** a human UI on the same
  session id, not a chat-only toy wrapper.
- Session-bound MCP prevents “inspect as user X.”

## Related

[essay 04](../essays/04-mcp-usb-c-of-security-tools.md)
