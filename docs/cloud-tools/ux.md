# Cloud Tools UX (AskAkin)

**Status: Proposed.** Workspace chrome today is eight tabs
([workspace.md](../product/workspace.md)). Labs is an additional tab,
not a replacement for SIEM.

## New tab: Labs (or Tools)

- Catalog of SKUs (ZAP, Wireshark, Ghidra, …) with **Start session**
  (cost + scope reminder) — same confirmation energy as
  [ADR-0010](../adr/0010-human-confirmation-before-provision.md).
- **Scope picker** (reuse Cloud/Devices asset lists where possible).
- **Split view:** chat | tool UI (iframe or desktop stream).
- **Approval cards** in chat: “ZAP wants to start an active scan on
  staging.example.com (in-scope). Approve / Deny.”
- **Artifact drawer:** pcaps, ZAP/Burp reports, Ghidra projects,
  exported PDFs.
- **Session TTL** countdown; hibernate vs destroy.

```text
┌─ AskAkin ─────────────────────────────────────────────┐
│ Chat  Activity  Alerts  Devices  Threats  Ops  Cloud  │
│ Config  [ Labs ]                                       │
├──────────────┬────────────────────────────────────────┤
│ Agent thread │  Tool UI (ZAP / Ghidra / Wireshark)    │
│              │                                        │
│ [Approve]    │  in-scope: staging.example.com         │
│ [Deny]       │  TTL 01:14:02    [Hibernate] [Destroy] │
├──────────────┴────────────────────────────────────────┤
│ Artifacts: scan-report.html   capture.pcap   app.exe  │
└───────────────────────────────────────────────────────┘
```

Phase 1 may be **chat-only** (headless tools, no GUI). That is still
useful and cheaper. Phase 2 adds the human GUI. Do not skip HITL
because the GUI is missing — active scan still needs a card.

## Empty and error states

| State | Copy intent |
|-------|-------------|
| No scope | Cannot start. Admin must declare assets. |
| Entitlement missing | Not a SKU on this plan. Honest; no fake trial of IDA. |
| Engine vs labs | Labs do not require SIEM, but sharing identity/tenant with AskAkin |
| Session failed | Resume/redeploy language borrowed from Security Engine, not “try again” spawn-storm |

## Accessibility and ops aesthetic

Dark, high contrast, SOC not pastel. Status chips: session health,
egress deny counts, last MCP decision. Avoid “AI purple haze.”
