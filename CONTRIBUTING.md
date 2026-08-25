# Contributing

Thank you for reading. This repository is **public architecture and product
documentation** for AkinSec / AskAkin. It is **not** the application.

## What we welcome

- Clarifying questions as GitHub issues (no private-source requests).
- Typo and broken-link fixes.
- Diagram improvements that stay at C4 context/container level.
- Discussion of the **proposed** Cloud Tools RFC (isolation, licensing, HITL).

## What we will not accept

- Patches that reconstruct or guess private source.
- Secrets, customer data, or “how I ran AskAkin locally” runbooks.
- Exploit PoCs, payload lists, or guides for attacking third parties.
- Claims that the product is open source.
- Fake metrics (customer counts, uptime SLAs presented as fact).

## How to propose a docs change

1. Fork or branch from the default branch.
2. Keep status labels honest: **Shipped**, **Partial**, **Proposed**.
3. Prefer linking existing pages over duplicating essays.
4. Do not cite private file paths or secret-bearing variable names.

Pull requests that violate [SECURITY.md](SECURITY.md) or
[docs/security/authorized-use.md](docs/security/authorized-use.md) will be closed.

## Code of conduct

See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
