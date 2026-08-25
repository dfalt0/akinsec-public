# Data handling (conceptual)

**Status:** control-plane rules **Shipped** as described in
[secrets-model.md](../architecture/secrets-model.md). This page is
**not** a privacy policy, DPA, or SOC 2 report. Legal documents live
on [akinsec.com](https://akinsec.com).

## What AskAkin stewards

| Class | Where | Public rule |
|-------|--------|-------------|
| Investigation threads, files, agents, skills | Control plane (Mongo, search, object storage) | Tenant-scoped; cross-tenant writes rejected |
| Customer LLM credentials | Control plane, encrypted at rest | Fail closed if encryption config is missing |
| Gateway token | Encrypted copy on control plane; used on TLS to the gateway | Never in chat, URLs, or HITL payloads |
| Vendor SIEM passwords | Runtime secrets **on the stack** | Unique per stack |
| SIEM telemetry | Customer data plane (indexer/manager, private) | Reachable only through the gateway |
| Lab artifacts (**Proposed**) | Tenant object store + session volume | Scope-bound; shred on destroy unless pinned |

## Encryption (conceptual)

- In transit: TLS to the app and to the gateway.
- At rest: control-plane copies of tokens and customer provider
  credentials are encrypted. Algorithms and key lengths are **not**
  published here.

## AI and training

Public product language: AkinSec does not require a single hosted
model (**BYOK**). Do not assume customer threads are used to train
foundation models; opt-in is the only honest path if that ever
changes. Tool output is untrusted data
([essay 11](../essays/11-prompt-injection-vs-siem-tools.md)).

## Residency

Marketing docs state primary regions are **US-based today**. Other
regions are a conversation before purchase, not a silent guarantee
in this repo.

## Subprocessors (named, not a complete list)

WorkOS (identity), the customer’s chosen model providers, the cloud
PaaS used for per-project stacks, optional LLM-trace fanout.
Optional means **optional**.

## Retention and labs (**Proposed** extras)

Cloud Tools sessions should TTL, hibernate or destroy, and avoid
logging packet payloads into the control plane by default. Malware
samples: encrypted, no unrestricted egress, shred unless pinned.

## What we will not put here

Connection strings, region IDs, bucket names, or “how long we keep
Mongo oplogs.” Those are either secrets or would map production.

Related: [threat-model.md](threat-model.md) ·
[authorized-use.md](authorized-use.md) ·
[Privacy on akinsec.com](https://akinsec.com/Privacy)
