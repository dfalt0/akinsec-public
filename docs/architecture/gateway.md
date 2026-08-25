# Gateway

**Status: Shipped** as the only public SIEM ingress.
Cloud Tools **broker** is **Proposed** (same idea, different backends).

AskAkin does **not** call manager or indexer URLs directly in
production. That is a core security decision.
[ADR-0002](../adr/0002-gateway-only-ingress.md).
Essay: [Why a SIEM should not be on the public internet](../essays/01-siem-not-on-the-public-internet.md).

## Responsibilities (shipped)

| Function | Note |
|----------|------|
| Sole public hostname | Unique per stack |
| Bearer authentication | Required except liveness health |
| Health | Liveness, not a data dump |
| Allowlisted manager proxy | Named operations only |
| Allowlisted indexer search + field-caps | No arbitrary admin OpenSearch |
| Private DNS to manager and indexer | Data plane stays off the public net |

The gateway is **allowlist-in**, not “proxy everything.” This document
does **not** publish the allowlist path inventory.

## Data path

```text
Analyst  →  AskAkin UI / Agent
              │  JWT session (OIDC-backed)
              ▼
         AskAkin API
              │  looks up user Security Engine record
              │  loads encrypted gateway token
              │  (must not appear in chat)
              ▼
         Gateway (only public hostname)
              │  Authorization: Bearer <gateway token>
              │
              ├── allowlisted manager API  →  Wazuh manager (private DNS)
              └── allowlisted indexer search →  Wazuh indexer (private DNS)
```

## Token handling (conceptual)

- Transport: TLS
- Token not placed in URLs
- Encrypted at rest on the control plane
- Rotation schedule is **Proposed** (v1 stores and uses; rotation policy
  should be explicit in operations)

See [secrets-model.md](secrets-model.md).

## What the gateway is not

- Not the Wazuh Dashboard
- Not a generic HTTP CONNECT tunnel for analysts
- Not a place to expose enrollment ports in v1 (those ports stay off
  the public topology today)

## Cloud Tools broker (**Proposed**)

A **tool broker** authenticates analyst + agent, injects **scope** into
egress, and fronts MCP. Humans may still get a remote desktop to the
same session id. [cloud-tools/README.md](../cloud-tools/README.md).
