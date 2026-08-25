# Responsible AI

**Status: Shipped** principles for SIEM agents; **Proposed** HITL UX
for labs.

AskAkin is a **copilot**. It is not an autonomous SOC and not an
autonomous attacker. [ADR-0016](../adr/0016-ai-copilot-hitl.md).

## Rules that are product, not slogans

1. **Never invent SIEM data.** No fake agents, alerts, or CVEs.
2. **Unprovisioned engine → onboarding**, not a hallucinated dashboard.
3. **BYOK.** Customer chooses providers and allowlists. AkinSec does
   not require a single hosted model.
4. **Tool output is untrusted.** It is data, not instructions to disable
   scope or exfiltrate tokens.
5. **Writes are narrow.** v1: single-target, audited. Bulk and
   fire-and-forget response are out of scope.
6. **No secret material in the prompt furniture.** Gateway tokens and
   provider credentials stay out of chat, traces, and HITL payloads.

## HITL

v1 restarts do not all wait for a click (honest). Approval cards for
dangerous actions are the **direction**, especially for Cloud Tools
active scans. [essay 06](../essays/06-hitl-restart-agents.md).

## What we will not build

An agent that autonomously exploits third-party systems. Authorized
offensive testing, if ever offered, is a **separate engagement mode**
with contracts, scope, and humans.

## Traces

Optional OpenTelemetry / Langfuse-style fanout must remain
**tenant-aware** and optional. Observability is not a reason to ship
prompts containing secrets to a third party by default.
[observability.md](../architecture/observability.md).
