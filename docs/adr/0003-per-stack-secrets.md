# ADR-0003: Per-stack secrets, not a global Wazuh password

- **Status:** accepted
- **Date:** 2026

## Context

Shared default vendor passwords are how compose demos become production
incidents. A multi-tenant SaaS that provisioned every customer with the
same manager password would turn one leak into every tenant’s SIEM.

## Decision

Each provisioned stack gets a **unique gateway token** and **unique
stack secrets**. There is no global Wazuh password for the fleet.
Control-plane copies follow [ADR-0004](0004-encrypt-control-plane-copies.md).
Vendor runtime passwords stay **on the cloud project**.

## Consequences

- Provisioner must generate and store secrets as part of create/resume.
- Rotation is operationally harder than a single password — and
  necessary. An explicit rotation policy is **Proposed**.
- Support cannot “try the default password.”
- Documentation in this public repo never includes vendor defaults.

## Related

[secrets-model.md](../architecture/secrets-model.md)
