# SKU sizing

**Status: Proposed.** Numbers are **design estimates**, not production
facts, not price quotes, not measured utilization.

Security Engine indexer already taught the platform that **JVM +
security plugins need real memory** (multi-GB). Carry that lesson into
Cloud Tools: do not undersize analysis VMs.

Essay: [Cost of a per-user JVM SIEM](../essays/10-cost-of-jvm-siem.md).

## Estimates

| SKU | CPU / RAM / disk (estimate) | Notes |
|-----|----------------------------|-------|
| ZAP small | 2 vCPU / 4 GB / 20 GB | Web lab |
| Wireshark | 2 vCPU / 8 GB / 100 GB | pcap storage dominates disk |
| Ghidra | 4 vCPU / 16 GB / 50 GB | decompiler |
| Malware VM | 4 vCPU / 16 GB / 80 GB + snapshot | **no egress**; microVM |
| IDA BYOL | similar to Ghidra | license serving is unspecified until Hex-Rays terms are reviewed; IDA is not a planned default SKU |

## Cost gates (product)

- Sleep on idle
- Disk quotas (especially Wireshark)
- GPU as **add-on**, not default
- Attempt caps on “Start session” analogous to SIEM provision caps
- Destroy vs hibernate: hibernate costs storage; destroy costs re-import time

## What not to do

- Pack Ghidra into the code-interpreter container “to save money”
- Share one Wireshark among tenants with folder-name isolation
- Assume 512 MB is enough because a tutorial used it

## Relation to billing

Meters are **Phase 6**. Until payments ship, even dogfood labs need
**attempt caps** so a loop cannot spawn unbounded PaaS projects.
[cost-model.md](../operations/cost-model.md).
