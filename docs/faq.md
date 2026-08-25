# FAQ

## Can I see the AskAkin code?

No. The application source is **private**. This repository is
architecture and product documentation. See
[what this repo is](00-what-this-repo-is.md).

## Is this LibreChat?

**Lineage yes, product no.** The conversational UI is
LibreChat-lineage. AkinSec treats upstream as a **patch source**. The
brand, SIEM workspace, Security Engine, tenancy overlay, and MCP SIEM
server are AkinSec. Credits: [NOTICE.md](../NOTICE.md).

## Is AkinSec open source?

No. Public container images exist for the **provisioned Security Engine
stack**. The application is not open source.

## Can I pentest anyone with Cloud Tools?

No. Products are for **defending and authorized testing of systems the
customer owns or has written permission to test**. Third-party attacks
are prohibited and will be technically constrained. Cloud Tools is
**Proposed**, not shipped. [authorized-use.md](security/authorized-use.md).

## Is IDA Pro or Burp Suite already hosted?

No. Do not say they are. OSS-first defaults (ZAP, Wireshark, Ghidra)
are the proposed labs default. Commercial tools are **BYOL / ISV** stories.
[licensing.md](cloud-tools/licensing.md).

## Is the Wazuh Dashboard included?

No. AskAkin is the UI. [ADR-0017](adr/0017-no-wazuh-dashboard.md).

## Can customers enroll agents like a classic on-prem manager?

Not in v1. Enrollment ports are **not** publicly exposed. That is a
called-out limitation. [security-engine.md](product/security-engine.md).

## Is Kubernetes how production SIEM is provisioned today?

No. Per-project cloud PaaS is the current path. Helm exists for the
**chat API** lineage. A Kubernetes provisioner is **Proposed**.

## Are payments live?

No. An entitlement hook exists. The payment processor is not shipped.
[billing.md](product/billing.md).

## Do you have SOC 2 or ISO 27001?

This repo does **not** claim a current attestation. Isolation, audit
logs, and encryption are designed so future certifications are
*possible*. Ask for current vendor-review detail privately if you need
it.

## Is there a public quick-start to run AskAkin?

No. There is no public clone-and-run path for the private app.

## Who built this?

Mark, GitHub [dfalt0](https://github.com/dfalt0), site
[dfalt0.com](https://dfalt0.com).
