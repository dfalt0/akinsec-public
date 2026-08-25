# ADR-0016: AI is a copilot with HITL, not an autonomous attacker

- **Status:** accepted as a product principle; Cloud Tools HITL UX is **proposed**
- **Date:** 2026

## Context

AskAkin agents already call live SIEM tools. The failure mode is not
“the model is slightly wrong about a CVE.” It is “the model restarts
the wrong agent” or, later, “the model active-scans a bank.”

Consumer copilot marketing (“just let the agent cook”) is incompatible
with a security company.

## Decision

- Models **do not invent** telemetry. Unprovisioned engine → onboarding.
- v1 writes are audited and single-target ([ADR-0009](0009-audited-single-target-writes.md)).
- Dangerous Cloud Tools actions (active scan, unrestricted capture,
  anything named like exploit/shell) require **explicit approval** in
  AskAkin, plus scope ([ADR-0014](0014-authorized-scope-binding.md)).
- AkinSec will **not** build an AI that autonomously exploits
  third-party systems. Authorized offensive testing, if ever offered,
  is a separate engagement mode with contracts, scope, and humans.

## Consequences

- Slower demos than “fully autonomous SOC.”
- Clearer procurement story.
- Prompt injection is treated as **input**, not as admin
  ([essay 11](../essays/11-prompt-injection-vs-siem-tools.md)).
