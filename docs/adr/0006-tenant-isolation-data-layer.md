# ADR-0006: Tenant isolation in the data layer, not only in route handlers

- **Status:** accepted
- **Date:** 2026

## Context

Every multi-tenant bug bounty write-up has the same plot: a new endpoint
forgot `tenantId`. Handler discipline does not survive a 900-file SPA
and hundreds of API modules.

## Decision

Isolation lives in a **Mongoose plugin plus async context**:

- Queries are scoped to the current tenant.
- Cross-tenant **writes are rejected**.
- Caches and logs are tenant-aware.

Route handlers still must not be sloppy. They are not the last line.

## Consequences

- Background jobs and MCP operations must propagate async context.
  Inspection-only MCP cannot act as another user.
- Indexes and unique constraints must include tenant.
- Essay: [03](../essays/03-multitenant-mongodb.md).

## Related

[data-isolation.md](../architecture/data-isolation.md)
