# Workspace

**Status: Shipped** for chrome and the eight tabs. Cloud connector and
Ops framework **depth** is **Partial**.

AskAkin is one operations plane. Chat is part of the workspace — not
the whole product. Summaries, triage help, and guided steps live
**inside** monitoring workflows.

## Information architecture (shipped)

| Tab | What the analyst sees |
|-----|------------------------|
| **Chat** | Multi-model chat and a floating chat overlay on other tabs |
| **Activity** | Overview: agent health, 24h severity, module cards |
| **Alerts** | Discover: query, filters, time range, fields, histogram, inspect, export, saved searches |
| **Devices** | Agent inventory, status, OS, CSV export |
| **Threats** | Vulnerabilities, SCA, MITRE-oriented views |
| **Ops** | Framework posture: hygiene, PCI DSS, GDPR, HIPAA, NIST, TSC |
| **Cloud** | Connector cards: Docker, AWS, GCP, GitHub, Microsoft 365, Microsoft Graph |
| **Config** | Engine status, provision/stop, connection health |

Onboarding: **choice → company/org details → confirm → provisioning poll → done**.

## Activity and endpoint modules

Activity cards cover endpoint themes aligned with the Wazuh lineage:
configuration assessment (SCA), malware-oriented views, and file
integrity monitoring (FIM). Threat intel cards cover hunting,
vulnerabilities, and MITRE-oriented rollups. These are **workspace
modules**, not a claim that every detector is uniquely invented by
AkinSec.

## Ops (Partial)

Framework cards produce **SCA-based posture rollups when data exists**.
Otherwise the UX is a placeholder. This is **not** a certified GRC
product and not an attestation of SOC 2, ISO 27001, PCI, HIPAA, or GDPR.

## Cloud connectors (Partial)

When Wazuh cloud integrations are configured, cards can show
**indexer-backed 24-hour event counts**. When they are not, the UI
shows **educational empty or demo states**. Demo numbers are not live
customers.

## Config

Config is the operator’s grip on the engine: status, start or stop
provisioning, connection health. It does not expose manager or indexer
admin consoles.

## Proposed: Labs / Tools tab

Cloud Tools adds a **Labs** (or **Tools**) tab: SKU catalog, scope
picker, split view (chat | tool UI), approval cards, artifact drawer,
session TTL. That tab is **Proposed**. See [cloud-tools/ux.md](../cloud-tools/ux.md).

## Related

- [AskAkin](askakin.md)
- [Security Engine](security-engine.md)
- [Agents and MCP](agents-mcp-skills.md)
- [One operations plane vs five consoles](../architecture/one-operations-plane.md)
