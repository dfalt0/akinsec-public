# Documentation index

Public architecture for **AkinSec** (company) and **AskAkin** (product).
Every page is labeled **Shipped**, **Partial**, or **Proposed**. The
application source is private.

## Start here

| Document | Status | Purpose |
|----------|--------|---------|
| [What this repo is](00-what-this-repo-is.md) | — | Boundary: docs, not the app |
| [Overview](00-overview.md) | mixed | Names, truth paragraph, scale |
| [FAQ](faq.md) | — | Short answers |
| [Glossary](glossary.md) | — | SIEM, MCP, HITL, BYOL, … |

## Product

| Document | Status |
|----------|--------|
| [AskAkin](product/askakin.md) | Shipped (alpha) |
| [Security Engine](product/security-engine.md) | Shipped (v1 limits called out) |
| [Workspace](product/workspace.md) | Shipped + Partial modules |
| [Agents, MCP, skills](product/agents-mcp-skills.md) | Shipped |
| [Identity and tenancy](product/identity-tenancy.md) | Shipped |
| [Code interpreter](product/code-interpreter.md) | Shipped |
| [Billing](product/billing.md) | Partial (hook only) |

## Architecture

| Document | Status |
|----------|--------|
| [System context](architecture/system-context.md) | Shipped + Proposed Cloud Tools |
| [Containers](architecture/containers.md) | Shipped |
| [Provisioning](architecture/provisioning.md) | Shipped |
| [Gateway](architecture/gateway.md) | Shipped |
| [Data isolation](architecture/data-isolation.md) | Shipped |
| [Secrets model](architecture/secrets-model.md) | Shipped (conceptual) |
| [Observability](architecture/observability.md) | Partial |
| [Upstream LibreChat](architecture/upstream-librechat.md) | Shipped practice |

## Decisions

[ADR index](adr/README.md) — eighteen records.

## Security

| Document |
|----------|
| [Threat model](security/threat-model.md) |
| [Secure development](security/secure-development.md) |
| [Responsible AI](security/responsible-ai.md) |
| [Authorized use](security/authorized-use.md) |

## Cloud Tools (Proposed)

[RFC home](cloud-tools/README.md) — catalog, isolation, MCP design,
licensing, UX, phases, SKU estimates, ZAP vs Burp, Ghidra vs IDA.

## Essays

[Essay index](essays/README.md) — longer engineering notes (gateway,
provisioning, tenancy, MCP, fork strategy, HITL, isolation, BYOL, scope,
cost, prompt injection, n8n history).

## Operations

| Document |
|----------|
| [Reliability](operations/reliability.md) |
| [Cost model](operations/cost-model.md) |

## Hiring-manager map

[Resume notes](resume-notes.md)

## Diagrams

Mermaid lives **inline** in the Markdown so GitHub renders it. Additional
sources: [docs/diagrams/](diagrams/README.md).
