# Resume notes

Third person, for hiring-manager mapping. No revenue, headcount, or
customer-count claims. Author: Mark, GitHub [dfalt0](https://github.com/dfalt0),
[dfalt0.com](https://dfalt0.com). Title line: Security / Software Engineer.

## One-liner

Founder/engineer, AkinSec — multi-tenant AI security workspace (AskAkin)
with per-customer SIEM provisioning, MCP-operated detection tools, and a
designed path to hosted analyst labs (web testing, packet analysis,
reverse engineering).

## Evidence map

| Resume bullet (example) | Evidence in this public repo |
|-------------------------|------------------------------|
| Designed multi-tenant SaaS isolation for a security product | [tenancy](product/identity-tenancy.md), [ADR-0006](adr/0006-tenant-isolation-data-layer.md), [essay 03](essays/03-multitenant-mongodb.md) |
| Built AI agents that operate a live SIEM through MCP with audited writes | [agents-mcp](product/agents-mcp-skills.md), [ADR-0008](adr/0008-mcp-and-rest-facades.md), [ADR-0009](adr/0009-audited-single-target-writes.md) |
| Implemented async provisioning of per-customer infrastructure with resume/idempotency | [provisioning](architecture/provisioning.md), [essay 02](essays/02-provisioning-as-a-product.md) |
| Integrated OIDC (WorkOS) organization claims into a tenant model | [identity](product/identity-tenancy.md), [ADR-0005](adr/0005-oidc-workos-tenant-mapping.md) |
| Operated JVM-based SIEM (Wazuh/OpenSearch) as a managed service | [Security Engine](product/security-engine.md), [cost model](operations/cost-model.md) |
| Defined a roadmap for hosted professional security tools with license and isolation constraints | [Cloud Tools RFC](cloud-tools/README.md) |
| Practiced responsible upstream-fork engineering (CVE ports, brand isolation) | [upstream](architecture/upstream-librechat.md), [ADR-0018](adr/0018-selective-upstream-sync.md) |
| Applied gateway/allowlist thinking instead of exposing vendor admin planes | [gateway](architecture/gateway.md), [essay 01](essays/01-siem-not-on-the-public-internet.md) |

## Honest limits to mention in interviews

- v1 SIEM is per-user, not org-shared
- Agent enrollment is not a public classic 1514/1515 edge yet
- Payments are not live
- Burp/IDA/Ghidra workstations are designed, not shipped
- Product source is private; this repo is the public architecture

## Links

- App: [https://app.akinsec.com](https://app.akinsec.com)
- Company: [https://akinsec.com](https://akinsec.com)
- This repo: [https://github.com/dfalt0/akinsec-public](https://github.com/dfalt0/akinsec-public)
