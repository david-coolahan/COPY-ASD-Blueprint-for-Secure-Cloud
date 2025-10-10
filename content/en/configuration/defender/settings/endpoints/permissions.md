---
title: "Permissions"
weight: 20
description: "This section describes the configuration of endpoint permissions within Microsoft Defender associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Defender portal at the following URL:

<https://security.microsoft.com/securitysettings/endpoints/user_roles>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Roles

#### Microsoft Defender for Endpoint Administrator (default)

| Item                     |                                  Value |
| ------------------------ | -------------------------------------: |
| **General**              |                                        |
| All Settings             |                     _Leave as default_ |
| **Assigned user groups** |                                        |
| Group Name               | Azure ATP _tenant name_ Administrators |

#### Microsoft Defender for Endpoint Remediation

| Item                                                                              |                                       Value |
| --------------------------------------------------------------------------------- | ------------------------------------------: |
| **General**                                                                       |                                             |
| Role name                                                                         | Microsoft Defender for Endpoint Remediation |
| View Data                                                                         |                                     Enabled |
| - Security operations                                                             |                                     Enabled |
| - Defender Vulnerability Management                                               |                                     Enabled |
| Active remediation actions                                                        |                                     Enabled |
| - Security Operations                                                             |                                     Enabled |
| - Defender Vulnerability Management - Exception handling                          |                                     Enabled |
| - Defender Vulnerability Management - Remediation handling                        |                                     Enabled |
| - Defender Vulnerability Management - Application handling                        |                                     Enabled |
| Defender Vulnerability Management - Manage security baselines assessment profiles |                                     Enabled |
| Alerts investigation                                                              |                                     Enabled |
| Manage security settings in Security Center                                       |                                    Disabled |
| Live response capabilities                                                        |                                     Enabled |
| - Advanced                                                                        |                                    Selected |
| **Assigned User groups**                                                          |                                             |
| Group Name                                                                        |               Azure ATP _tenant name_ Users |

#### Microsoft Defender for Endpoint Viewer

| Item                                |                                  Value |
| ----------------------------------- | -------------------------------------: |
| **General**                         |                                        |
| Role name                           | Microsoft Defender for Endpoint Viewer |
| View Data                           |                                Enabled |
| - Security operations               |                                Enabled |
| - Defender Vulnerability Management |                                Enabled |
| **Assigned User groups**            |                                        |
| Group Name                          |        Azure ATP _tenant name_ Viewers |

### Device groups

#### Windows 10/11

| Item              |                                                                                                  Value |
| ----------------- | -----------------------------------------------------------------------------------------------------: |
| Rank              |                                                                                                      1 |
| **General**       |                                                                                                        |
| Device group name |                                                                                          Windows 10/11 |
| Remediation level |                                                                 Full - remediate threats automatically |
| **Devices**       |                                                                                                        |
| Name              |                                                                                       `Not configured` |
| AND Domain        |                                                                                       `Not configured` |
| AND Tag           |                                                                                       `Not configured` |
| AND OS            |                                                                            In - Windows 10, Windows 11 |
| **User access**   |                                                                                                        |
| Group Name        | Azure ATP _tenant name_ Administrators, Azure ATP _tenant name_ Users, Azure ATP _tenant name_ Viewers |

#### Ungrouped devices

| Item              |                                                                                                  Value |
| ----------------- | -----------------------------------------------------------------------------------------------------: |
| Rank              |                                                _Not applicable for the default ungrouped device group_ |
| **General**       |                                                                                                        |
| Device group name |                                                                            Ungrouped devices (default) |
| Remediation level |                                                                 Full - remediate threats automatically |
| **Devices**       |                                                _Not applicable for the default ungrouped device group_ |
| **User access**   |                                                                                                        |
| Group Name        | Azure ATP _tenant name_ Administrators, Azure ATP _tenant name_ Users, Azure ATP _tenant name_ Viewers |

### Related information

#### Security and governance

- [System management](/security-and-governance/system-security-plan/system-management)
- [Essential Eight - User application hardening](/security-and-governance/essential-eight/user-application-hardening)

#### Design

- [Endpoints and devices](/design/platform/security/endpoint-security)

#### Configuration

- [Microsoft Intune - Applications](/configuration/intune/apps)
- [Microsoft Entra ID - Applications](/configuration/entra-id/applications)
- [Configuration policies](/configuration/intune/devices/configuration-policies)

#### References

- [Defender for Endpoint](https://learn.microsoft.com/microsoft-365/security/defender-endpoint)
