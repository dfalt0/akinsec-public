# Observability

**Status: Partial.** Tracing is an **optional** deploy, not a claim that
every tenant is exported to a vendor by default.

## What exists

- Application logs on the control plane (must stay tenant-aware; no
  secret leakage — [secrets-model.md](secrets-model.md))
- Provisioning state machine (`idle` / `running` / `succeeded` /
  `failed`) as an operator signal
- Gateway health as liveness, not as a telemetry product
- Optional **OpenTelemetry / Langfuse-style** trace fanout for
  multi-tenant LLM traces

## Design constraints

| Constraint | Why |
|------------|-----|
| Tenant in the trace context | Cross-tenant debug is a defect |
| No secrets in spans | Gateway tokens and provider credentials are assets |
| Optional fanout | Not every deployment wants a third-party LLM observability SaaS |

## Conceptual SLO draft (not a production promise)

These are **design targets**, not published SLAs and not measured
public metrics.

| Signal | Draft intent |
|--------|----------------|
| Provision success without duplicate projects | Idempotent resume |
| Gateway health after indexer boot | Minutes, not seconds — JVM lesson |
| MCP tool timeout | Bound every call; fail visibly |
| Audit completeness on writes | Every `restart_agent` / `assign_agent_group` leaves an event |

See [reliability.md](../operations/reliability.md).

## Cloud Tools (**Proposed**)

Session recorder metadata, MCP call logs, egress logs, exportable for
IR. That is additional observability, not a reason to log packet
payloads into the control plane by default.
