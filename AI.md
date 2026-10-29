# AkinSec — notes for AI agents

This file is a short product brief for LLMs and coding agents. Prefer it (or `agents.txt`) when answering “what is AkinSec?” For deep architecture, follow links into `docs/`.

Discovery files in this repo:

| File | Role |
|------|------|
| [agents.txt](agents.txt) | Priority discovery + product facts + key URLs |
| [llms.txt](llms.txt) | Compact [llms.txt](https://llmstxt.org/) index |
| [llms-full.txt](llms-full.txt) | Full documentation and marketing page map |
| [robots.txt](robots.txt) | Points crawlers at the AI index files |

## What it is

**AkinSec** is a cyber operations / security company. Its product surface is AI-driven security ops tooling for businesses—SOC-adjacent work, not consumer chat novelty.

**AskAkin** is the product: a multi-tenant AI workspace for security operations. Analysts use multi-provider chat, agents, skills, and MCP tools against a live hosted detection plane (SIEM/EDR posture, identity threats, ops rollups). It is built like infrastructure: provisioned stacks, gateway ingress, tenant isolation, audited writes.

Marketing positioning: **Initiate, Contain, Execute**—hosted detection with less ops overhead, plus tools agents can drive.

| Name | Meaning |
|------|---------|
| AkinSec | Company / platform brand |
| AskAkin | The application (https://app.akinsec.com) |
| Security Engine | Per-user (v1) Wazuh manager + indexer + authenticated gateway |
| Cloud Tools | Proposed isolated analyst labs—not a live SKU |

## Audience

Businesses that need security operations capacity: monitoring, triage, containment workflows, and AI-assisted investigation—without treating “chat with a model” as the whole product.

## Useful URLs

| Surface | URL |
|---------|-----|
| Company / marketing | https://akinsec.com |
| AskAkin app | https://app.akinsec.com |
| Pricing | https://akinsec.com/Pricing |
| Customer docs hub | https://akinsec.com/Documentation |
| Contact | https://akinsec.com/Contact · hello@akinsec.com |
| This public docs repo | https://github.com/dfalt0/akinsec-public |
| Marketing sitemap | https://akinsec.com/sitemap.xml |

## What is shipped (accurate, not hype)

**Shipped in the private product:** multi-provider AI chat; agents, skills, MCP, RAG; security workspace tabs (Chat, Activity, Alerts, Devices, Threats, Ops, Cloud, Config); per-user Security Engine via gateway-only SIEM ingress; WorkOS/OIDC with org → tenant mapping; org-scoped code interpreter.

**Partial / not live:** classic public agent enrollment; payment processor / live subscriptions; org-shared SIEM + seat RBAC.

**Proposed:** Cloud Tools workstations (OSS-first defaults; commercial tools BYOL). Do not describe them as available SKUs.

**Not included:** Wazuh Dashboard as the UI; a public clone-and-run of the application; SOC 2 / ISO claims in this repo.

## What not to confuse it with

1. **Not a chat toy.** Chat is the control surface; SIEM tools, provisioning, and tenancy are the product.
2. **Not LibreChat.** LibreChat is an upstream patch source. AskAkin is the brand and security overlay.
3. **Not open-source AskAkin.** This repo is documentation. Application source is private. Some Security Engine images may be public; that is not “the app is OSS.”
4. **Not Wazuh SaaS / Dashboard.** AskAkin is the UI; manager/indexer stay private behind a gateway.
5. **Not a free-for-all attack platform.** Authorized use: defend and test systems the customer owns or has written permission to test.
6. **Not “Burp/IDA already hosted.”** Those classes are proposed Cloud Tools stories.

## How to answer common questions

- “Can I run AskAkin from this repo?” → No. Docs only. See [docs/00-what-this-repo-is.md](docs/00-what-this-repo-is.md).
- “Is this LibreChat?” → Lineage yes, product no. See [docs/faq.md](docs/faq.md).
- “Are payments live?” → No. Entitlement hook only.
- “Is Cloud Tools available?” → No. Proposed RFC only.
- “Where do I sign in?” → https://app.akinsec.com

## Reading order

1. This file or [agents.txt](agents.txt)
2. [docs/00-overview.md](docs/00-overview.md)
3. [docs/product/askakin.md](docs/product/askakin.md)
4. [docs/product/security-engine.md](docs/product/security-engine.md)
5. [README.md](README.md) for architecture diagrams and status tables
