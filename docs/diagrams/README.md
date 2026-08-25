# Diagram sources

Mermaid diagrams are **inline** in architecture and product pages so
GitHub renders them without a site generator.

This folder is a map, not a second copy of every chart.

| Diagram | Lives in |
|---------|----------|
| Logical platform | [README.md](../../README.md), [system-context.md](../architecture/system-context.md) |
| Containers | [containers.md](../architecture/containers.md) |
| Provision state machine | [provisioning.md](../architecture/provisioning.md) |
| SIEM data path | [gateway.md](../architecture/gateway.md), [security-engine.md](../product/security-engine.md) |
| MCP loop | [agents-mcp-skills.md](../product/agents-mcp-skills.md) |
| Cloud Tools session | [cloud-tools/README.md](../cloud-tools/README.md) |

Do not add screenshots of the private app. They can leak stealth UX or
mock data that looks like a real tenant.
