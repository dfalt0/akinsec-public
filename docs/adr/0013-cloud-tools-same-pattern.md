# ADR-0013: Cloud Tools follow the same isolation / gateway / MCP pattern as Security Engine

- **Status:** proposed
- **Date:** 2026

## Context

AkinSec already provisions heavy stateful security infrastructure per
customer and already connects agents to live tools via MCP. The naive
next step — “embed Wireshark in an iframe on a shared box” — throws
away the only hard-won pattern in the company.

## Decision

Cloud Tools **must** reuse:

- Isolated environment per session (project, namespace, or microVM)
- Authenticated broker (gateway analogue)
- MCP adapter with typed tools, timeouts, HITL flags
- Encrypted artifacts
- Idempotent provision (lock, resume, cancel, destroy)

Human GUI (remote desktop or native web UI) shares the **same session
id** as the broker. AI is not a screenshot wrapper.

This ADR does not ship labs. It constrains the RFC so alpha cannot
“just docker run Ghidra on the API host.”

## Consequences

- Alpha may still use the same PaaS as Security Engine
  ([isolation.md](../cloud-tools/isolation.md)); malware still needs
  microVMs.
- Proof that this is not vaporware is the **shipped** engine, not a
  slide.

## Related

[cloud-tools/README.md](../cloud-tools/README.md)
