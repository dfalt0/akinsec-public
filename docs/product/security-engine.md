# Security Engine

**Status: Shipped** (v1), with **Partial** enrollment and sharing.

Security Engine is a dedicated **Wazuh-based** detection stack
provisioned for a customer (in v1: **per user**), reachable only through
an **authenticated gateway**. AkinSec did not fork Wazuh. The managed
stack is **4.12-era**. The Wazuh Dashboard is **not** exposed. AskAkin
is the UI.

## Why it exists

A SIEM manager and indexer should not sit on the public internet with
vendor admin surfaces wide open. AskAkin already has identity, audit,
and a first-party UI. The engine is therefore:

1. Provisioned as an **isolated cloud project**.
2. Split into **private** manager + indexer and a **public** gateway.
3. Driven from AskAkin REST (workspace) and MCP (agents) through the
   same operations layer.

Essay: [Why a SIEM should not be on the public internet](../essays/01-siem-not-on-the-public-internet.md).

## Topology (shipped)

```text
                    ┌─────────────────────────────────────┐
  Analyst / Agent   │         AskAkin control plane        │
                    │  (OIDC session, encrypted metadata)  │
                    └──────────────────┬──────────────────┘
                                       │ HTTPS + bearer
                                       │ (token never logged)
                                       ▼
                    ┌─────────────────────────────────────┐
                    │     Gateway — only public hostname   │
                    │     health ≠ data                    │
                    │     allowlisted manager + search     │
                    └──────────────┬───────────┬──────────┘
                                   │           │
                         private DNS     private DNS
                                   │           │
                                   ▼           ▼
                            Wazuh manager  Wazuh indexer
                            (not public)   (OpenSearch,
                                           not public)
```

Three containers per stack: **indexer**, **manager**, **gateway**.
Public images for that provisioned stack exist under the `akinsec`
Docker Hub namespace. That is not a runbook for running AskAkin.

## Onboarding (shipped)

After signup the customer can enable SIEM **now**, **later**, or
**skip**. The flow collects company and organization names, starts
**async** provisioning, and **polls until healthy**. Humans confirm
before provision because the action has **cost and security**
consequences ([ADR-0010](../adr/0010-human-confirmation-before-provision.md)).

States: `idle` → `running` → `succeeded` | `failed`. Cancel returns
toward `idle`. See [provisioning.md](../architecture/provisioning.md).

## Public-safe properties of provision (shipped)

- Atomic lock: two clicks cannot create two cloud projects.
- If a project id already exists, **resume and redeploy**, do not create another.
- Stale `running` locks can be re-acquired after a timeout.
- Fresh creates are **attempt-capped**.
- Deleted cloud projects are detected; stale IDs are cleared before a new create.
- Indexer starts first and gets a boot window; manager and gateway follow
  (JVM + security plugin on the indexer is the slow part).
- Unique public gateway hostname per stack (company slug + disambiguator).
- Health: gateway reports ready when manager and indexer respond; **empty
  alert indices are OK** on a fresh stack.
- User can stop in-flight provisioning.
- Billing entitlement can be enforced later without rewriting the provisioner.

## First-party REST surfaces (conceptual)

AskAkin exposes Wazuh-backed UI operations. This is **not** a private
route map:

- Engine status
- Agent inventory
- Alert discover (search, filters, histogram, inspect, CSV/JSON export, saved searches)
- Severity summary
- Threats / vulnerability summary
- Ops / compliance posture rollups
- Cloud-connector event summaries

## v1 limitations (honest)

| Topic | v1 fact | Direction |
|-------|---------|-----------|
| Sharing | One stack **per user**, not org-shared | One stack per tenant + RBAC (**Proposed**) |
| Enrollment | Agent enrollment ports **not** publicly exposed (no classic public 1514/1515) | Controlled edge enrollment (**Proposed**) |
| Dashboard | Wazuh Dashboard **not** exposed | AskAkin remains the UI ([ADR-0017](../adr/0017-no-wazuh-dashboard.md)) |
| Billing | Entitlement flag exists | Payment processor **not shipped** |
| Cloud modules | Indexer-backed 24h counts when integrations exist; otherwise educational empty/demo states | Do not treat demo numbers as customers |
| Ops frameworks | SCA rollups when data exists; else placeholder | Not a certified GRC product |

## Secrets (conceptual)

Gateway tokens and control-plane copies of stack secrets are
**encrypted at rest**. Vendor passwords live as **runtime secrets on
the stack**, not in chat logs. Fail closed if encryption keys are
missing. See [secrets-model.md](../architecture/secrets-model.md) and
[ADR-0003](../adr/0003-per-stack-secrets.md),
[ADR-0004](../adr/0004-encrypt-control-plane-copies.md).

## Proof this pattern is not vaporware for Cloud Tools

Cloud Tools (**Proposed**) reuses: isolated project, authenticated
ingress, MCP adapters, encrypted artifacts, HITL for dangerous actions.
Read [cloud-tools/README.md](../cloud-tools/README.md) with this page
open.
