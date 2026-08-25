# Overview

**Status:** mixed — names and shipped capabilities below; Cloud Tools is
**Proposed**.

## The two names

| Name | What it is | Public wording |
|------|------------|----------------|
| **AkinSec** | Company / platform brand | AkinSec is a cybersecurity company building AI-operated security infrastructure for businesses. |
| **AskAkin** | The application | AskAkin is AkinSec’s security workspace: multi-provider AI chat, agents, skills, and a live SIEM workspace, delivered as a multi-tenant web app. |
| **Security Engine** | Per-customer SIEM stack | A dedicated Wazuh-based detection stack provisioned for a customer, reachable only through an authenticated gateway. |
| **Cloud Tools** | Hosted analyst workstations | Isolated, AI-controllable instances of professional security tools (web testing, packet analysis, reverse engineering) bound to the customer’s authorized scope. **Proposed.** |

There is **no separate public “AkinSec application repo.”** AskAkin is
the product. AkinSec is the company wrapping it.

## One-paragraph product truth

AkinSec builds **AskAkin**, a multi-tenant security operations workspace.
Analysts chat with AI agents that can call **live SIEM tools** over
**MCP**. When a customer enables **Security Engine**, the platform
provisions an **isolated cloud project** containing a Wazuh manager, a
Wazuh indexer (OpenSearch), and a **public gateway that is the only
ingress**. Manager and indexer stay on a private network. Gateway tokens
and stack secrets are **encrypted at rest** on the control plane; Wazuh
passwords live as **runtime secrets on the stack**, not in chat logs.
Identity is **OIDC (WorkOS AuthKit)** with **organization → tenant**
mapping. The same provisioning pattern is used for a **per-organization
sandboxed code interpreter**. The conversational UI is a
**LibreChat-lineage** application that AkinSec treats as an upstream
patch source, not as the product brand. The next platform bet is
**Cloud Tools**: per-tenant hosted Burp-class, Wireshark-class, and
Ghidra/IDA-class workstations, AI-orchestrated, fully functional, scoped
to the customer’s own assets, with audit and human approval for
dangerous actions.

## Technical scale (public-safe)

These numbers characterize the **private product**. They are order-of-magnitude
characterizations, **not** a lines-of-code audit and **not** customer
metrics.

| Area | Approximate scale |
|------|-------------------|
| Product lineage | LibreChat v0.8.6 / v0.8.7-era fork + large AkinSec overlay |
| Workspaces | API (legacy JS Express), TypeScript API package, data-schemas, data-provider, React SPA |
| Frontend | ~900 React/TSX modules; ~570 TS modules in the SPA tree |
| Legacy API | ~690 JS modules |
| New backend TS | ~690 TS modules |
| Data schemas | ~250 TS modules; 40+ document models |
| Tests | ~900 spec files + ~40 Playwright e2e specs |
| HTTP route modules | ~50 Express route files |
| Locales | 40+ language folders (mostly upstream; do not claim AkinSec uniquely translated all of them) |
| Runtime (full local/dev) | MongoDB, Meilisearch, RAG API, pgvector, Wazuh indexer, Wazuh manager, optional interpreter, optional OTEL fanout |
| Per-customer Security Engine | 3 containers (indexer, manager, gateway) |
| Per-org code interpreter | 3 containers (API, Redis, object storage) |
| MCP product server | ~20 tools |
| Workspace tabs | 8 |
| Overview modules | endpoint (SCA, malware, FIM), threat intel (hunting, vulns, MITRE), ops (6 frameworks), cloud (6 connectors) |

## Engineering practices worth highlighting

- New backend is TypeScript-first; legacy Express is a thin wrapper.
- Shared types live in a data-provider package consumed by SPA and API.
- Tenant isolation is a data-layer plugin plus async context, not a hope-and-filter in handlers.
- Provisioning is **idempotent resume**: lock, attempt cap, stale recovery, cancel, health wait — no duplicate cloud projects.
- MCP writes are audited; bulk destructive SIEM actions are out of v1.
- Gateway is allowlist-in, not “proxy everything.”
- Control-plane copies of secrets are encrypted at rest; vendor passwords stay on the cloud project.
- Tests prefer real logic (in-memory stores, real MCP SDK) over theater mocks — stated as **philosophy**, not pasted tests.

## Control plane vs data plane

- **Control plane:** AskAkin — identity, UI, agents, provisioners, encrypted metadata.
- **Data plane:** customer Security Engine and future Cloud Tool sessions.
- **Gateway / broker:** authenticating reverse proxy with allowlists.

See [system context](architecture/system-context.md).
