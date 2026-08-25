# Architecture Decision Records

Each ADR: context, decision, consequences, status (`accepted` or `proposed`).

| # | Title | Status |
|---|-------|--------|
| [0001](0001-librechat-as-upstream.md) | LibreChat as upstream, not brand | accepted |
| [0002](0002-gateway-only-ingress.md) | Gateway as the only public SIEM ingress | accepted |
| [0003](0003-per-stack-secrets.md) | Per-stack secrets, not a global Wazuh password | accepted |
| [0004](0004-encrypt-control-plane-copies.md) | Encrypt control-plane copies; vendor passwords on the project | accepted |
| [0005](0005-oidc-workos-tenant-mapping.md) | OIDC/WorkOS; org → tenant | accepted |
| [0006](0006-tenant-isolation-data-layer.md) | Tenant isolation in the data layer | accepted |
| [0007](0007-async-provision-resume.md) | Async provision + resume | accepted |
| [0008](0008-mcp-and-rest-facades.md) | MCP for AI-to-SIEM, REST for the UI | accepted |
| [0009](0009-audited-single-target-writes.md) | Audited single-target writes only in v1 | accepted |
| [0010](0010-human-confirmation-before-provision.md) | Human confirmation before provisioning | accepted |
| [0011](0011-public-images-private-source.md) | Public stack images; private application source | accepted |
| [0012](0012-interpreter-org-siem-user.md) | Interpreter per org, SIEM per user in v1 | accepted (unify later: proposed) |
| [0013](0013-cloud-tools-same-pattern.md) | Cloud Tools follow Security Engine isolation/gateway/MCP | proposed |
| [0014](0014-authorized-scope-binding.md) | Authorized-scope binding for offensive-capable tools | proposed |
| [0015](0015-byol-oss-first.md) | BYOL for commercial ISVs; OSS-first defaults | proposed |
| [0016](0016-ai-copilot-hitl.md) | AI is a copilot with HITL, not an autonomous attacker | accepted (principle); labs HITL proposed |
| [0017](0017-no-wazuh-dashboard.md) | No Wazuh Dashboard exposure | accepted |
| [0018](0018-selective-upstream-sync.md) | Selective upstream sync | accepted |
