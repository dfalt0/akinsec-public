# Comparison: OWASP ZAP vs Burp Suite

**Status: Proposed** product choice. Neither is hosted today.

## Why ZAP is the default

| | OWASP ZAP | Burp Suite Professional |
|---|---------|-------------------------|
| License | Apache 2.0 | Commercial EULA |
| Hosting | We can run it | Needs PortSwigger agreement / BYOL |
| Automation | Daemon + APIs suitable for MCP | Strong, but legally gated |
| Market familiarity | High among OSS/AppSec | Higher among professional pentesters |
| AkinSec v1 labs | **Default** | **Phase 4 BYOL** |

Burp is often the tool an AppSec team already bought.
Promising it early without an EULA path is how startups get letters.
AkinSec’s honest line: **Burp-class workflow**, ZAP in alpha, Burp
when BYOL is real.

## AI role

- ZAP: sitemap, history, passive scan, **HITL active scan**, report
- Burp: **human-primary**; AI summarizes **already captured** proxy
  history. Do not market “AI fires Burp scanner at the Internet.”

## What we will not write in this repo

Payload libraries, bypass recipes, or exploit PoCs. Authorized testing
of **in-scope** tenant apps only.
[authorized-use.md](../security/authorized-use.md).

## Related

[catalog.md](catalog.md) · [licensing.md](licensing.md) ·
[ADR-0015](../adr/0015-byol-oss-first.md)
