# Cloud Tools catalog

**Status: Proposed.** No SKU is live. Names of commercial products are
**comparables** or **BYOL candidates**, not a redistribution claim.

Never publish payload lists, CVE exploit recipes, or “bypass WAF”
tutorials. Talk about **authorized testing of the tenant’s applications**.

## A. Web application security (Burp-class)

| Tool | License | Role | AI/MCP ideas (high level) |
|------|---------|------|---------------------------|
| OWASP ZAP | OSS (Apache 2.0) | **Default** hosted intercepting proxy + spider + passive scan | `list_sites_in_scope`, `get_history`, `generate_report` — **active scan only with HITL** |
| Burp Suite Professional | Commercial BYOL | Customer uploads license; we run official product in isolated desktop **if EULA allows** | Drive via documented extension/API if licensed; otherwise GUI-only + human |
| mitmproxy | OSS | Scriptable intercepting proxy | Scripted intercept with approval |

See [comparison-burp-zap.md](comparison-burp-zap.md).

## B. Network analysis (Wireshark-class)

| Tool | License | Role |
|------|---------|------|
| Wireshark + tshark | GPL | GUI + CLI packet analysis on uploaded or tap-limited captures |
| tcpdump | BSD | Capture on an isolated tap attached only to in-scope lab nets |
| Zeek | OSS | Protocol logging |
| NetworkMiner | OSS | Session reconstruction (where license permits hosting) |

Captures are tenant-owned artifacts in object storage. **No promiscuous
capture on AkinSec’s production network.**

## C. Reverse engineering (Ghidra / IDA-class)

| Tool | License | Role |
|------|---------|------|
| Ghidra | Apache 2.0 | **Default** RE environment (headless + GUI) |
| Cutter / rizin | OSS | Alternative GUI RE |
| radare2 | LGPL | CLI for agent-driven analysis |
| IDA Pro | Commercial BYOL | Optional **if Hex-Rays terms allow hosted use**; otherwise “bring your own workstation” later |
| Binary Ninja | Commercial BYOL | Same BYOL story |

**Malware:** analysis VMs have **no unrestricted internet**. Sample
handling: customer-uploaded, encrypted at rest, shredded on session end
unless they pin an artifact. AkinSec will **not** host a public malware
zoo.

See [comparison-ghidra-ida.md](comparison-ghidra-ida.md).

## D. Adjacent labs (later waves)

- Volatility 3 on customer-supplied memory dumps
- Autopsy / Sleuth Kit on disk images with huge-disk SKUs
- GVM/OpenVAS or Nuclei **against in-scope only**
- MISP / OpenCTI as **read-only** intel MCP tools
- Live response **only via customer-approved agent**, never unsolicited
  remote access

## What will not appear in the catalog

- Tools whose primary purpose is unauthenticated mass exploitation
- Public sample feeds that turn AkinSec into a malware CDN
- “Anonymous sandbox” with no tenant identity

License matrix: [licensing.md](licensing.md).
