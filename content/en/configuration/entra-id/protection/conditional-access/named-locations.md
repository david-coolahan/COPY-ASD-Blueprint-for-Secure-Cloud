---
title: "Named locations"
weight: 20
type: docs
description: "This page describes the configuration of named Locations within Microsoft Entra ID associated with systems built according to the guidance provided by ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below tables outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Entra admin portal at the following URL:

<https://entra.microsoft.com/#view/Microsoft_AAD_ConditionalAccess/ConditionalAccessBlade/~/NamedLocations/fromNav/>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Countries location

| Item                              |                                            Value |
| --------------------------------- | -----------------------------------------------: |
| **Name**                          |                                Allowed Countries |
| Country lookup method             | Determine location by IP address (IPv4 and IPv6) |
| Include unknown countries/regions |                                      Not checked |
| Name                              |                                        Australia |

### IP ranges location location

| Item                     |                          Value |
| ------------------------ | -----------------------------: |
| **Name**                 |                    Trusted IPs |
| Mark as trusted location |                        Checked |
| IPv4 or IPv6 range       | _Relevant IPv4 or IPv6 ranges_ |

### Related information

#### Security and governance

- [Multi-factor authentication](/security-and-governance/essential-eight/multi-factor-authentication)
- [Authentication hardening](/security-and-governance/system-security-plan/system-hardening-authentication)

#### Design

- [Conditional access](/design/platform/identity/conditional-access)
- [Purview labels](/design/shared-services/purview/labelling-and-classification)
- [Organisation Residency](/design/shared-services/microsoft-365/residency)

#### Configuration

- [Endpoint security policies](/configuration/defender/endpoints/configuration-management/endpoint-security-policies)

#### References

- [Conditional Access: Target resources](https://learn.microsoft.com/entra/identity/conditional-access/concept-conditional-access-cloud-apps#authentication-context)
