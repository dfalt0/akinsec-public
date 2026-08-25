# ADR-0011: Public container images for the provisioned stack; private application source

- **Status:** accepted
- **Date:** 2026

## Context

A Railway-class PaaS pulls images to build customer stacks. Requiring
registry credentials on every tenant project is operationally painful
and leaks another secret class into provisioner config.

The application, however, contains detection content, tenancy internals,
and gateway allowlists. Publishing it would map attack surface.

## Decision

- **Public** images under the `akinsec` Docker Hub namespace for
  indexer / manager / gateway **used in provisioning**.
- **Private** AskAkin application source.
- Do **not** document image tags as a deployment runbook in this repo.
- Secrets never baked into images ([ADR-0003](0003-per-stack-secrets.md)).

## Consequences

- Image contents should assume they are inspectable. No embedded
  customer data, no default passwords.
- Forks of public stack images are possible; they still cannot call
  AskAkin’s control plane.
- Hiring managers can see that “public images” ≠ “open-source product.”
