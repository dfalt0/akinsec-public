# Reliability (conceptual)

**Status: Shipped** behaviors for provision; **design SLO** numbers are
not production SLAs and not public metrics.

## What operators can already depend on

| Behavior | Mechanism |
|----------|-----------|
| No duplicate cloud projects | Lock + resume |
| Stuck `running` | Stale lock re-acquire |
| User abort | Cancel toward `idle` |
| Slow indexer | Health wait measured in minutes, poll UI |
| Empty SIEM | Healthy; agents must not invent data |
| Deleted PaaS project | Detect, clear id, allow new create |

## Draft intents (not promises)

| Signal | Intent |
|--------|--------|
| Provision idempotency | Two enables → one project |
| Gateway liveness | Health ≠ data |
| MCP timeout | Bound calls; visible failure |
| Write audit | Every v1 mutating tool leaves an event |

There is **no** published 99.99% uptime number. Do not invent one.

## Cloud Tools (**Proposed**)

Copy: resume, cancel, TTL destroy/hibernate, broker health. Add egress
deny metrics (count, not packet payloads in the control plane).

[provisioning.md](../architecture/provisioning.md) ·
[observability.md](../architecture/observability.md)
