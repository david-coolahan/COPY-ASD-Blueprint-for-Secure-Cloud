---
title: "OLE hardening"
weight: 50
description: "This section describes the design decisions associated with Object Linking and Embedding (OLE) on Windows 10 and 11 endpoints configured according to guidance in ASD's Blueprint for Secure Cloud."
---

Object Linking and Embedding (OLE) is a functionality within Microsoft Office which enables the embedding and linking to documents and other objects. OLE is utilised to seamlessly integrate several types of data or components within a Microsoft Office file.

Adversaries have leveraged the OLE functionality to enable and download malicious content or execute a malicious payload. Within Microsoft Office 365 and Microsoft Office 2019 clients, the activation of objects that link to extensions that are considered high risk are blocked from executing. The list of high risk extensions can be configured through the use of Intune or GPOs.

ASD's provides guidance around securing systems against malicious OLE packages and recommend they are implemented in all Windows environments. The guidance is to block all OLE packages from executing in Word, PowerPoint, and Excel.

{{% alert title="Design decisions" color="warning" %}}

| Decision point    | Design decision | Justification                                                                                                                                                                                                                                                  |
| ----------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OLE configuration | Block all       | To align with the ASD's [_Restricting Microsoft Office Macros_](https://www.cyber.gov.au/resources-business-and-government/maintaining-devices-and-systems/system-hardening-and-administration/system-hardening/restricting-microsoft-office-macros) guidance. |

{{% /alert %}}

### Related information

#### Security and governance

- [Microsoft Office macro hardening](/security-and-governance/essential-eight/restrict-microsoft-office-macros)
- [Essential Eight - Application control](/security-and-governance/essential-eight/application-control)
- [Essential Eight - Restrict Microsoft Office macros](/security-and-governance/essential-eight/restrict-microsoft-office-macros)

#### Design

- None identified

#### Configuration

- [Microsoft Office macro hardening](/design/endpoints/windows/security/microsoft-office-macro-hardening)

#### References

- None identified
