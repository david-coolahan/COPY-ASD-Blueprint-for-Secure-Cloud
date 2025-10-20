---
title: "Admin consent settings"
weight: 20
type: docs
description: "This page describes the configuration of admin consent settings within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/~/AdminConsentSettings>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Admin consent requests

| Item                                                                   | Value |
| ---------------------------------------------------------------------- | ----: |
| Users can request admin consent to apps they are unable to consent to​ |    No |

| Item                                                          | Value |
| ------------------------------------------------------------- | ----: |
| Selected users will receive email notifications for requests​ |   Yes |
| Selected users will receive request expiration reminders​     |   Yes |
| Consent request expires after (days)​                         |    30 |

### Related information

#### Security and governance

- [Essential Eight - Application control](/security-and-governance/essential-eight/application-control)
- [User application hardening](/security-and-governance/system-security-plan/system-hardening-user-apps)
- [Essential Eight - Patch applications](/security-and-governance/essential-eight/patch-applications)
- [System monitoring](/security-and-governance/system-security-plan/system-monitoring)

#### Design

- None identified

#### Configuration

- [User consent settings](/configuration/entra-id/applications/enterprise-applications/consent-and-permissions/user-consent-settings)
- [Permissions](/configuration/defender/settings/endpoints/permissions)

#### References

- [Application management documentation](https://learn.microsoft.com/entra/identity/enterprise-apps)
