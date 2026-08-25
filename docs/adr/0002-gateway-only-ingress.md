# ADR-0002: Gateway as the only public SIEM ingress

- **Status:** accepted
- **Date:** 2026

## Context

A Wazuh manager and OpenSearch indexer expose powerful APIs. Putting
them on the public internet — even “behind a password” — is how SIEM
estates get scraped, clustered to death, or used as a confused deputy.

AskAkin already authenticates analysts (OIDC) and already has a place
to put allowlists and audit. Direct browser-to-indexer access would
bypass that.

## Decision

**Never** expose manager or indexer publicly. AskAkin does not call
those URLs directly in production. A **gateway** is the only public
hostname. It is an **allowlist**, not a transparent proxy. Health is
liveness, not data. Bearer token required except health.

This document does not publish the allowlist inventory.

## Consequences

- Extra hop and extra secret (gateway token).
- Enrollment ports in v1 stay off the public topology — a **limitation**,
  not a stealth feature. A controlled enrollment edge is future work.
- Cloud Tools should copy this pattern (broker), not invent a raw
  desktop with a public IP and a hope.
- Operators debug through AskAkin status + gateway health, not by
  opening vendor dashboards ([ADR-0017](0017-no-wazuh-dashboard.md)).

## Related

[gateway.md](../architecture/gateway.md) ·
[essay 01](../essays/01-siem-not-on-the-public-internet.md)
