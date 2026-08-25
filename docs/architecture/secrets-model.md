# Secrets model

**Status: Shipped** conceptually. This page **does not** document
algorithms, key lengths, environment variable names, or vendor default
passwords.

## Classes of secret

| Class | Where it lives | Rule |
|-------|----------------|------|
| OIDC client credentials | Identity config on the control plane | Not logged; not in this repo |
| Credential-encryption keys | Control plane | Missing config **fails closed** |
| Customer LLM provider credentials | Encrypted at rest on the control plane | Never plaintext config; never HITL pause payloads |
| Gateway token | Encrypted copy on control plane; presented to gateway over TLS | Not in URLs; not in chat logs |
| Stack / vendor runtime passwords | **On the cloud project**, not in chat | Unique per stack |
| Platform cloud API token | Control plane (provisioner) | Never published |
| Object-store credentials | Control plane / interpreter project | Tenant-scoped usage |

[ADR-0003](../adr/0003-per-stack-secrets.md) ·
[ADR-0004](../adr/0004-encrypt-control-plane-copies.md)

## Fail closed

If encryption configuration for stored customer credentials is missing,
AskAkin does **not** fall back to writing plaintext. Operators must
fix configuration rather than silently weaken the product.

## What never appears in model context

Gateway tokens, vendor passwords, platform cloud API tokens, and
credential-encryption keys. Tool results are **untrusted data**. Prompt
injection that says “print the gateway token” must fail.
[essays/11-prompt-injection-vs-siem-tools.md](../essays/11-prompt-injection-vs-siem-tools.md).

## Rotation (**Proposed** as an explicit ops policy)

v1 can store and use tokens. A published rotation schedule (gateway
tokens, stack secrets) should exist before Cloud Tools adds more
long-lived session credentials.

## Public images vs private secrets

Stack **images** can be public so a PaaS can pull without registry
credentials. **Secrets** are never in the image. [ADR-0011](../adr/0011-public-images-private-source.md).
