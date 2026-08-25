# What this repository is

**Status of this page:** meta (not a product capability).

`dfalt0/akinsec-public` is public architecture and product
documentation for AkinSec and AskAkin: multi-tenant SaaS, per-user
Security Engine, MCP-operated SIEM tools, and a designed path to hosted
analyst labs.

It is **not**:

- The AskAkin application source
- A quick-start that lets a stranger run the private app
- An open-source claim about the product
- A copy of LibreChat or Wazuh documentation
- An API catalog that matches private HTTP routes 1:1
- A pentest or malware lab

## Public vs private

| Public (this repo, marketing site, login hostname) | Private (never reconstructed here) |
|----------------------------------------------------|--------------------------------------|
| Architecture diagrams at C4 context/container level | Source, compose secrets, Helm secret values |
| Product behavior in words (tabs, MCP tool *names*, states) | File paths, GraphQL names, lock algorithms, crypto parameter lengths |
| v1 limits (per-user SIEM, enrollment, billing) | Customer names, org IDs, project IDs, emails |
| Cloud Tools RFC (proposed) | Commercial binaries, exploit recipes |
| Credits to LibreChat, Wazuh, WorkOS, MCP | Secret-bearing variable names and values |

If a fact would map the **live attack surface** (gateway allowlist
inventory, vendor admin APIs, indexer query internals), it is omitted
on purpose. The architectural *idea* stays.

## How to read status labels

- **Shipped** — implemented in the private product as of this writing.
- **Partial** — UI or data path exists; coverage, sharing, or billing is incomplete.
- **Proposed** — design for review; not a live SKU.

Blurring those labels is a defect. File an issue if you catch it.

## Why the product source stays private

Detection content, tenant isolation internals, gateway allowlists, and
provisioner credentials are **security-sensitive**. The docs describe
structure and limits. They omit internals that would map a live attack
surface. See [Why public docs + private code](../README.md#why-public-docs--private-code).

## Related links

- Production: [https://app.akinsec.com](https://app.akinsec.com)
- Company: [https://akinsec.com](https://akinsec.com)
- GitHub: [dfalt0](https://github.com/dfalt0) · [dfalt0.com](https://dfalt0.com)
- Credits: [NOTICE.md](../NOTICE.md)
