# ADR-0004: Encrypt control-plane copies; keep vendor passwords on the cloud project

- **Status:** accepted
- **Date:** 2026

## Context

The control plane must remember enough to call the gateway (a token)
and to resume a project. If those values sit in Mongo as plaintext,
a control-plane dump is a fleet-wide incident. If encryption is
optional, it will be off in the one environment that matters.

Chat logs and HITL pause payloads are another sink. Models and UI
debug streams must never become secret stores.

## Decision

- Encrypt control-plane copies of gateway tokens and related metadata
  **at rest**.
- Keep vendor passwords as **runtime secrets on the stack**.
- **Fail closed** if encryption configuration is missing — no plaintext
  fallback for customer LLM credentials either.
- Never log tokens. Never put secrets in HITL pause payloads.

Algorithm names, key lengths, and environment variable names are
**intentionally omitted** here.

## Consequences

- Key management is a production dependency.
- Disaster recovery must include encryption keys, not only Mongo dumps.
- Prompt-injection defenses assume secrets are not in the context
  window ([essay 11](../essays/11-prompt-injection-vs-siem-tools.md)).

## Related

[secrets-model.md](../architecture/secrets-model.md)
