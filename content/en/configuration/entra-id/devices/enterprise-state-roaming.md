---
title: "Enterprise state roaming"
weight: 20
type: docs
description: "This page describes the configuration of enterprise state roaming within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_Devices/DevicesMenuBlade/~/RoamingSettings>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

| Item                                                | Value |
| --------------------------------------------------- | ----: |
| Users may sync settings and app data across devices |   All |

### Related information

#### Security and governance

- [Enterprise mobility](/security-and-governance/system-security-plan/enterprise-mobility)
- [`<SYSTEM-NAME>` Mobile Device Usage Policy](/security-and-governance/policies)
- [`<SYSTEM-NAME>` Mobile Device Management Policy](/security-and-governance/policies)
- [Overseas Travel SOP](/security-and-governance/general-documentation)
- [Enterprise mobility](/security-and-governance/system-security-plan/enterprise-mobility)

#### Design

- [Devices](/design/platform/identity/devices)

#### Configuration

- [Entra ID Protection](/configuration/entra-id/protection)
- [Configuration policies](/configuration/intune/devices/configuration-policies)
- [Endpoint security policies](/configuration/defender/endpoints/configuration-management/endpoint-security-policies)

#### References

- [Microsoft Entra device identity documentation](https://learn.microsoft.com/entra/identity/devices)
