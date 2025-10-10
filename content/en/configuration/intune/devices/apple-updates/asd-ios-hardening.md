---
title: "ASD iOS hardening"
weight: 30
description: "This section describes the configuration of device configuration profiles within Microsoft Intune associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Intune portal at the following URL:

<https://intune.microsoft.com/#view/Microsoft_Intune_DeviceSettings/DevicesMenu/~/iOSiPadOSUpdate>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Properties

#### Basics

| Item        |             Value |
| ----------- | ----------------: |
| Name        | ASD iOS Hardening |
| Description |                   |

#### Update policy settings

| Item              |                   Value |
| ----------------- | ----------------------: |
| Update to install |           Latest update |
| Schedule type     | Update at next check-in |

#### Assignments

| Item            |              Value |
| --------------- | -----------------: |
| Included groups | No Included groups |
| Excluded groups | No Excluded groups |

### Related information

#### Security and governance

- [Enterprise mobility](/security-and-governance/system-security-plan/enterprise-mobility)
- [User application hardening](/security-and-governance/system-security-plan/system-hardening-user-apps)
- [Essential Eight - Restrict Microsoft Office macros](/security-and-governance/essential-eight/restrict-microsoft-office-macros)
- [Essential Eight - Patch applications](/security-and-governance/essential-eight/patch-applications)
- [Essential Eight - Patch operating systems](/security-and-governance/essential-eight/patch-os)
- [Essential Eight - Regular backups](/security-and-governance/essential-eight/regular-backups)
- [Essential Eight - Application control](/security-and-governance/essential-eight/application-control)
- [Enterprise mobility](/security-and-governance/system-security-plan/enterprise-mobility)
- [System management](/security-and-governance/system-security-plan/system-management)
- [System monitoring](/security-and-governance/system-security-plan/system-monitoring)

#### Design

- [Authentication](/design/platform/identity/authentication)
- [Securing iOS devices](/design/endpoints/ios/security/securing-ios-devices)

#### Configuration

- [iOS and iPadOS](/configuration/intune/apps/by-platform/ios-ipados)
- [Microsoft Intune - profile configurations](/configuration/intune/devices/configuration-policies)
- [Endpoint security policies](/configuration/defender/endpoints/configuration-management/endpoint-security-policies)
- [Permissions](/configuration/defender/settings/endpoints/permissions)
- [Rules](/configuration/defender/settings/endpoints/rules)

#### References

- None identified
