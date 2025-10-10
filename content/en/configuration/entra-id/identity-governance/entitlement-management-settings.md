---
title: "Entitlement management settings"
weight: 10
type: docs
description: "This page describes the configuration of entitlement management settings within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_ERM/DashboardBlade/~/elmSetting>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Manage the lifecycle of external users

| Item                                                             | Value |
| ---------------------------------------------------------------- | ----: |
| Block external user from signing in to this directory            |   Yes |
| Remove external user                                             |   Yes |
| Number of days before removing external user from this directory |    30 |

### Related information

#### Security and governance

- [Security documentation](/security-and-governance/system-security-plan/security-documentation)
- [Essential Eight - Restrict administrative privileges](/security-and-governance/essential-eight/restrict-administrative-privileges)

#### Design

- [Identity governance](/design/platform/identity/governance)
- [Conditional access](/design/platform/identity/conditional-access)

#### Configuration

- [Configuration policies](/configuration/intune/devices/configuration-policies)

#### References

- None identified
