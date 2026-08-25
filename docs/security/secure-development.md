# Secure development

**Status:** practices in the private product, described without source.

## Testing philosophy

Tests favor **real logic** — in-memory Mongo, real MCP SDK — over
theater mocks. Approximate scale: ~900 spec files and ~40 Playwright
e2e specs. This repo does not paste those tests.

## Monorepo discipline

- TypeScript-first new backend; legacy Express as a thin wrapper
- Shared types in a data-provider package for SPA and API
- CI builds the monorepo; image-publish workflow for Security Engine
  containers (tags not documented as a runbook)

## Fork hygiene

Selective upstream sync ([ADR-0018](../adr/0018-selective-upstream-sync.md)):
port CVEs and authz/MCP fixes; skip branding/i18n automation.
Preserve AkinSec surfaces. Do not merge blindly.

## Secrets in development

No vendor default passwords in this public repo. Local compose exists
in the **private** tree; it is not reproduced here. Fail closed for
missing encryption config is a production rule that should also bite
in staging.

## What “secure development” is not

- Not a claimed SOC 2 report
- Not a public bug bounty unless announced
- Not permission to publish gateway allowlists “for researchers”

Reports: [SECURITY.md](../../SECURITY.md).
