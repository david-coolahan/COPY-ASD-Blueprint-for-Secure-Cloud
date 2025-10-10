---
title: "Rules"
weight: 30
description: "This section describes the configuration of rules within Microsoft Defender associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Defender portal at the following URL:

<https://security.microsoft.com/securitysettings/endpoints/alert_suppression>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Alert suppression

`Not configured`

### Indicators

`Not configured`

### Process Memory Indicators

`Not configured`

### Web Content Filtering

| Item                   |           Value |
| ---------------------- | --------------: |
| **General**            |                 |
| Policy Name            | Blocked content |
| **Blocked Categories** |                 |
| Adult content          |      Select all |
| High Bandwidth         |      Select all |
| Legal Liability        |      Select all |
| Leisure                |      Select all |
| Uncategorized          |      Select all |
| **Scope**              |                 |
| Machine Groups         |      Select all |

### Automation uploads

| Item                        |                                                                                                                       Value |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------: |
| **File Content Analysis**   |                                                                                                                             |
| Content analysis            |                                                                                                                          On |
| File extension names        | ’’,air,bat,cmd,com,cpl,dll,elf,exe,gadget,inf,job,js,ko,ko.gz,msi,pl,ps1,py,rb,reg,rgs,scr,sh,sys,tcl,url,vb,vbe,vbs,ws,wsf |
| **Memory Content Analysis** |                                                                                                                             |
| Enabled                     |                                                                                                                          On |

### Automation folder exclusions

`Not configured`

### Asset rule management

`Not configured`

### Related information

#### Security and governance

- None identified

#### Design

- [Endpoints and devices](/design/platform/security/endpoint-security)

#### Configuration

- [Entra ID Protection](/configuration/entra-id/protection)
- [Endpoint security](/configuration/intune/endpoint-security)
- [Configuration policies](/configuration/intune/devices/configuration-policies)

#### References

- [Defender for Endpoint](https://learn.microsoft.com/microsoft-365/security/defender-endpoint)
