# Data isolation

**Status: Shipped** for Mongo tenant plugin + per-stack networks.
Org-shared SIEM is **Proposed**.

## Control-plane isolation (shipped)

A Mongoose plugin plus async context:

- Injects `tenantId` into queries
- Rejects cross-tenant mutations
- Keeps caches and logs tenant-aware

This is the difference between “we meant to filter” and “the database
layer will not return another tenant’s documents.”
Essay: [docs/essays/03-multitenant-mongodb.md](../essays/03-multitenant-mongodb.md).
[ADR-0006](../adr/0006-tenant-isolation-data-layer.md).

## Data-plane isolation (shipped)

Each Security Engine is its own cloud project:

- Private manager and indexer
- Gateway token unique per stack ([ADR-0003](../adr/0003-per-stack-secrets.md))
- No lateral routing to the control-plane database

Code interpreter stacks are **org-keyed** with private Redis and object
storage.

## The v1 inconsistency to say out loud

SIEM is **per-user**. Interpreter is **per-org**. Unifying SIEM onto
the tenant with RBAC is **Proposed**. Until then, two users in the same
company can have **two engines**. That is a v1 limit: SIEM is per user,
not org-shared.

## What isolation is not

- Not “the LLM will please not mention other customers”
- Not a shared OpenSearch cluster with index-name hope
- Not a single global Wazuh password

## Cloud Tools (**Proposed**)

No shared GPU/VM that can leak files across customers. Session volumes
encrypted. Default deny egress. Malware SKUs on microVMs.
[isolation.md](../cloud-tools/isolation.md).
