---
title: Microsoft 365 connectivity
weight: 12
description: "This section describes the design decisions associated with on-premises endpoint connectivity."
---

Microsoft 365 is a publicly facing SaaS offering and firewall ports are required to be opened to enable communication between infrastructure and desktops and Microsoft 365. These ports configurations are updated frequently and are available online from [Microsoft](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges).

It is important to note the traffic between the clients and the Microsoft 365 offering is TLS 1.2 encrypted.

Configuration will occur on the proxy and external gateway of the organisation as required.

### Mail flow and gateway

Mail flow is the path taken by an email from the sender to a receiver. A Mail Gateway acts as the central egress and ingress point for mail traffic into organisations.

For organisations implementing a PROTECTED environment, organisations are required to use a separate mail gateway to interface with [GovLINK](https://www.finance.gov.au/government/whole-government-information-communications-technology-services/govlink) for the following functions:

- Encryption
- Message rules
- Header modification

This will achieve the closest alignment to whole-of-government policy for [Secure Internet Gateways](https://www.cyber.gov.au/resources-business-and-government/maintaining-devices-and-systems/system-hardening-and-administration/gateway-hardening/gateway-security-guidance-package-gateway-security-principles) and with the guidance in ASD's [_Information Security Manual_](https://www.cyber.gov.au/resources-business-and-government/essential-cyber-security/ism?ss=true) and the [_Protective Security Policy Framework_](https://www.protectivesecurity.gov.au/publications-library/pspf-annual-release).

GovLINK enables secure communication between Commonwealth entities across public infrastructure and is required for PROTECTED mail to be securely transferred between government organisations.

A Transport Layer Security (TLS) solution for GovLINK is available enabling a direct interface between Microsoft 365 Exchange Online and GovLINK. In addition to Exchange Online, organisations wishing to deploy this solution will also require Microsoft Defender, Mail Transfer Agent-Strict Transport Security (MTA-STS), and TLS.

More information on GovLINK is available on [the Department of Finance website](https://www.finance.gov.au/government/whole-government-information-communications-technology-services/govlink).

Enquires on the GovLINK TLS solution can also be directed to [govlinkenquiries@finance.gov.au](mailto:govlinkenquiries@finance.gov.au) or via the above website.

{{% alert title="Design decisions" color="warning" %}}

| Implementation Type | Mail Gateway                     | Mail Connectors         | Mail Ingress | Mail Egress  | Sensitivity Labels |
| ------------------- | -------------------------------- | ----------------------- | ------------ | ------------ | ------------------ |
| Cloud               | Exchange Online Protection (EOP) | Not required            | EOP          | EOP          | Required           |
| Hybrid              | Existing mail gateway            | EOL &lt;-> Mail gateway | Mail gateway | Mail gateway | Required           |

{{% /alert %}}

### Exchange hybrid

This section is only relevant for organisations implementing a hybrid solution that leverages an on-premises Exchange Server(s).

Exchange Online can be used standalone (cloud only) or integrated with an on-premises Exchange Server(s) and Active Directory Domain Services, extending the organisation's messaging farm in a hybrid configuration.

A Hybrid configuration provides administrators with added flexibility to transition users to the Cloud without isolating them from the on-premises resources. A Hybrid configuration can also assist with transport routing for compliance reasons (e.g. GovLINK) when "centralized mail transport" is enabled. The [Edge Transport](https://docs.microsoft.com/exchange/edge-transport-servers) service may be deployed in scenarios where the organisation does not wish to expose Hybrid mail servers directly to Exchange Online Protection.

organisations wishing to synchronise their existing on-premises Active Directory Domain Services for identity (hybrid identity) must maintain an on-premises Exchange server for recipient management purposes, this is because most of the user attributes cannot be managed from Exchange online due to directory synchronisation rules, for more information see [decommissioning on-premises Exchange servers](https://docs.microsoft.com/exchange/decommission-on-premises-exchange).

Establishing hybrid deployments requires an Exchange hybrid server that is supported with existing on-premises Exchange Server. Microsoft recommends the deployment of the newest Exchange Hybrid server for the environment to ensure the best compatibility with Exchange Online.

Exchange 2010 has reached [end of support](https://docs.microsoft.com/microsoft-365/enterprise/exchange-2010-end-of-support?view=o365-worldwide), organisations that wish to use retain a Hybrid configuration after the Hybrid migration method should migrate those Exchange server roles to a supported version of Exchange. Microsoft also recommend that organisations still on Exchange 2010 that have not started or completed their Hybrid migration, upgrade from 2010 to 2016 before commencing the hybrid configuration.

Exchange Hybrid Server Supported Configurations.

| On-premises environment | Exchange 2019 Hybrid Deployment | Exchange 2016 Hybrid Deployment | Exchange 2013 Hybrid Deployment | Exchange 2010 Hybrid Deployment |
| ----------------------- | ------------------------------- | ------------------------------- | ------------------------------- | ------------------------------- |
| Exchange 2019           | Supported                       | Not supported                   | Not supported                   | Not supported                   |
| Exchange 2016           | Supported                       | Supported                       | Not supported                   | Not supported                   |
| Exchange 2013           | Supported                       | Supported                       | Supported                       | Not supported                   |
| Exchange 2010           | Not supported                   | Supported                       | Supported                       | Supported                       |

The following table outlines the Exchange server roles required to be installed based on on-premises Exchange environment version. The roles mentioned for Exchange 2013 and 2010 can be installed separately or on one server, Microsoft strongly recommend installing all roles on one server.

| On-premises environment | Mailbox server        | Client Access server  | Hub Transport         |
| ----------------------- | --------------------- | --------------------- | --------------------- |
| Exchange 2016 and newer | At least one instance | Not required          | Not required          |
| Exchange 2013           | At least one instance | At least one instance | Not required          |
| Exchange 2010           | At least one instance | At least one instance | At least one instance |

Exchange Hybrid design considerations and decisions only apply to organisations leveraging a hybrid implementation.

| Decision point                                  | Design decision       | Justification                                                                                                                                                                                             |
| ----------------------------------------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Exchange Hybrid Deployment                      | Exchange 2016-based   | The organisation will use its existing Exchange 2016 server to establish the hybrid connection.                                                                                                           |
| Edge Transport Server for hybrid mail transport | Organisation decision | The organisation can choose to leverage an Edge Transport server to prevent the exposure of internal Exchange servers directly to the internet, depending on their risk appetite and gateway environment. |

### Mail connectors

Mail connectors use TLS to secure communication and can customise the way mail flows into and out of the organisation.

Generally mail connectors are required. An exception may be where organisations do not use a mail gateway and relies on Exchange Online Protection.

When the organisation intends to operate at the PROTECTED level, the Blueprint assumes that all organisations are implementing the configuration with a Mail Gateway and as such, provides detailed configurations on implementing mail connectors via the relevant gateway.

{{% alert title="Design decisions" color="warning" %}}

| Decision point  | Design decision | Justification                                                                                                                                            |
| --------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mail Connectors | Configured      | Mail connectors are required for all Exchange and Exchange Online implementations. Specific connectors are configured when implementing Exchange hybrid. |

{{% /alert %}}

Mail Connector Configuration for all organisations and implementation types for environments intended to be used at the PROTECTED level

| Configuration                                      | Value                                                                                                                     | Description                                                                                                               |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Certificate details                                | Configured                                                                                                                | Certificate to be issued from the gateway hosting the GovLINK connection.                                                 |
| Virtual IP address (VIP)                           | Configured                                                                                                                | Virtual IP Address details will be provided by the gateway provider.                                                      |
| **Exchange Online Receive Connector**              |                                                                                                                           |                                                                                                                           |
| Name                                               | `Inbound-connector-from-<GATEWAY>`                                                                                        | Describes the source and directionality of mail.                                                                          |
| Retain internal mail headers                       | Unchecked                                                                                                                 | Internal Mail headers are stripped off messages.                                                                          |
| On-premises server identification method and value | Identify by Senders Domain. Reject email messages if they are not sent over TLS. Require subject name matching `<DOMAIN>` | Ensures mail is being sent over an encrypted connection to a known domain.                                                |
| **Exchange Online Send Connector**                 |                                                                                                                           |                                                                                                                           |
| Name                                               | `outbound-connector-to-<GATEWAY>`                                                                                         | Describes the source and directionality of mail.                                                                          |
| Retain internal mail headers                       | Checked                                                                                                                   | When reporting spam that slips past the filters, it is essential that we receive the full message headers from a message. |
| When to use the connector                          | \\\* (All Mail)                                                                                                           | All mail should use the connector.                                                                                        |
| Message routing                                    | Route through these smart hosts.                                                                                          | This should be used route mail to the gateway.                                                                            |
| Connector Authentication settings                  | Always use TLS issued by a trusted Certificate Authority with a SAN matching `<DOMAIN>`                                   | Ensures mail is being sent over an encrypted connection to a known domain.                                                |

### Certificates for hybrid deployments

There are additional specific certificate requirements when configuring Exchange Hybrid that only apply to organisations implementing a hybrid configuration as Exchange Online encrypts all traffic to the on-premises environment. organisations implementing cloud only environments that do not leverage an on-premises Exchange Server do not need require these configurations.

The following certificates are associated with Exchange hybrid deployments:

- Azure Active Directory Connect (Entra Connect) with Active Directory Federation Services (AD FS) -- a third party certificate from a Trusted Authority (CA) is required to establish a trust between web clients and federations server proxies used to sign and decrypt security tokens.
- Exchange Federation -- a self-signed certificate is used to create a secure connection between the on-premises Exchange server and Azure Active Directory authentication
- Exchange Services -- a third party certificated from a Trusted Authority (CA) is required to secure the TLS communication between Exchange servers and clients. These include Outlook on the web, Exchange ActiveSync, Outlook Anywhere and secure message transport
- Existing Exchange Servers -- might use self-signed or certificates issued by a Trusted Authority (CA) depending on Exchange server certificates. These certificates may need updating for Exchange Hybrid

Suggested FQDNs for hybrid deployments:

| Service                                                    | Suggested FQDN                                                                                                                                                     | Field                    |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------ |
| Primary shared Simple Mail Transfer Protocol (SMTP) domain | organisation.gov.au                                                                                                                                                | Subject name             |
| Autodiscover                                               | To be determined by the organisation. <br>Label that matches the external Autodiscover FQDN on the Exchange Client Access server, such as Autodiscover.contoso.com | Subject alternative name |
| Transport                                                  | To be determined by the organisation. <br>Label that matches the external FQDN of the Edge Transport servers, such as edge.contoso.com                             | Subject alternative name |

{{% alert title="Design decisions" color="warning" %}}

| Decision point            | Design decision                 | Justification                                                                                                                                                    |
| ------------------------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hybrid Server Certificate | New certificate to be purchased | As the only new service which is being configured is the Exchange Hybrid Server, that is the only certificate which requires validation and updates as required. |

{{% /alert %}}

### Related information

#### Security and governance

- None identified

#### Design

- None identified

#### Configuration

- None identified

#### References

- [GovLink](https://www.finance.gov.au/government/whole-government-information-communications-technology-services/govlink)
- [Secure Internet Gateways](https://www.cyber.gov.au/acsc/view-all-content/programs/irap/asd-certified-gateways)
- ASD's [_Information Security Manual_](https://www.cyber.gov.au/acsc/view-all-content/guidance/email-gateways-and-servers)
- [_Protective Security Policy Framework_](https://www.protectivesecurity.gov.au/publications-library/pspf-annual-release)
