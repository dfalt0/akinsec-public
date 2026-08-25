# ADR-0009: Audited, single-target writes only in v1

- **Status:** accepted
- **Date:** 2026

## Context

A model that can `restart_agent` on one device is useful. A model that
can bulk-restart, upload rule files, or fire active response across a
fleet is a **production incident** waiting for a prompt injection.

## Decision

v1 MCP writes:

- **Single target** only (`restart_agent`, `assign_agent_group` where
  the group already exists).
- **Audited** every time.
- **Out of scope:** bulk restart, rule-file upload, active-response
  fire-and-forget from the model.

HITL approval cards for writes are a **tightening** (see
[ADR-0016](0016-ai-copilot-hitl.md)), not a claim that every v1 restart
already waits for a click.

## Consequences

- Agents must explain “I will restart this one agent” rather than
  “I will remediate the environment.”
- SOAR-style playbooks remain **Proposed**.
- Audit logs are a future certification input, not a current SOC 2 claim.

## Related

[essay 06](../essays/06-hitl-restart-agents.md)
