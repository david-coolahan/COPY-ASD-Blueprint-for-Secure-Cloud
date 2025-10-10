---
title: "Add PSPF X-header and subject marking"
weight: 010
description: "This section describes the configuration of Data Loss Prevention policies within Microsoft Purview associated with systems built according to guidance in ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below pages outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Purview portal at the following URL:

<https://purview.microsoft.com/datalossprevention/policies>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

[//]: # "                                         * * * * * Note * * * * *                                                           "
[//]: # "                                                                                                                            "
[//]: # " Regular expressions in tables include extra escape characters for formatting, do not copy and paste them from raw markdown "
[//]: # "                                                                                                                            "
[//]: # "                                         * * * * * Note * * * * *                                                           "

### Data to protect

#### Choose what type of data to protect

| Item                             |    Value |
| -------------------------------- | -------: |
| Data stored in connected sources | Selected |

### Name

#### Name your DLP policy

| Item        |                                                                            Value |
| ----------- | -------------------------------------------------------------------------------: |
| Name        |                                  Add PSPF X-header and subject marking to emails |
| Description | Apply PSPF markings to the email X-Protective-Marking X-header and email subject |

### Admin units

#### Assign admin units

| Item        |          Value |
| ----------- | -------------: |
| Admin units | Full directory |

### Locations

#### Choose where to apply the policy

| Item                            |       Value |
| ------------------------------- | ----------: |
| Exchange email                  |  All groups |
| SharePoint sites                | Not checked |
| OneDrive accounts               | Not checked |
| Teams chat and channel messages | Not checked |
| Devices                         | Not checked |
| Instances                       | Not checked |
| On-premises repositories        | Not checked |
| Fabric and Power BI workspaces  | Not checked |
| Microsoft 365 Copilot           | Not checked |

### Policy settings

| Item                   |                                  Value |
| ---------------------- | -------------------------------------: |
| Define policy settings | Create or customize advanced DLP rules |

#### Advanced DLP rules

{{% alert title="Subject replacement text" color="warning" %}}

1: The _modify subject_ replacement text values must have a leading whitespace character before the `[SEC=`.

{{% /alert %}}

{{% alert title="Regular expressions in DLP rules" color="info" %}}

Unlike other Purview configurations, DLP rules do not support the use of commas in regular expressions: commas (`,`) have been replaced by the unicode expression `\u002C`.

{{% /alert %}}

**_Rule index:_**

- [Mark UNOFFICIAL X-header](#mark-unofficial-x-header)
- [Mark UNOFFICIAL subject](#mark-unofficial-subject)
- [Mark OFFICIAL X-header](#mark-official-x-header)
- [Mark OFFICIAL subject](#mark-official-subject)
- [Mark OS X-header](#mark-os-x-header)
- [Mark OS subject](#mark-os-subject)
- [Mark OS PP X-header](#mark-os-pp-x-header)
- [Mark OS PP subject](#mark-os-pp-subject)
- [Mark OS LP X-header](#mark-os-lp-x-header)
- [Mark OS LP subject](#mark-os-lp-subject)
- [Mark OS LS X-header](#mark-os-ls-x-header)
- [Mark OS LS subject](#mark-os-ls-subject)
- [Mark PROTECTED X-header](#mark-protected-x-header)
- [Mark PROTECTED subject](#mark-protected-subject)
- [Mark P PP X-header](#mark-p-pp-x-header)
- [Mark P PP subject](#mark-p-pp-subject)
- [Mark P LP X-header](#mark-p-lp-x-header)
- [Mark P LP subject](#mark-p-lp-subject)
- [Mark P LS X-header](#mark-p-ls-x-header)
- [Mark P LS subject](#mark-p-ls-subject)
- [Mark P C X-header](#mark-p-c-x-header)
- [Mark P C subject](#mark-p-c-subject)
- [Mark P C PP X-header](#mark-p-c-pp-x-header)
- [Mark P C PP subject](#mark-p-c-pp-subject)
- [Mark P C LP X-header](#mark-p-c-lp-x-header)
- [Mark P C LP subject](#mark-p-c-lp-subject)
- [Mark P C LS X-header](#mark-p-c-ls-x-header)
- [Mark P C LS subject](#mark-p-c-ls-subject)

##### Mark UNOFFICIAL X-header

| Item                                                                                                                                |                                                                                       Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                    Mark UNOFFICIAL X-header |
| Description                                                                                                                         |                                                                                      _None_ |
| **Conditions**                                                                                                                      |                                                                                             |
| Content contains                                                                                                                    |                                                                                             |
| - Group name                                                                                                                        |                                                                                     Default |
| - Group operator                                                                                                                    |                                                                                Any of these |
| - Sensitivity labels                                                                                                                |                                                                                  UNOFFICIAL |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                       Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                             |
| **NOT**                                                                                                                             |                                                                                             |
| **Conditions**                                                                                                                      |                                                                                             |
| Header matches patterns                                                                                                             |                                                    X-Protective-Marking<br>`SEC=UNOFFICIAL` |
| **Actions**                                                                                                                         |                                                                                             |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=UNOFFICIAL, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                             |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                         Off |
| **User overrides**                                                                                                                  |                                                                                             |
| Allow overrides from M365 services                                                                                                  |                                                                                 Not checked |
| **Incident reports**                                                                                                                |                                                                                             |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                         Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                         Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                         Off |
| **Additional options**                                                                                                              |                                                                                             |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                 Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                         Off |
| Priority                                                                                                                            |                                                                                           0 |

##### Mark UNOFFICIAL subject

| Item                                                                                                                                |                                                 Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------: |
| Name                                                                                                                                |                               Mark UNOFFICIAL subject |
| Description                                                                                                                         |                                                _None_ |
| **Conditions**                                                                                                                      |                                                       |
| Content contains                                                                                                                    |                                                       |
| - Group name                                                                                                                        |                                               Default |
| - Group operator                                                                                                                    |                                          Any of these |
| - Sensitivity labels                                                                                                                |                                            UNOFFICIAL |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                 Message or attachment |
| **Actions**                                                                                                                         |                                                       |
| Modify subject                                                                                                                      |                                                       |
| - Remove text that matches                                                                                                          |                                     `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      |                  &nbsp;`[SEC=UNOFFICIAL]`<sup>1</sup> |
| - Position                                                                                                                          | Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                       |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                   Off |
| **User overrides**                                                                                                                  |                                                       |
| Allow overrides from M365 services                                                                                                  |                                           Not checked |
| **Incident reports**                                                                                                                |                                                       |
| Use this severity level in admin alerts and reports:                                                                                |                                                   Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                   Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                   Off |
| **Additional options**                                                                                                              |                                                       |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                           Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                   Off |
| Priority                                                                                                                            |                                                     1 |

##### Mark OFFICIAL X-header

| Item                                                                                                                                |                                                                                     Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                    Mark OFFICIAL X-header |
| Description                                                                                                                         |                                                                                    _None_ |
| **Conditions**                                                                                                                      |                                                                                           |
| Content contains                                                                                                                    |                                                                                           |
| - Group name                                                                                                                        |                                                                                   Default |
| - Group operator                                                                                                                    |                                                                              Any of these |
| - Sensitivity labels                                                                                                                |                                                                                  OFFICIAL |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                     Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                           |
| **NOT**                                                                                                                             |                                                                                           |
| **Conditions**                                                                                                                      |                                                                                           |
| Header matches patterns                                                                                                             |                                      X-Protective-Marking<br>`SEC=OFFICIAL(?!:Sensitive)` |
| **Actions**                                                                                                                         |                                                                                           |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=OFFICIAL, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                           |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                       Off |
| **User overrides**                                                                                                                  |                                                                                           |
| Allow overrides from M365 services                                                                                                  |                                                                               Not checked |
| **Incident reports**                                                                                                                |                                                                                           |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                       Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                       Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                       Off |
| **Additional options**                                                                                                              |                                                                                           |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                               Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                       Off |
| Priority                                                                                                                            |                                                                                         2 |

##### Mark OFFICIAL subject

| Item                                                                                                                                |                                                 Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------: |
| Name                                                                                                                                |                                 Mark OFFICIAL subject |
| Description                                                                                                                         |                                                _None_ |
| **Conditions**                                                                                                                      |                                                       |
| Content contains                                                                                                                    |                                                       |
| - Group name                                                                                                                        |                                               Default |
| - Group operator                                                                                                                    |                                          Any of these |
| - Sensitivity labels                                                                                                                |                                              OFFICIAL |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                 Message or attachment |
| **Actions**                                                                                                                         |                                                       |
| Modify subject                                                                                                                      |                                                       |
| - Remove text that matches                                                                                                          |                                     `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      |                    &nbsp;`[SEC=OFFICIAL]`<sup>1</sup> |
| - Position                                                                                                                          | Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                       |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                   Off |
| **User overrides**                                                                                                                  |                                                       |
| Allow overrides from M365 services                                                                                                  |                                           Not checked |
| **Incident reports**                                                                                                                |                                                       |
| Use this severity level in admin alerts and reports:                                                                                |                                                   Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                   Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                   Off |
| **Additional options**                                                                                                              |                                                       |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                           Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                   Off |
| Priority                                                                                                                            |                                                     3 |

##### Mark OS X-header

| Item                                                                                                                                |                                                                                                Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                     Mark OS X-header |
| Description                                                                                                                         |                                                                                               _None_ |
| **Conditions**                                                                                                                      |                                                                                                      |
| Content contains                                                                                                                    |                                                                                                      |
| - Group name                                                                                                                        |                                                                                              Default |
| - Group operator                                                                                                                    |                                                                                         Any of these |
| - Sensitivity labels                                                                                                                |                                                        OFFICIAL Sensitive (group)/OFFICIAL Sensitive |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                      |
| **NOT**                                                                                                                             |                                                                                                      |
| **Conditions**                                                                                                                      |                                                                                                      |
| Header matches patterns                                                                                                             | X-Protective-Marking<br>`SEC=OFFICIAL:Sensitive(?!\u002C CAVEAT=\|[a-zA-Z\u002C= /]*\u002C ACCESS=)` |
| **Actions**                                                                                                                         |                                                                                                      |
| Set headers                                                                                                                         |  `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=OFFICIAL:Sensitive, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                      |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                  Off |
| **User overrides**                                                                                                                  |                                                                                                      |
| Allow overrides from M365 services                                                                                                  |                                                                                          Not checked |
| **Incident reports**                                                                                                                |                                                                                                      |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                  Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                  Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                  Off |
| **Additional options**                                                                                                              |                                                                                                      |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                          Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                  Off |
| Priority                                                                                                                            |                                                                                                    4 |

##### Mark OS subject

| Item                                                                                                                                |                                                 Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------: |
| Name                                                                                                                                |                                       Mark OS subject |
| Description                                                                                                                         |                                                _None_ |
| **Conditions**                                                                                                                      |                                                       |
| Content contains                                                                                                                    |                                                       |
| - Group name                                                                                                                        |                                               Default |
| - Group operator                                                                                                                    |                                          Any of these |
| - Sensitivity labels                                                                                                                |         OFFICIAL Sensitive (group)/OFFICIAL Sensitive |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                 Message or attachment |
| **Actions**                                                                                                                         |                                                       |
| Modify subject                                                                                                                      |                                                       |
| - Remove text that matches                                                                                                          |                                     `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      |          &nbsp;`[SEC=OFFICIAL:Sensitive]`<sup>1</sup> |
| - Position                                                                                                                          | Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                       |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                   Off |
| **User overrides**                                                                                                                  |                                                       |
| Allow overrides from M365 services                                                                                                  |                                           Not checked |
| **Incident reports**                                                                                                                |                                                       |
| Use this severity level in admin alerts and reports:                                                                                |                                                   Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                   Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                   Off |
| **Additional options**                                                                                                              |                                                       |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                           Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                   Off |
| Priority                                                                                                                            |                                                     5 |

##### Mark OS PP X-header

| Item                                                                                                                                |                                                                                                                        Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                          Mark OS PP X-header |
| Description                                                                                                                         |                                                                                                                       _None_ |
| **Conditions**                                                                                                                      |                                                                                                                              |
| Content contains                                                                                                                    |                                                                                                                              |
| - Group name                                                                                                                        |                                                                                                                      Default |
| - Group operator                                                                                                                    |                                                                                                                 Any of these |
| - Sensitivity labels                                                                                                                |                                                                                  OFFICIAL Sensitive (group)/Personal Privacy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                                        Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                              |
| **NOT**                                                                                                                             |                                                                                                                              |
| **Conditions**                                                                                                                      |                                                                                                                              |
| Header matches patterns                                                                                                             |                           X-Protective-Marking<br>`SEC=OFFICIAL:Sensitive(?!\u002C CAVEAT=).*\u002C ACCESS=Personal-Privacy` |
| **Actions**                                                                                                                         |                                                                                                                              |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=OFFICIAL:Sensitive, ACCESS=Personal-Privacy, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                              |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                          Off |
| **User overrides**                                                                                                                  |                                                                                                                              |
| Allow overrides from M365 services                                                                                                  |                                                                                                                  Not checked |
| **Incident reports**                                                                                                                |                                                                                                                              |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                          Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                          Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                          Off |
| **Additional options**                                                                                                              |                                                                                                                              |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                                  Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                          Off |
| Priority                                                                                                                            |                                                                                                                            6 |

##### Mark OS PP subject

| Item                                                                                                                                |                                                                 Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------: |
| Name                                                                                                                                |                                                    Mark OS PP subject |
| Description                                                                                                                         |                                                                _None_ |
| **Conditions**                                                                                                                      |                                                                       |
| Content contains                                                                                                                    |                                                                       |
| - Group name                                                                                                                        |                                                               Default |
| - Group operator                                                                                                                    |                                                          Any of these |
| - Sensitivity labels                                                                                                                |                           OFFICIAL Sensitive (group)/Personal Privacy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                 Message or attachment |
| **Actions**                                                                                                                         |                                                                       |
| Modify subject                                                                                                                      |                                                                       |
| - Remove text that matches                                                                                                          |                                                     `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=OFFICIAL:Sensitive, ACCESS=Personal-Privacy]`<sup>1</sup> |
| - Position                                                                                                                          |                 Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                                       |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                   Off |
| **User overrides**                                                                                                                  |                                                                       |
| Allow overrides from M365 services                                                                                                  |                                                           Not checked |
| **Incident reports**                                                                                                                |                                                                       |
| Use this severity level in admin alerts and reports:                                                                                |                                                                   Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                   Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                   Off |
| **Additional options**                                                                                                              |                                                                       |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                           Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                   Off |
| Priority                                                                                                                            |                                                                     7 |

##### Mark OS LP X-header

| Item                                                                                                                                |                                                                                                                       Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                         Mark OS LP X-header |
| Description                                                                                                                         |                                                                                                                      _None_ |
| **Conditions**                                                                                                                      |                                                                                                                             |
| Content contains                                                                                                                    |                                                                                                                             |
| - Group name                                                                                                                        |                                                                                                                     Default |
| - Group operator                                                                                                                    |                                                                                                                Any of these |
| - Sensitivity labels                                                                                                                |                                                                                  OFFICIAL Sensitive (group)/Legal Privilege |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                                       Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                             |
| **NOT**                                                                                                                             |                                                                                                                             |
| **Conditions**                                                                                                                      |                                                                                                                             |
| Header matches patterns                                                                                                             |                           X-Protective-Marking<br>`SEC=OFFICIAL:Sensitive(?!\u002C CAVEAT=).*\u002C ACCESS=Legal-Privilege` |
| **Actions**                                                                                                                         |                                                                                                                             |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=OFFICIAL:Sensitive, ACCESS=Legal-Privilege, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                             |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                         Off |
| **User overrides**                                                                                                                  |                                                                                                                             |
| Allow overrides from M365 services                                                                                                  |                                                                                                                 Not checked |
| **Incident reports**                                                                                                                |                                                                                                                             |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                         Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                         Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                         Off |
| **Additional options**                                                                                                              |                                                                                                                             |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                                 Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                         Off |
| Priority                                                                                                                            |                                                                                                                           8 |

##### Mark OS LP subject

| Item                                                                                                                                |                                                                Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------: |
| Name                                                                                                                                |                                                   Mark OS LP subject |
| Description                                                                                                                         |                                                               _None_ |
| **Conditions**                                                                                                                      |                                                                      |
| Content contains                                                                                                                    |                                                                      |
| - Group name                                                                                                                        |                                                              Default |
| - Group operator                                                                                                                    |                                                         Any of these |
| - Sensitivity labels                                                                                                                |                           OFFICIAL Sensitive (group)/Legal Privilege |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                Message or attachment |
| **Actions**                                                                                                                         |                                                                      |
| Modify subject                                                                                                                      |                                                                      |
| - Remove text that matches                                                                                                          |                                                    `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=OFFICIAL:Sensitive, ACCESS=Legal-Privilege]`<sup>1</sup> |
| - Position                                                                                                                          |                Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                                      |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                  Off |
| **User overrides**                                                                                                                  |                                                                      |
| Allow overrides from M365 services                                                                                                  |                                                          Not checked |
| **Incident reports**                                                                                                                |                                                                      |
| Use this severity level in admin alerts and reports:                                                                                |                                                                  Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                  Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                  Off |
| **Additional options**                                                                                                              |                                                                      |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                          Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                  Off |
| Priority                                                                                                                            |                                                                    9 |

##### Mark OS LS X-header

| Item                                                                                                                                |                                                                                                                           Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                             Mark OS LS X-header |
| Description                                                                                                                         |                                                                                                                          _None_ |
| **Conditions**                                                                                                                      |                                                                                                                                 |
| Content contains                                                                                                                    |                                                                                                                                 |
| - Group name                                                                                                                        |                                                                                                                         Default |
| - Group operator                                                                                                                    |                                                                                                                    Any of these |
| - Sensitivity labels                                                                                                                |                                                                                  OFFICIAL Sensitive (group)/Legislative Secrecy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                                           Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                                 |
| **NOT**                                                                                                                             |                                                                                                                                 |
| **Conditions**                                                                                                                      |                                                                                                                                 |
| Header matches patterns                                                                                                             |                           X-Protective-Marking<br>`SEC=OFFICIAL:Sensitive(?!\u002C CAVEAT=).*\u002C ACCESS=Legislative-Secrecy` |
| **Actions**                                                                                                                         |                                                                                                                                 |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=OFFICIAL:Sensitive, ACCESS=Legislative-Secrecy, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                                 |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                             Off |
| **User overrides**                                                                                                                  |                                                                                                                                 |
| Allow overrides from M365 services                                                                                                  |                                                                                                                     Not checked |
| **Incident reports**                                                                                                                |                                                                                                                                 |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                             Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                             Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                             Off |
| **Additional options**                                                                                                              |                                                                                                                                 |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                                     Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                             Off |
| Priority                                                                                                                            |                                                                                                                              10 |

##### Mark OS LS subject

| Item                                                                                                                                |                                                                    Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | -----------------------------------------------------------------------: |
| Name                                                                                                                                |                                                       Mark OS LS subject |
| Description                                                                                                                         |                                                                   _None_ |
| **Conditions**                                                                                                                      |                                                                          |
| Content contains                                                                                                                    |                                                                          |
| - Group name                                                                                                                        |                                                                  Default |
| - Group operator                                                                                                                    |                                                             Any of these |
| - Sensitivity labels                                                                                                                |                           OFFICIAL Sensitive (group)/Legislative Secrecy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                    Message or attachment |
| **Actions**                                                                                                                         |                                                                          |
| Modify subject                                                                                                                      |                                                                          |
| - Remove text that matches                                                                                                          |                                                        `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=OFFICIAL:Sensitive, ACCESS=Legislative-Secrecy]`<sup>1</sup> |
| - Position                                                                                                                          |                    Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                                          |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                      Off |
| **User overrides**                                                                                                                  |                                                                          |
| Allow overrides from M365 services                                                                                                  |                                                              Not checked |
| **Incident reports**                                                                                                                |                                                                          |
| Use this severity level in admin alerts and reports:                                                                                |                                                                      Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                      Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                      Off |
| **Additional options**                                                                                                              |                                                                          |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                              Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                      Off |
| Priority                                                                                                                            |                                                                       11 |

##### Mark PROTECTED X-header

| Item                                                                                                                                |                                                                                       Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                     Mark PROTECTED X-header |
| Description                                                                                                                         |                                                                                      _None_ |
| **Conditions**                                                                                                                      |                                                                                             |
| Content contains                                                                                                                    |                                                                                             |
| - Group name                                                                                                                        |                                                                                     Default |
| - Group operator                                                                                                                    |                                                                                Any of these |
| - Sensitivity labels                                                                                                                |                                                                 PROTECTED (group)/PROTECTED |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                       Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                             |
| **NOT**                                                                                                                             |                                                                                             |
| **Conditions**                                                                                                                      |                                                                                             |
| Header matches patterns                                                                                                             | X-Protective-Marking<br>`SEC=PROTECTED(?!\u002C CAVEAT=\|[a-zA-Z\u002C= /]*\u002C ACCESS=)` |
| **Actions**                                                                                                                         |                                                                                             |
| Set headers                                                                                                                         |  `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=PROTECTED, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                             |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                         Off |
| **User overrides**                                                                                                                  |                                                                                             |
| Allow overrides from M365 services                                                                                                  |                                                                                 Not checked |
| **Incident reports**                                                                                                                |                                                                                             |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                         Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                         Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                         Off |
| **Additional options**                                                                                                              |                                                                                             |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                 Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                         Off |
| Priority                                                                                                                            |                                                                                          20 |

##### Mark PROTECTED subject

| Item                                                                                                                                |                                                 Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------: |
| Name                                                                                                                                |                                Mark PROTECTED subject |
| Description                                                                                                                         |                                                _None_ |
| **Conditions**                                                                                                                      |                                                       |
| Content contains                                                                                                                    |                                                       |
| - Group name                                                                                                                        |                                               Default |
| - Group operator                                                                                                                    |                                          Any of these |
| - Sensitivity labels                                                                                                                |                           PROTECTED (group)/PROTECTED |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                 Message or attachment |
| **Actions**                                                                                                                         |                                                       |
| Modify subject                                                                                                                      |                                                       |
| - Remove text that matches                                                                                                          |                                     `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      |                   &nbsp;`[SEC=PROTECTED]`<sup>1</sup> |
| - Position                                                                                                                          | Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                       |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                   Off |
| **User overrides**                                                                                                                  |                                                       |
| Allow overrides from M365 services                                                                                                  |                                           Not checked |
| **Incident reports**                                                                                                                |                                                       |
| Use this severity level in admin alerts and reports:                                                                                |                                                   Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                   Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                   Off |
| **Additional options**                                                                                                              |                                                       |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                           Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                   Off |
| Priority                                                                                                                            |                                                    21 |

##### Mark P PP X-header

| Item                                                                                                                                |                                                                                                               Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                  Mark P PP X-header |
| Description                                                                                                                         |                                                                                                              _None_ |
| **Conditions**                                                                                                                      |                                                                                                                     |
| Content contains                                                                                                                    |                                                                                                                     |
| - Group name                                                                                                                        |                                                                                                             Default |
| - Group operator                                                                                                                    |                                                                                                        Any of these |
| - Sensitivity labels                                                                                                                |                                                                                  PROTECTED (group)/Personal Privacy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                               Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                     |
| **NOT**                                                                                                                             |                                                                                                                     |
| **Conditions**                                                                                                                      |                                                                                                                     |
| Header matches patterns                                                                                                             |                            X-Protective-Marking<br>`SEC=PROTECTED(?!\u002C CAVEAT).*\u002C ACCESS=Personal-Privacy` |
| **Actions**                                                                                                                         |                                                                                                                     |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=PROTECTED, ACCESS=Personal-Privacy, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                     |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                 Off |
| **User overrides**                                                                                                                  |                                                                                                                     |
| Allow overrides from M365 services                                                                                                  |                                                                                                         Not checked |
| **Incident reports**                                                                                                                |                                                                                                                     |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                 Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                 Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                 Off |
| **Additional options**                                                                                                              |                                                                                                                     |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                         Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                 Off |
| Priority                                                                                                                            |                                                                                                                  22 |

##### Mark P PP subject

| Item                                                                                                                                |                                                        Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | -----------------------------------------------------------: |
| Name                                                                                                                                |                                            Mark P PP subject |
| Description                                                                                                                         |                                                       _None_ |
| **Conditions**                                                                                                                      |                                                              |
| Content contains                                                                                                                    |                                                              |
| - Group name                                                                                                                        |                                                      Default |
| - Group operator                                                                                                                    |                                                 Any of these |
| - Sensitivity labels                                                                                                                |                           PROTECTED (group)/Personal Privacy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                        Message or attachment |
| **Actions**                                                                                                                         |                                                              |
| Modify subject                                                                                                                      |                                                              |
| - Remove text that matches                                                                                                          |                                            `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=PROTECTED, ACCESS=Personal-Privacy]`<sup>1</sup> |
| - Position                                                                                                                          |        Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                              |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                          Off |
| **User overrides**                                                                                                                  |                                                              |
| Allow overrides from M365 services                                                                                                  |                                                  Not checked |
| **Incident reports**                                                                                                                |                                                              |
| Use this severity level in admin alerts and reports:                                                                                |                                                          Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                          Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                          Off |
| **Additional options**                                                                                                              |                                                              |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                  Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                          Off |
| Priority                                                                                                                            |                                                           23 |

##### Mark P LP X-header

| Item                                                                                                                                |                                                                                                              Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                 Mark P LP X-header |
| Description                                                                                                                         |                                                                                                             _None_ |
| **Conditions**                                                                                                                      |                                                                                                                    |
| Content contains                                                                                                                    |                                                                                                                    |
| - Group name                                                                                                                        |                                                                                                            Default |
| - Group operator                                                                                                                    |                                                                                                       Any of these |
| - Sensitivity labels                                                                                                                |                                                                                  PROTECTED (group)/Legal Privilege |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                              Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                    |
| **NOT**                                                                                                                             |                                                                                                                    |
| **Conditions**                                                                                                                      |                                                                                                                    |
| Header matches patterns                                                                                                             |                            X-Protective-Marking<br>`SEC=PROTECTED(?!\u002C CAVEAT).*\u002C ACCESS=Legal-Privilege` |
| **Actions**                                                                                                                         |                                                                                                                    |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=PROTECTED, ACCESS=Legal-Privilege, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                    |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                Off |
| **User overrides**                                                                                                                  |                                                                                                                    |
| Allow overrides from M365 services                                                                                                  |                                                                                                        Not checked |
| **Incident reports**                                                                                                                |                                                                                                                    |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                Off |
| **Additional options**                                                                                                              |                                                                                                                    |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                        Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                Off |
| Priority                                                                                                                            |                                                                                                                 24 |

##### Mark P LP subject

| Item                                                                                                                                |                                                       Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------: |
| Name                                                                                                                                |                                           Mark P LP subject |
| Description                                                                                                                         |                                                      _None_ |
| **Conditions**                                                                                                                      |                                                             |
| Content contains                                                                                                                    |                                                             |
| - Group name                                                                                                                        |                                                     Default |
| - Group operator                                                                                                                    |                                                Any of these |
| - Sensitivity labels                                                                                                                |                           PROTECTED (group)/Legal Privilege |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                       Message or attachment |
| **Actions**                                                                                                                         |                                                             |
| Modify subject                                                                                                                      |                                                             |
| - Remove text that matches                                                                                                          |                                           `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=PROTECTED, ACCESS=Legal-Privilege]`<sup>1</sup> |
| - Position                                                                                                                          |       Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                             |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                         Off |
| **User overrides**                                                                                                                  |                                                             |
| Allow overrides from M365 services                                                                                                  |                                                 Not checked |
| **Incident reports**                                                                                                                |                                                             |
| Use this severity level in admin alerts and reports:                                                                                |                                                         Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                         Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                         Off |
| **Additional options**                                                                                                              |                                                             |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                 Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                         Off |
| Priority                                                                                                                            |                                                          25 |

##### Mark P LS X-header

| Item                                                                                                                                |                                                                                                                  Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                     Mark P LS X-header |
| Description                                                                                                                         |                                                                                                                 _None_ |
| **Conditions**                                                                                                                      |                                                                                                                        |
| Content contains                                                                                                                    |                                                                                                                        |
| - Group name                                                                                                                        |                                                                                                                Default |
| - Group operator                                                                                                                    |                                                                                                           Any of these |
| - Sensitivity labels                                                                                                                |                                                                                  PROTECTED (group)/Legislative Secrecy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                                  Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                        |
| **NOT**                                                                                                                             |                                                                                                                        |
| **Conditions**                                                                                                                      |                                                                                                                        |
| Header matches patterns                                                                                                             |                            X-Protective-Marking<br>`SEC=PROTECTED(?!\u002C CAVEAT).*\u002C ACCESS=Legislative-Secrecy` |
| **Actions**                                                                                                                         |                                                                                                                        |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=PROTECTED, ACCESS=Legislative-Secrecy, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                        |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                    Off |
| **User overrides**                                                                                                                  |                                                                                                                        |
| Allow overrides from M365 services                                                                                                  |                                                                                                            Not checked |
| **Incident reports**                                                                                                                |                                                                                                                        |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                    Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                    Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                    Off |
| **Additional options**                                                                                                              |                                                                                                                        |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                            Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                    Off |
| Priority                                                                                                                            |                                                                                                                     26 |

##### Mark P LS subject

| Item                                                                                                                                |                                                           Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------: |
| Name                                                                                                                                |                                               Mark P LS subject |
| Description                                                                                                                         |                                                          _None_ |
| **Conditions**                                                                                                                      |                                                                 |
| Content contains                                                                                                                    |                                                                 |
| - Group name                                                                                                                        |                                                         Default |
| - Group operator                                                                                                                    |                                                    Any of these |
| - Sensitivity labels                                                                                                                |                           PROTECTED (group)/Legislative Secrecy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                           Message or attachment |
| **Actions**                                                                                                                         |                                                                 |
| Modify subject                                                                                                                      |                                                                 |
| - Remove text that matches                                                                                                          |                                               `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=PROTECTED, ACCESS=Legislative-Secrecy]`<sup>1</sup> |
| - Position                                                                                                                          |           Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                                 |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                             Off |
| **User overrides**                                                                                                                  |                                                                 |
| Allow overrides from M365 services                                                                                                  |                                                     Not checked |
| **Incident reports**                                                                                                                |                                                                 |
| Use this severity level in admin alerts and reports:                                                                                |                                                             Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                             Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                             Off |
| **Additional options**                                                                                                              |                                                                 |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                     Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                             Off |
| Priority                                                                                                                            |                                                              27 |

##### Mark P C X-header

| Item                                                                                                                                |                                                                                                         Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                             Mark P C X-header |
| Description                                                                                                                         |                                                                                                        _None_ |
| **Conditions**                                                                                                                      |                                                                                                               |
| Content contains                                                                                                                    |                                                                                                               |
| - Group name                                                                                                                        |                                                                                                       Default |
| - Group operator                                                                                                                    |                                                                                                  Any of these |
| - Sensitivity labels                                                                                                                |                                                                  PROTECTED CABINET (group)/ PROTECTED CABINET |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                         Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                               |
| **NOT**                                                                                                                             |                                                                                                               |
| **Conditions**                                                                                                                      |                                                                                                               |
| Header matches patterns                                                                                                             |           X-Protective-Marking<br>`SEC=PROTECTED\u002C CAVEAT=SH:CABINET(?![a-zA-Z\u002C= /]*\u002C ACCESS=)` |
| **Actions**                                                                                                                         |                                                                                                               |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=PROTECTED, CAVEAT=SH:CABINET, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                               |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                           Off |
| **User overrides**                                                                                                                  |                                                                                                               |
| Allow overrides from M365 services                                                                                                  |                                                                                                   Not checked |
| **Incident reports**                                                                                                                |                                                                                                               |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                           Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                           Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                           Off |
| **Additional options**                                                                                                              |                                                                                                               |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                   Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                           Off |
| Priority                                                                                                                            |                                                                                                            36 |

##### Mark P C subject

| Item                                                                                                                                |                                                  Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | -----------------------------------------------------: |
| Name                                                                                                                                |                                       Mark P C subject |
| Description                                                                                                                         |                                                 _None_ |
| **Conditions**                                                                                                                      |                                                        |
| Content contains                                                                                                                    |                                                        |
| - Group name                                                                                                                        |                                                Default |
| - Group operator                                                                                                                    |                                           Any of these |
| - Sensitivity labels                                                                                                                |            PROTECTED CABINET (group)/PROTECTED CABINET |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                  Message or attachment |
| **Actions**                                                                                                                         |                                                        |
| Modify subject                                                                                                                      |                                                        |
| - Remove text that matches                                                                                                          |                                      `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=PROTECTED, CAVEAT=SH:CABINET]`<sup>1</sup> |
| - Position                                                                                                                          |  Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                        |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                    Off |
| **User overrides**                                                                                                                  |                                                        |
| Allow overrides from M365 services                                                                                                  |                                            Not checked |
| **Incident reports**                                                                                                                |                                                        |
| Use this severity level in admin alerts and reports:                                                                                |                                                    Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                    Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                    Off |
| **Additional options**                                                                                                              |                                                        |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                            Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                    Off |
| Priority                                                                                                                            |                                                     37 |

##### Mark P C PP X-header

| Item                                                                                                                                |                                                                                                                                  Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                                   Mark P C PP X-header |
| Description                                                                                                                         |                                                                                                                                 _None_ |
| **Conditions**                                                                                                                      |                                                                                                                                        |
| Content contains                                                                                                                    |                                                                                                                                        |
| - Group name                                                                                                                        |                                                                                                                                Default |
| - Group operator                                                                                                                    |                                                                                                                           Any of these |
| - Sensitivity labels                                                                                                                |                                                                                              PROTECTED CABINET(group)/Personal Privacy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                                                  Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                                        |
| **NOT**                                                                                                                             |                                                                                                                                        |
| **Conditions**                                                                                                                      |                                                                                                                                        |
| Header matches patterns                                                                                                             |                                        X-Protective-Marking<br>`SEC=PROTECTED\u002C CAVEAT=SH:CABINET.*\u002C ACCESS=Personal-Privacy` |
| **Actions**                                                                                                                         |                                                                                                                                        |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=PROTECTED, CAVEAT=SH:CABINET, ACCESS=Personal-Privacy, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                                        |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                                    Off |
| **User overrides**                                                                                                                  |                                                                                                                                        |
| Allow overrides from M365 services                                                                                                  |                                                                                                                            Not checked |
| **Incident reports**                                                                                                                |                                                                                                                                        |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                                    Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                                    Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                                    Off |
| **Additional options**                                                                                                              |                                                                                                                                        |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                                            Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                                    Off |
| Priority                                                                                                                            |                                                                                                                                     38 |

##### Mark P C PP subject

| Item                                                                                                                                |                                                                           Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                             Mark P C PP subject |
| Description                                                                                                                         |                                                                          _None_ |
| **Conditions**                                                                                                                      |                                                                                 |
| Content contains                                                                                                                    |                                                                                 |
| - Group name                                                                                                                        |                                                                         Default |
| - Group operator                                                                                                                    |                                                                    Any of these |
| - Sensitivity labels                                                                                                                |                                      PROTECTED CABINET (group)/Personal Privacy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                           Message or attachment |
| **Actions**                                                                                                                         |                                                                                 |
| Modify subject                                                                                                                      |                                                                                 |
| - Remove text that matches                                                                                                          |                                                               `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=PROTECTED, CAVEAT=SH:CABINET, ACCESS=Personal-Privacy]`<sup>1</sup> |
| - Position                                                                                                                          |                           Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                                                 |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                             Off |
| **User overrides**                                                                                                                  |                                                                                 |
| Allow overrides from M365 services                                                                                                  |                                                                     Not checked |
| **Incident reports**                                                                                                                |                                                                                 |
| Use this severity level in admin alerts and reports:                                                                                |                                                                             Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                             Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                             Off |
| **Additional options**                                                                                                              |                                                                                 |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                     Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                             Off |
| Priority                                                                                                                            |                                                                              39 |

##### Mark P C LP X-header

| Item                                                                                                                                |                                                                                                                                 Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                                  Mark P C LP X-header |
| Description                                                                                                                         |                                                                                                                                _None_ |
| **Conditions**                                                                                                                      |                                                                                                                                       |
| Content contains                                                                                                                    |                                                                                                                                       |
| - Group name                                                                                                                        |                                                                                                                               Default |
| - Group operator                                                                                                                    |                                                                                                                          Any of these |
| - Sensitivity labels                                                                                                                |                                                                                             PROTECTED CABINET (group)/Legal Privilege |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                                                 Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                                       |
| **NOT**                                                                                                                             |                                                                                                                                       |
| **Conditions**                                                                                                                      |                                                                                                                                       |
| Header matches patterns                                                                                                             |                                        X-Protective-Marking<br>`SEC=PROTECTED\u002C CAVEAT=SH:CABINET.*\u002C ACCESS=Legal-Privilege` |
| **Actions**                                                                                                                         |                                                                                                                                       |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=PROTECTED, CAVEAT=SH:CABINET, ACCESS=Legal-Privilege, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                                       |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                                   Off |
| **User overrides**                                                                                                                  |                                                                                                                                       |
| Allow overrides from M365 services                                                                                                  |                                                                                                                           Not checked |
| **Incident reports**                                                                                                                |                                                                                                                                       |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                                   Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                                   Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                                   Off |
| **Additional options**                                                                                                              |                                                                                                                                       |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                                           Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                                   Off |
| Priority                                                                                                                            |                                                                                                                                    40 |

##### Mark P C LP subject

| Item                                                                                                                                |                                                                          Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | -----------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                            Mark P C LP subject |
| Description                                                                                                                         |                                                                         _None_ |
| **Conditions**                                                                                                                      |                                                                                |
| Content contains                                                                                                                    |                                                                                |
| - Group name                                                                                                                        |                                                                        Default |
| - Group operator                                                                                                                    |                                                                   Any of these |
| - Sensitivity labels                                                                                                                |                                      PROTECTED CABINET (group)/Legal Privilege |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                          Message or attachment |
| **Actions**                                                                                                                         |                                                                                |
| Modify subject                                                                                                                      |                                                                                |
| - Remove text that matches                                                                                                          |                                                              `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=PROTECTED, CAVEAT=SH:CABINET, ACCESS=Legal-Privilege]`<sup>1</sup> |
| - Position                                                                                                                          |                          Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                                                |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                            Off |
| **User overrides**                                                                                                                  |                                                                                |
| Allow overrides from M365 services                                                                                                  |                                                                    Not checked |
| **Incident reports**                                                                                                                |                                                                                |
| Use this severity level in admin alerts and reports:                                                                                |                                                                            Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                            Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                            Off |
| **Additional options**                                                                                                              |                                                                                |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                    Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                            Off |
| Priority                                                                                                                            |                                                                             41 |

##### Mark P C LS X-header

| Item                                                                                                                                |                                                                                                                                     Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                                                                      Mark P C LS X-header |
| Description                                                                                                                         |                                                                                                                                    _None_ |
| **Conditions**                                                                                                                      |                                                                                                                                           |
| Content contains                                                                                                                    |                                                                                                                                           |
| - Group name                                                                                                                        |                                                                                                                                   Default |
| - Group operator                                                                                                                    |                                                                                                                              Any of these |
| - Sensitivity labels                                                                                                                |                                                                                             PROTECTED CABINET (group)/Legislative Secrecy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                                                                                     Message or attachment |
| Condition group **AND**                                                                                                             |                                                                                                                                           |
| **NOT**                                                                                                                             |                                                                                                                                           |
| **Conditions**                                                                                                                      |                                                                                                                                           |
| Header matches patterns                                                                                                             |                                        X-Protective-Marking<br>`SEC=PROTECTED\u002C CAVEAT=SH:CABINET.*\u002C ACCESS=Legislative-Secrecy` |
| **Actions**                                                                                                                         |                                                                                                                                           |
| Set headers                                                                                                                         | `X-Protective-Marking: VER=2025.1, NS=gov.au, SEC=PROTECTED, CAVEAT=SH:CABINET, ACCESS=Legislative-Secrecy, ORIGIN=<organisation.gov.au>` |
| **User notifications**                                                                                                              |                                                                                                                                           |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                                                                       Off |
| **User overrides**                                                                                                                  |                                                                                                                                           |
| Allow overrides from M365 services                                                                                                  |                                                                                                                               Not checked |
| **Incident reports**                                                                                                                |                                                                                                                                           |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                                                                       Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                                                                       Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                                                                       Off |
| **Additional options**                                                                                                              |                                                                                                                                           |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                                                                               Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                                                                       Off |
| Priority                                                                                                                            |                                                                                                                                        42 |

##### Mark P C LS subject

| Item                                                                                                                                |                                                                              Value |
| ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------: |
| Name                                                                                                                                |                                                                Mark P C LS subject |
| Description                                                                                                                         |                                                                             _None_ |
| **Conditions**                                                                                                                      |                                                                                    |
| Content contains                                                                                                                    |                                                                                    |
| - Group name                                                                                                                        |                                                                            Default |
| - Group operator                                                                                                                    |                                                                       Any of these |
| - Sensitivity labels                                                                                                                |                                      PROTECTED CABINET (group)/Legislative Secrecy |
| - Evaluate predicate for (available for Exchange workload only)                                                                     |                                                              Message or attachment |
| **Actions**                                                                                                                         |                                                                                    |
| Modify subject                                                                                                                      |                                                                                    |
| - Remove text that matches                                                                                                          |                                                                  `\s*?\[SEC=.*?\]` |
| - Insert this replacement text                                                                                                      | &nbsp;`[SEC=PROTECTED, CAVEAT=SH:CABINET, ACCESS=Legislative-Secrecy]`<sup>1</sup> |
| - Position                                                                                                                          |                              Remove matches and append replacement text to subject |
| **User notifications**                                                                                                              |                                                                                    |
| Use notifications to inform your users and help educate them on the proper use of sensitive info.                                   |                                                                                Off |
| **User overrides**                                                                                                                  |                                                                                    |
| Allow overrides from M365 services                                                                                                  |                                                                        Not checked |
| **Incident reports**                                                                                                                |                                                                                    |
| Use this severity level in admin alerts and reports:                                                                                |                                                                                Low |
| Send an alert to admins when a rule match occurs.                                                                                   |                                                                                Off |
| Use email incident reports to notify you when a policy match occurs.                                                                |                                                                                Off |
| **Additional options**                                                                                                              |                                                                                    |
| If there's a match for this rule, stop processing additional DLP policies and rules.                                                |                                                                        Not checked |
| Evaluate rule per component (Email body and each individual attachment will be considered an individual entity for rule evaluation) |                                                                                Off |
| Priority                                                                                                                            |                                                                                 43 |

{{% alert title="Subject replacement text" color="warning" %}}

1: The _modify subject_ replacement text values must have a leading whitespace character before the `[SEC=`.

{{% /alert %}}

### Policy mode

| Item        |                          Value |
| ----------- | -----------------------------: |
| Policy mode | Turn the policy on immediately |

### Related information

#### Security and governance

- None identified

#### Design

- [Data Loss Prevention](/design/shared-services/purview/data-loss-prevention)

#### Configuration

- None identified

#### References

- [Data loss prevention Exchange reference](https://learn.microsoft.com/en-au/purview/dlp-exchange-conditions-and-actions)
- [Data loss prevention policy reference](https://learn.microsoft.com/en-au/purview/dlp-policy-reference)
- [Learn about using regular expressions (regex) in data loss prevention policies](https://learn.microsoft.com/en-au/purview/dlp-policy-learn-about-regex-use)
- [Regular expression quick reference](https://learn.microsoft.com/en-au/dotnet/standard/base-types/regular-expression-language-quick-reference)
