# ADR-0010: Human confirmation before provisioning

- **Status:** accepted
- **Date:** 2026

## Context

Enabling Security Engine creates a paid-shaped cloud project (JVM
indexer memory, three containers, public hostname). Accidental double
clicks are handled by locks ([ADR-0007](0007-async-provision-resume.md)).
Accidental **intent** is not: a user exploring Config should not spawn
infrastructure without knowing cost and security implications.

## Decision

Onboarding is **choice → details → confirm → poll**. Provision does
not start from a hover or a single ambiguous toggle without confirm.
The same principle applies to **Proposed** Cloud Tools “Start session”
(cost + scope reminder).

## Consequences

- Slightly more UX friction; fewer surprise bills and orphan projects.
- Billing entitlement can sit in front of the same confirm step later.
