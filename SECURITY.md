# Security

This repository is **documentation**. It does not contain the AskAkin
application, provisioner credentials, or gateway allowlists.

## Reporting issues in these docs

If you find a problem in this public material that could help an attacker
(for example: an accidentally committed secret, an overly specific internal
path, or a diagram that maps live attack surface), please:

1. Open a [GitHub security advisory](https://github.com/dfalt0/akinsec-public/security/advisories/new) on **this** repo if the issue is in the published Markdown, or
2. Open a private report via GitHub on [dfalt0](https://github.com/dfalt0) if advisories are unavailable.

Do not file a public issue that pastes the sensitive content.

## Reporting issues in the live product

The production workspace is [https://app.akinsec.com](https://app.akinsec.com).

For suspected vulnerabilities in AskAkin itself:

- Prefer a **private** channel to GitHub user [dfalt0](https://github.com/dfalt0).
- Include impact and a high-level description. Do not attach exploit PoCs to public GitHub issues on this docs repo.
- There is **no published bug bounty** unless the owner announces one later. Do not assume payment.

AkinSec will not provide a public “clone and run” path, internal route maps, or secret-bearing configuration examples in response to reports.

## What this repo will never publish

- Credentials, tokens, encryption keys, or connection strings
- Customer identifiers
- Gateway allowlist inventories and vendor admin APIs
- Exploit recipes, malware, or attack playbooks

See [docs/security/authorized-use.md](docs/security/authorized-use.md).

## Coordinated disclosure

Reasonable time to remediate live-product issues is expected before public
write-ups. Docs-only mistakes (wrong status label, over-specific diagram)
will be corrected in this repository.
