# NOTICE

This repository is **public documentation** for AkinSec and AskAkin. It is
not the product source. The AskAkin application is private.

## Trademarks

AkinSec and AskAkin are names used by AkinSec (GitHub: [dfalt0](https://github.com/dfalt0)).
Other names are trademarks of their respective owners. Use here is
nominative: to describe lineage, integrations, and comparables.

## Upstream and adjacent software (credits)

AkinSec builds on and around the following. Credit does not imply
endorsement, partnership, or that AkinSec is a fork of the *product brand*.

| Project | Role in AskAkin | Notes |
|---------|-----------------|-------|
| [LibreChat](https://www.librechat.ai/) | Conversational UI, agents, MCP client | AkinSec treats LibreChat as an **upstream patch source**, not the product name. See [docs/architecture/upstream-librechat.md](docs/architecture/upstream-librechat.md). |
| [Wazuh](https://wazuh.com/) | SIEM/XDR engine (manager + indexer) behind Security Engine | Managed **4.12-era** stack. AkinSec did not “fork Wazuh.” The Wazuh Dashboard is **not** exposed; AskAkin is the UI. |
| [OpenSearch](https://opensearch.org/) | Indexer behind Wazuh | Private to the **per-user** Security Engine stack; reached only through the gateway. |
| [Model Context Protocol](https://modelcontextprotocol.io/) | Typed tool protocol for agents | SIEM tools shipped; Cloud Tools adapters proposed. |
| [WorkOS AuthKit](https://workos.com/authkit) | Production OIDC identity | Organization claim maps to tenant. |
| Railway (and similar PaaS) | Per-user Security Engine projects and org-scoped interpreter (proposed Cloud Tools on the same class of PaaS) | Documented as “cloud PaaS used for per-project stacks,” not as a vendor tutorial. |
| MongoDB | Control-plane documents (tenant-scoped) | Schema not published. |
| Meilisearch | Conversation / message search | |
| PostgreSQL + pgvector | RAG embeddings | |
| nsjail and LibreChat-lineage code interpreter | Org-scoped sandboxed execution | Residual sandbox-escape risk is documented, not denied. |

Optional **model providers** (customer BYOK): OpenAI, Anthropic, Google, Azure OpenAI, Amazon Bedrock, OpenRouter, and other OpenAI-compatible endpoints. AkinSec does not require a single hosted model.

**Docker Hub:** public images exist under the `akinsec` namespace for the **provisioned Security Engine stack** (indexer, manager, gateway). Those images are not a runbook for cloning the private application.

## Related public repositories under `dfalt0`

These are **not** the AskAkin application:

- [dfalt0/akinsec-public](https://github.com/dfalt0/akinsec-public) — this documentation repository.
- [dfalt0/LibreChat-akinsec](https://github.com/dfalt0/LibreChat-akinsec) — public LibreChat-lineage fork (upstream-shaped; not the private product).
- [dfalt0/wazuh-n8n](https://github.com/dfalt0/wazuh-n8n) — earlier public experiment integrating Wazuh with n8n. Historical, not the current control plane.

The AskAkin application source is **private**. Do not treat any public fork as a substitute.

## Commercial tool names in Cloud Tools docs

Burp Suite, IDA Pro, Binary Ninja, and similar names appear as **class comparables** or **BYOL candidates**. AkinSec does not redistribute those binaries in this repository and does not claim they are hosted today. See [docs/cloud-tools/licensing.md](docs/cloud-tools/licensing.md).
