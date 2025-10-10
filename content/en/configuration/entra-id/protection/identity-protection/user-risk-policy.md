---
title: "User risk policy"
weight: 10
type: docs
description: "This page describes the configuration of a user risk policy within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_IAM/IdentityProtectionMenuBlade/~/UserPolicy>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### User risk remediation policy

| Item               |                             Value |
| ------------------ | --------------------------------: |
| Users              |                Include: All users |
|                    | Exclude: `<Break Glass accounts>` |
| User risk          |                  Medium and above |
| Controls           |           Require password change |
| Policy enforcement |                           Enabled |

### Related information

#### Security and governance

- [Essential Eight - Restrict administrative privileges](/security-and-governance/essential-eight/restrict-administrative-privileges)
- [Authentication hardening](/security-and-governance/system-security-plan/system-hardening-authentication)
- [Essential Eight - Multi-factor authentication](/security-and-governance/essential-eight/multi-factor-authentication)

#### Design

- [Identity protection](/design/platform/identity/protection)

#### Configuration

- [Sign-in risk policy](/configuration/entra-id/protection/identity-protection/sign-in-risk-policy)
- [MFA for Risky Sign-ins](/configuration/entra-id/protection/conditional-access/policies/reauthentication-for-risky-sign-ins)

#### References

- [Migrate risk policies from Identity Protection to Conditional Access](https://learn.microsoft.com/entra/id-protection/howto-identity-protection-configure-risk-policies#migrate-risk-policies-from-identity-protection-to-conditional-access)
- [What is identity protection](https://learn.microsoft.com/entra/id-protection/overview-identity-protection)
