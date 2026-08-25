# ADR-0015: BYOL for commercial ISVs; OSS-first defaults

- **Status:** proposed
- **Date:** 2026

## Context

Hiring managers and customers will ask “do you have Burp and IDA?”
The honest answer today is **no**. Shipping pirated binaries would end
the company. Hosting commercial tools without an EULA path would end
it slower.

## Decision

- **Default hosted:** OWASP ZAP, Wireshark/tshark, Ghidra (and Cutter/rizin
  as alternatives).
- **Commercial:** Burp Suite, IDA Pro, Binary Ninja — **BYOL** or ISV
  partnership. Until legal review, **do not promise IDA SaaS**.
- This repository never redistributes commercial binaries.

Alpha is OSS headless behind the existing gateway pattern
([phases.md](../cloud-tools/phases.md)).

## Consequences

- Marketing copy must say “Burp-class” or “BYOL,” not “we include Burp.”
- GPL (Wireshark) obligations apply if we modify and distribute
  ([licensing.md](../cloud-tools/licensing.md)).
- Sales can still tell a true story: the **platform** for labs is
  designed; the **ISV** boxes are gated.

## Related

[comparison-burp-zap.md](../cloud-tools/comparison-burp-zap.md) ·
[comparison-ghidra-ida.md](../cloud-tools/comparison-ghidra-ida.md)
