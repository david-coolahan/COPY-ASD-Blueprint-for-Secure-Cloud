---
title: "Settings"
weight: 30
type: docs
description: "This page describes the configuration of Identity Protection within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_IAM/IdentityProtectionMenuBlade/~/Settings>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

| Item                                                |       Value |
| --------------------------------------------------- | ----------: |
| Allow on-premise password change to reset user risk | Not checked |

### Related information

#### Security and governance

- [Multi-factor authentication](/security-and-governance/essential-eight/multi-factor-authentication)
- [Authentication hardening](/security-and-governance/system-security-plan/system-hardening-authentication)
- [Essential Eight - Restrict administrative privileges](/security-and-governance/essential-eight/restrict-administrative-privileges)

#### Design

- [Identity protection](/design/platform/identity/protection)

#### Configuration

- [Entra ID Protection](/configuration/entra-id/protection)
- [Cloud apps settings](/configuration/defender/settings/cloud-apps/settings)

#### References

- [What is identity protection](https://learn.microsoft.com/entra/id-protection/overview-identity-protection)
