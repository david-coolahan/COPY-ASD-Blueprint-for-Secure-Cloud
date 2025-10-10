---
title: "Voicemail"
weight: 90
description: "This section describes the configuration of voicemail settings within Microsoft Teams associated with systems built according to guidance in ASD's Blueprint for Secure Cloud."
---

{{% alert title="Instruction" color="dark" %}}

The below pages outline the _as built_ configuration for ASD's _Blueprint for Secure Cloud_ (the Blueprint) for the Microsoft Teams admin portal at the following URL:

<https://admin.teams.microsoft.com/one-policy/settings/onlinevoicemail>

The settings described on these pages provide a baseline implementation for a system configured using the Blueprint. Any implementation implied by these pages should not be considered as prescriptive as to how an organisation must scope, build, document, or assess a system.

Implementation of the guidance provided by the Blueprint will differ depending on an organisation’s operating context and organisational culture. Organisations should implement the Blueprint in alignment with their existing change management, business processes and frameworks.

Placeholders such as `<ORGANISATION.GOV.AU>`, `<BLUEPRINT.GOV.AU>` and `<TENANT-NAME>` should be replaced with the relevant details as required.

{{% /alert %}}

### Voicemail settings

| Item                                                               |                                  Value |
| ------------------------------------------------------------------ | -------------------------------------: |
| Users can edit call answering rules                                |                                     On |
| Maximum voicemail recording length (seconds)                       |                                    300 |
| Primary prompt language                                            |                                 _None_ |
| Secondary prompt language                                          |                                 _None_ |
| Voicemail transcription                                            |                                    Off |
| Translation for transcriptions                                     |                                     On |
| Mask profanity in voicemail transcription                          |                                    Off |
| Users can share data for service improvement                       |                                    Off |
| Play preamble audio file before voicemail greeting                 | _Organisation voicemail greeting file_ |
| Play postamble audio file after voicemail greeting                 | _Organisation voicemail greeting file_ |
| Disconnect the call if preamble or postamble audio can't be played |                                    Off |

### Related information

#### Security and governance

- None identified

#### Design

- [Teams](/design/shared-services/teams)

#### Configuration

- None identified

#### References

- [Set up Cloud Voicemail](https://learn.microsoft.com/en-au/microsoftteams/set-up-phone-system-voicemail#setting-voicemail-policies-in-your-organization)
- [Teams settings and policies reference](https://learn.microsoft.com/en-au/microsoftteams/settings-policies-reference)
