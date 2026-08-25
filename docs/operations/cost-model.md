# Cost model

**Status: design estimates only.** Not invoices. Payments **not shipped**.

## Security Engine (v1)

- Three containers per **user** (indexer, manager, gateway)
- Indexer JVM + security plugin → **multi-GB RAM**, minutes to healthy
- Unique public hostname
- Attempt cap is the v1 brake

Org-shared stacks (**Proposed**) exist partly to stop paying for N
indexers per N analysts.

## Code interpreter

- Three containers per **org** (API, Redis, object storage)
- Privileged hosts cost more and may be refused by the PaaS (weaker
  fallback exists — document, don’t pretend)

## Cloud Tools (Proposed SKUs)

See [sku-sizing.md](../cloud-tools/sku-sizing.md). Sleep on idle, disk
quotas, GPU add-on. Phase 6 meters require a real billing engine.

## What not to publish as fact

- Customer counts
- Revenue
- Exact PaaS invoices
- “Unlimited” compute

[essay 10](../essays/10-cost-of-jvm-siem.md) ·
[billing.md](../product/billing.md)
