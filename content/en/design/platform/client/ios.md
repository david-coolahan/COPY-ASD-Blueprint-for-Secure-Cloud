---
title: iOS
weight: 35
description: "This section describes the design decisions associated with the management of Applications deployed to endpoints for system(s) built using ASD's Blueprint for Secure Cloud."
---

iOS devices are enrolled with the Microsoft Intune portal to gain secure access to organisational data. After devices are enrolled, they become `MANAGED`. Organisations can assign policies and apps to the device through a Mobile Device Management (MDM) provider, such as Microsoft Intune.

{{% alert title="Design decisions" color="warning" %}}

| Decision point    | Design decision                                                                                              | Justification                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| iOS Enrolment     | Configured                                                                                                   | iOS is commonly deployed across the Australian Government and can be hardened in line with Apples hardening guide for iOS devices. |
| iOS Configuration | Configurations will follow Apples hardening guide for iOS devices as much as possible using Microsoft Intune | Aligns with Apple iOS hardening guidance.                                                                                          |

{{% /alert %}}

{{% alert title="Note" color="info" %}}

ASD’s _Blueprint for Secure Cloud_ (the Blueprint) recommends organisations secure iOS for devices based on a variety of hardening guidance including the United States' (US) National Information Assurance Partnership [_Protection Profile for Mobile Device Fundamentals version 3.3_](https://www.niap-ccevs.org/Profile/Info.cfm?PPID=468&id=468), the US Department of Defence's [_Cyber Exchange Security Technical Implementation Guides (STIGs)_](https://public.cyber.mil/stigs/downloads), the Centre for Internet Security's(CIS) [_Apple iOS Benchmarks_](https://www.cisecurity.org/benchmark/apple_ios), and ASD's [_Security Configuration Guidance for Apple iOS Devices_](https://www.cyber.gov.au/acsc/view-all-content/publications/security-configuration-guide-apple-ios-14-devices) to provide secure access to corporate information.

{{% /alert %}}

### Related information

#### Security and governance

- [Enterprise mobility](/security-and-governance/system-security-plan/enterprise-mobility)

#### Design

- None identified

#### Configuration

- [ASD iOS hardening](/configuration/intune/devices/apple-updates/asd-ios-hardening)
- [iOS and iPadOS](/configuration/intune/apps/by-platform/ios-ipados)

#### References

- None identified
