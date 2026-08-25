# Authorized use

**Status:** product policy (applies to shipped SIEM and **Proposed** labs).

AkinSec products are for **defending and authorized testing of systems
the customer owns or has written permission to test**.

Hosted web-testing, packet-analysis, and reverse-engineering tools will
be **scope-bound**. Using the platform to attack third parties is
**prohibited** and will be technically constrained (egress allowlists,
session audit, kill switch).

## SIEM (shipped)

Telemetry in a Security Engine is **that principal’s stack**. MCP and
REST cannot be aimed at another tenant’s manager. Sharing a login to
“help a friend” is a policy violation and a tenancy smell; v1 is
per-user which makes shared logins worse — another reason org-shared
RBAC is on the roadmap.

## Cloud Tools (Proposed)

| Allowed | Not allowed |
|---------|-------------|
| ZAP/Burp-class testing of **in-scope** staging/prod the tenant owns | Scanning random Internet hosts |
| Wireshark on **customer-owned** pcaps or taps on lab nets they defined | Promiscuous capture on AkinSec production networks |
| Ghidra/IDA-class analysis of **customer-uploaded** binaries | Building a public malware zoo; unrestricted sample egress |
| Memory/disk forensics on **customer-supplied** dumps | Unsolicited live response onto machines without an approved agent |

Malware analysis VMs: **no unrestricted internet**. Samples encrypted
at rest; shredded on session end unless the customer pins an artifact.

## Continuous red team (Proposed, later)

Only against the customer’s **own authorized scope**, with contracts
and humans. Never unsolicited third parties.

## Legal

This page is documentation, not a substitute for Terms of Service on
[akinsec.com](https://akinsec.com). Commercial ISV EULAs (Burp, IDA)
are additional gates ([licensing.md](../cloud-tools/licensing.md)).
