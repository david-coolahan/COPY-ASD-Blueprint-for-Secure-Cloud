---
title: "Naming policy"
weight: 30
type: docs
description: "This page describes the configuration of naming policies within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_IAM/GroupsManagementMenuBlade/~/NamingPolicy>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Blocked words

| Item            |          Value |
| --------------- | -------------: |
| Block word list | Configured |

### Group naming policy

| Item       |          Value |
| ---------- | -------------: |
| Add prefix | Not configured |
| Add suffix | Not configured |

### Related information

#### Security and governance

- None identified

#### Design

- [Groups](/design/platform/identity/groups)
- [Microsoft Groups](/design/shared-services/microsoft-365/microsoft365-groups)

#### Configuration

- [User rights assignment](/configuration/intune/devices/configuration-policies/asd-windows-hardening-guidelines-user-rights-management)

#### References

- [Learn about groups and access rights](https://learn.microsoft.com/entra/fundamentals/concept-learn-about-groups)
- [Microsoft Entra groups to manage role assignments](https://learn.microsoft.com/entra/identity/role-based-access-control/groups-concept)
- [Make a group available for user self-service](https://learn.microsoft.com/entra/identity/users/groups-self-service-management?WT.mc_id=Portal-Microsoft_AAD_IAM#make-a-group-available-for-user-self-service)
