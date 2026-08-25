# Glossary

Terms are used consistently across this repository.

| Term | Meaning |
|------|---------|
| **AkinSec** | Company / platform brand. |
| **AskAkin** | The multi-tenant security workspace application. |
| **Security Engine** | Per-customer (v1: per-user) Wazuh-based detection stack behind a gateway. |
| **Cloud Tools** | Proposed hosted analyst workstations (web testing, packet analysis, RE). |
| **Control plane** | AskAkin: identity, UI, agents, provisioners, encrypted metadata. |
| **Data plane** | Customer Security Engine and future Cloud Tool sessions. |
| **Gateway / broker** | Authenticating reverse proxy with allowlists. Sole public SIEM ingress today. |
| **Tenant** | Typically a WorkOS organization. v1 SIEM is still per-user. |
| **OIDC** | OpenID Connect. Production identity via WorkOS AuthKit. |
| **MCP** | Model Context Protocol — typed tools for models. |
| **HITL** | Human-in-the-loop approval. |
| **BYOL** | Bring your own license (commercial ISVs). |
| **BYOK** | Bring your own key — customer-held model provider credentials. |
| **Skill** | Versioned playbook an agent can load. |
| **SCA** | Wazuh Security Configuration Assessment. |
| **FIM** | File integrity monitoring. |
| **MITRE ATT&CK** | Knowledge base used in Threats-oriented views. |
| **SIEM** | Security information and event management. |
| **XDR** | Extended detection and response (Wazuh’s positioning; AskAkin is the operator UI). |
| **SOAR** | Security orchestration, automation, and response — **Partial/Proposed** playbooks, not a claim of a full SOAR product. |
| **nsjail** | Linux sandbox used inside the org code interpreter. |
| **OpenSearch** | Indexer behind Wazuh in the managed stack. |
| **PaaS** | Platform-as-a-service used today for per-tenant (per-user SIEM) cloud projects. Kubernetes is a planned alternative, not how SIEM is provisioned today. |
| **Allowlist** | Gateway permits only named operations; not a transparent proxy. |
| **Fail closed** | Missing encryption config does not fall back to plaintext secrets. |
| **Resume** | Provisioner redeploys an existing project instead of creating a duplicate. |
| **Scope** | Customer-declared assets (CIDRs, domains, artifacts) a session may touch. **Proposed** as a first-class object for Cloud Tools. |
