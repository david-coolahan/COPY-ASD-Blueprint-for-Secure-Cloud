---
title: "Compliance Manager"
weight: 50
description: "This section describes the design decisions associated with Compliance Manager with Microsoft Purview for system(s) built using ASD's Blueprint for Secure Cloud."
---

Compliance Manager helps automatically assess and manage compliance across Microsoft 365 services, apps and endpoints by assessing their configurations against common industry standards and regulations. These standards and regulations are implemented as _assessments_ that are comprised of a set of requirements, known as _controls_, that relate to specific configurations. Controls are described alongside improvement actions to address configuration compliance, with compliance status being reported and alerts able to be generated for configuration changes.

Assessments exist for many different Australian and international standards and regulations, including for ASD's _Essential Eight maturity model_ and _Information Security Manual_ (ISM), and while both assessments are based on older frameworks they still provide significant and relevant compliance advice and so are recommended for implementation.

{{% alert title="Design decisions" color="warning" %}}

| Decision point                       | Design decision                                                    | Justification                                                     |
| ------------------------------------ | ------------------------------------------------------------------ | ----------------------------------------------------------------- |
| Using Compliance Manager assessments | Add assessments for ASD's _Essential Eight maturity model_ and ISM | Facilitate security compliance reporting and configuration advice |

{{% /alert %}}

### Related information

#### Security and governance

- None identified

#### Design

- None identified

#### Configuration

- [Compliance Manager](/configuration/purview/compliance-manager)

#### References

- [_Essential Eight maturity model_](https://www.cyber.gov.au/resources-business-and-government/essential-cyber-security/essential-eight/essential-eight-maturity-model)
- [_Information Security Manual_ (ISM)](https://www.cyber.gov.au/resources-business-and-government/essential-cyber-security/ism)
- [Microsoft Purview Compliance Manager](https://learn.microsoft.com/en-au/purview/compliance-manager)
