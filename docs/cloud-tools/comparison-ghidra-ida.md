# Comparison: Ghidra vs IDA Pro

**Status: Proposed** product choice. Neither workstation is hosted today.

## Why Ghidra is the default

| | Ghidra | IDA Pro |
|---|--------|---------|
| License | Apache 2.0 | Hex-Rays EULA (strict) |
| Headless | First-class | Exists; hosting still legal-gated |
| MCP fit | Import → list → decompile → strings | Possible later; **not promised** |
| Cost to tenant | Included in OSS SKU estimates | BYOL + possible license server |
| Malware workflow | Needs **microVM** either way | Same isolation bar |

IDA remains the gold standard in many RE shops. AkinSec will not
pretend Apache-licensed Ghidra “is IDA.” We also will not ship IDA
as SaaS until counsel says hosted use is permitted.

Cutter/rizin and radare2 are **alternatives** for GUI/CLI diversity,
not a claim of IDA compatibility.

## AI role (non-weaponized)

- List imported APIs
- Decompile a named function (size-capped)
- Search strings that look like URLs
- Diff two **customer-supplied** firmware versions

No “auto-exploit this binary against a host.”

## Malware

Untrusted samples require Phase 5 isolation, no unrestricted egress,
and shred-on-destroy. Ghidra vs IDA does not change that.

## Related

[catalog.md](catalog.md) · [licensing.md](licensing.md) ·
[isolation.md](isolation.md)
