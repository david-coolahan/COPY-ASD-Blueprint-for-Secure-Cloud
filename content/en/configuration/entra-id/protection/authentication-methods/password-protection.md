---
title: "Password protection"
weight: 20
type: docs
description: "This page describes the configuration of password protection within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_IAM/AuthenticationMethodsMenuBlade/~/PasswordProtection/>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

| Item                                                          |                              Value |
| ------------------------------------------------------------- | ---------------------------------: |
| Lockout threshold                                             |                                  5 |
| Lockout duration in seconds                                   |                                 60 |
| Enforce custom list                                           |                                Yes |
| Custom banned password list                                   | _as per organisation requirements_ |
| Enable password protection on Windows Server Active Directory |                                Yes |
| Mode                                                          |                           Enforced |

### Related information

#### Security and governance

- [System management](/security-and-governance/system-security-plan/system-management)
- [Authentication hardening](/security-and-governance/system-security-plan/system-hardening-authentication)
- [Essential Eight - Restrict administrative privileges](/security-and-governance/essential-eight/restrict-administrative-privileges)
- [Essential Eight - Multi-factor authentication](/security-and-governance/essential-eight/multi-factor-authentication)
- [Essential Eight - Restrict Microsoft Office macros](/security-and-governance/essential-eight/restrict-microsoft-office-macros)

#### Design

- [Authentication](/design/platform/identity/authentication)
- [Identity](/design/platform/identity)
- [Identity security](/design/platform/security/identity-security)

#### Configuration

- [Entra ID Protection](/configuration/entra-id/protection)
- [Endpoint security](/configuration/intune/endpoint-security)
- [Configuration policies](/configuration/intune/devices/configuration-policies)
- [Endpoint security policies](/configuration/defender/endpoints/configuration-management/endpoint-security-policies)
- [Cloud apps settings](/configuration/defender/settings/cloud-apps/settings)
- [Rules](/configuration/defender/settings/endpoints/rules)

#### References

- [Password and account lockout policies](https://learn.microsoft.com/entra/identity/domain-services/password-policy)
