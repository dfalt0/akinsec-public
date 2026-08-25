# Licensing and legal

**Status: Proposed** for hosted labs. This section is here to show
maturity, not to give legal advice. Counsel review is required before
any commercial SKU.

AkinSec will **not** pirate or redistribute Burp Suite or IDA Pro in
this repository or as “included” binaries.

## OSS we can host (default path)

| Tool | License | Hosting note |
|------|---------|--------------|
| OWASP ZAP | Apache 2.0 | Default web tester |
| Ghidra | Apache 2.0 | Default RE; still need ToS for customer binaries |
| mitmproxy | MIT | Scriptable proxy |
| tshark/Wireshark | **GPL** | If we **distribute modified** Wireshark, publish corresponding source **or** use unmodified distro packages and document that |
| radare2 | LGPL | CLI adapter |
| rizin / Cutter | OSS | Alternative GUI |
| Zeek | BSD-style | Protocol logging |

GPL is not a blocker; it is an **obligation**. Alpha should prefer
**unmodified distro packages** for Wireshark/tshark to keep the
paperwork boring.

## Commercial BYOL

| Tool | Vendor reality | AkinSec plan until legal says otherwise |
|------|----------------|----------------------------------------|
| Burp Suite | PortSwigger EULA. Hosting for third parties likely needs agreement | **BYOL**: customer accepts EULA; AkinSec is the runtime. Until then, **ZAP is the default** |
| IDA Pro | Hex-Rays EULA is strict | **Do not promise IDA SaaS**. Ghidra/Cutter first; IDA as “BYOL if permitted” |
| Binary Ninja | Commercial | Same BYOL story |

Essay: [BYOL or bust](../essays/08-byol-or-bust.md).
[ADR-0015](../adr/0015-byol-oss-first.md).

## Export controls and malware

AkinSec is **not a botnet**. Samples stay in-tenant. There is **no
anonymous public sandbox**. Malware VMs have **no unrestricted
internet**. Customer-uploaded samples are encrypted at rest and
shredded on session end unless pinned.

This is not a full export-control opinion. It is a product constraint
so engineering does not “helpfully” add a world-readable sample bucket.

## Customer binaries and pcaps

Customer content in labs is **their** data. ToS must say: we process
it to provide the session; we do not train foundation models on it
without opt-in (aligned with public Privacy language on akinsec.com).
Retention follows session TTL unless they promote an artifact.

## Trademarks

Burp, IDA, Wireshark, Ghidra, and others are trademarks of their
owners. Use in this RFC is nominative (class comparables).
[NOTICE.md](../../NOTICE.md).
