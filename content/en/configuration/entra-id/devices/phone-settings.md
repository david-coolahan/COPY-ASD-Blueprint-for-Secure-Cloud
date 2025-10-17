---
title: "Phone settings"
weight: 10
type: docs
description: "This page describes the configuration of device settings within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_Devices/DevicesMenuBlade/~/DeviceSettings>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Microsoft Entra join and registration settings

| Item                                                                                |     Value |
| ----------------------------------------------------------------------------------- | --------: |
| Users may join devices to Microsoft Entra                                           |       All |
| Users may register their devices with Microsoft Entra                               |       All |
| Require Multifactor Authentication to register or join devices with Microsoft Entra |        No |
| Maximum number of devices per user                                                  | Unlimited |

### Local administrator settings

| Item                                                                                                          | Value |
| ------------------------------------------------------------------------------------------------------------- | ----: |
| Global administrator role is added as local administrator on the device during Microsoft Entra join (Preview) |    No |
| Registering user is added as local administrator on the device during Microsoft Entra join (Preview)          |  None |
| Enable Microsoft Entra Local Administrator Password Solution (LAPS)                                           |   Yes |

### Other settings

| Item                                                                        | Value |
| --------------------------------------------------------------------------- | ----: |
| Restrict users from recovering the BitLocker key(s) for their owned devices |    No |

### Related information

#### Security and governance

- [Enterprise mobility](/security-and-governance/system-security-plan/enterprise-mobility)

#### Design

- [Devices](/design/platform/identity/devices)
- [Securing iOS devices](/design/endpoints/ios/security/securing-ios-devices)
- [Endpoint Management](/design/platform/client)

#### Configuration

- [Entra ID Protection](/configuration/entra-id/protection)
- [Endpoint security](/configuration/intune/endpoint-security)
- [Endpoint security policies](/configuration/defender/endpoints/configuration-management/endpoint-security-policies)
- [Device settings](/configuration/entra-id/devices/device-settings)

#### References

- [Microsoft Entra device identity documentation](https://learn.microsoft.com/entra/identity/devices)
