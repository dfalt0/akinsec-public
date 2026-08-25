# ADR-0005: OIDC / WorkOS for production identity; map org → tenant

- **Status:** accepted
- **Date:** 2026

## Context

LibreChat lineage includes email/password and optional native Google
OAuth. Those paths are fine for a self-hosted chat app. A multi-tenant
security product needs **organization** as a first-class claim, SSO
that procurement recognizes, and a confidential OIDC client — not an
API key wearing a fake “OIDC” badge.

## Decision

Production identity is **WorkOS AuthKit** (OIDC Connect Application,
confidential client) at [app.akinsec.com](https://app.akinsec.com).
The organization claim maps to `tenantId` on the user document.
Social login may ride AuthKit. Native Google on the login form is a
**separate**, non-preferred path.

Callback URLs, client IDs, and issuer hostnames beyond the public
app domain are **not documented** here.

## Consequences

- Tenant alignment with WorkOS organizations is the default mental model.
- v1 SIEM still keys stacks **per user** ([ADR-0012](0012-interpreter-org-siem-user.md))
  — identity tenancy is ahead of SIEM sharing.
- 2FA and ACL lineage remain available; production is OIDC-first.

## Related

[identity-tenancy.md](../product/identity-tenancy.md)
