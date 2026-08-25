# Upstream LibreChat

**Status: Shipped** as an engineering practice. AkinSec is **not** the
LibreChat product.

LibreChat is a **chassis**: chat, agents, MCP client, multi-provider
routing, artifacts, RAG wiring, ACL lineage. AskAkin is the **car**:
security workspace, Security Engine, tenancy, provisioners, AkinSec MCP
SIEM server, seeded analyst skills.

Essay: [LibreChat is a chassis, not the car](../essays/05-librechat-chassis-not-the-car.md).
[ADR-0001](../adr/0001-librechat-as-upstream.md) ·
[ADR-0018](../adr/0018-selective-upstream-sync.md).

## Lineage (honest)

- AskAkin tracks LibreChat as a **patch source** (v0.8.6 lineage; in-tree
  version reported as **v0.8.7** during a 2026 upstream sync).
- A preserve-manifest of AkinSec-specific surfaces exists (on the order
  of **~120 paths**). This repo does **not** list those paths.
- Selective port: security, auth/tenancy, MCP, billing-idempotency
  fixes. Skip upstream branding and i18n automation (Locize/community
  CI) that would fight the AkinSec brand.

Public [dfalt0/LibreChat-akinsec](https://github.com/dfalt0/LibreChat-akinsec)
is an **upstream-shaped** tracking fork. It is **not** the private
product overlay. Do not treat it as AskAkin.

## Why not rebrand as LibreChat

This is not a reskin of LibreChat. The SIEM
gateway, Railway-class provisioner, WorkOS tenant mapping, and MCP
write audit are AkinSec work. Credits stay loud in [NOTICE.md](../../NOTICE.md).

## Locales

40+ language folders exist; much is upstream. Do not claim AkinSec
uniquely translated all of them.

## Kubernetes Helm

Helm lineage for the **chat API** is upstream-shaped. It is not how
Security Engine projects are provisioned today.
