---
title: "Server application hardening"
weight: 72
type: docs
description: This page provides a template and guidance to assist organisations in documenting their approach to server application hardening associated with their system(s) built on ASD's Blueprint for Secure Cloud.
---

{{% alert title="Instruction" color="dark" %}}

The server application hardening section of a System Security Plan (SSP) should document an organisation's approach to hardening server applications using vendor and ASD guidance. As with other sections of the SSP, information in the server application hardening section should be documented according to the relevant controls outlined in ASD's ISM and the SSP Annex.

All template text refers to a typical implementation of a system built using the Blueprint, and includes reference to organisational policies, processes and technical configurations to be implemented in addition to the technical controls that may be configured using guidance in the Blueprint. Any implementation implied by the below should not be considered as prescriptive as to how organisations must scope, build, document, or assess a system.

When completing the below template, organisations should insert and update information where relevant to ensure it accurately represents their approach to operating system hardening. When complete, remove any instructional boxes throughout.

{{% /alert %}}

Due to the number of applicable controls in ASD's [_Guidelines for System Hardening_](https://www.cyber.gov.au/resources-business-and-government/essential-cyber-security/ism/cyber-security-guidelines/guidelines-system-hardening), guidance on system hardening has been split into its five sections for the purpose of this SSP.

{{% alert title="Blueprint guidance" color="info" %}}

While applicable to any server applications within the scope of a system built using the Blueprint, this section of a SSP particularly relates to the selection of server applications on servers used for on-premises hybrid services and specifically to those applications developed by Microsoft (notably Entra Connect and Exchange Hybrid Configuration Wizard). Organisations should ensure that server application hardening is appropriately assessed and documented for any other systems within the organisation that are used to support the operation of system(s) built using the Blueprint.

{{% /alert %}}

#### Applicability

This section of the SSP is applicable to application hardening of applications on on-premises Active Directory and Exchange servers within the system boundary of `<SYSTEM-NAME>`.

`<INSERT ADDITIONAL INFORMATION AS APPROPRIATE>`

#### Organisational policies and processes implemented

All vendors of server applications used within `<SYSTEM-NAME>` have been assessed by `<ORGANISATION-NAME>` as demonstrating a commitment to secure-by-design and secure-by-default principles, use of memory-safe programming languages where possible, secure programming practices, and maintaining the security of their products.

- `<ORGANISATION-NAME>` [Vendor Assessment: Microsoft](/security-and-governance/general-documentation)
- `<ORGANISATION-NAME>` [Vendor Assessment: \<VENDOR-2>](/security-and-governance/general-documentation)

`<INSERT ADDITIONAL INFORMATION AS APPROPRIATE>`

#### Technical controls implemented

Technical controls for hardening of Entra Connect and Exchange Hybrid Configuration Wizard within `<SYSTEM-NAME>` are configured with reference to ASD's [_Blueprint for Secure Cloud_](https://blueprint.asd.gov.au) and includes the following technical configurations:

`<INSERT ADDITIONAL INFORMATION AS APPROPRIATE>`

### Related information

#### Security and governance

- [Essential Eight - Application control](/security-and-governance/essential-eight/application-control)
- [Essential Eight - Patch applications](/security-and-governance/essential-eight/patch-applications)
- [Essential Eight - Patch operating systems](/security-and-governance/essential-eight/patch-os)

#### Design

- [Operating system](/design/endpoints/windows/configuration/operating-system)
- [Windows hardening](/design/endpoints/windows/security/windows-hardening)
- [Windows update and patching](/design/endpoints/windows/configuration/windows-update-and-patching)
- [Endpoint Device Updates](/design/platform/client/device-updates)

#### Configuration

- [Microsoft Intune - Applications](/configuration/intune/apps)
- [Microsoft Entra ID - Applications](/configuration/entra-id/applications)
- [Configuration policies](/configuration/intune/devices/configuration-policies)

#### External documentation

- ASD's [_Guidelines for System Hardening_](https://www.cyber.gov.au/resources-business-and-government/essential-cyber-security/ism/cyber-security-guidelines/guidelines-system-hardening)
- ASD's [_Shifting the Balance of Cybersecurity Risk: Principles and Approaches for Security-by-Design and Default_](https://www.cyber.gov.au/resources-business-and-government/governance-and-user-education/secure-by-design/shifting-balance-cybersecurity-risk)
- ASD's [_The Case for Memory Safe Roadmaps_](https://www.cyber.gov.au/resources-business-and-government/governance-and-user-education/secure-by-design/case-memory-safe-roadmaps)
