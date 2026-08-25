# ADR-0012: Code interpreter isolated per org; SIEM per user in v1 — unify later

- **Status:** accepted for v1 split; **proposed** to unify SIEM per tenant
- **Date:** 2026

## Context

Code interpreter needs privileged containers and org-wide files. One
stack per user would multiply GPU-unlike but still expensive API/Redis
storage. SIEM, however, shipped first as a **per-user** engine to
avoid an unbuilt RBAC story blocking onboarding.

## Decision

v1:

- Interpreter: **tenant/org** keyed
- Security Engine: **user** keyed

Roadmap: **one SIEM stack per tenant** with viewer / analyst / admin
RBAC. Until then, document the split so nobody “fixes” it in support
by sharing gateway tokens across users.

## Consequences

- Two users in one company can have two engines (cost, confusion).
- Org admin vs analyst roles for SIEM are incomplete.
- Cloud Tools should **not** copy the per-user SIEM mistake; labs
  should be org-entitled from alpha where possible.

## Related

[identity-tenancy.md](../product/identity-tenancy.md)
