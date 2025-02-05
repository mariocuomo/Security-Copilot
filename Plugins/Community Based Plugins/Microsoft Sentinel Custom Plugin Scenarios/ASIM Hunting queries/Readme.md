# DNS,Network, Threat Protectionand Web Sessions Essentials ASIM Schemas Hunting Queries

This repository contains a collection of Advanced Security Information Model (ASIM) schema hunting queries that are designed to help detect various network anomalies and potential security threats.

## DNS Essentials ASIM Schema Queries

- **Top 25 DNS queries with most failures in last 24 hours**
- **Potential beaconing activity**
- **Possible DNS Tunneling or Data Exfiltration Activity**
- **Increase in DNS Requests by client than the daily average count**
- **Connection to Unpopular Website Detected**
- **Anomalous Increase in DNS activity by clients**
- **CVE-2020-1350 (SIGRED) exploitation pattern**

## Network Essentials Schema Queries

- **Detect Outbound LDAP Traffic (ASIM Network Session schema)**
- **Detect port misuse by anomaly (ASIM Network Session schema)**
- **Detect port misuse by static threshold (ASIM Network Session schema)**
- **Detects several users with the same MAC address (ASIM Network Session schema)**
- **Mismatch between Destination App name and Destination Port (ASIM Network Session schema)**
- **Protocols passing authentication in cleartext (ASIM Network Session schema)**
- **Remote Desktop Network Traffic (ASIM Network Session schema)**

## Network Threat Protection Schema/Essentials

- **Remote Desktop Network Traffic (ASIM Network Session schema)**
- **Risky base64 encoded command in URL**
- **Exploit and Pentest Framework User Agent**

## Web Session Essentials

- **Empty User Agent Detected (ASIM Web Session)**
- **Excessive number of forbidden requests detected (ASIM Web Session)**
- **Detect IP Address in the requested URL (ASIM Web Session)**
- **Detect Kali Linux UserAgent (ASIM Web Session)**
- **Beaconing traffic based on common user agents visiting limited number of domains (ASIM Web Session)**
- **Potential beaconing detected - Similar sent bytes (ASIM Web Session)**
- **Potential beaconing detected (ASIM Web Session)**
- **Request from bots and crawlers (ASIM Web Session)**
- **Detect threat information in web requests (ASIM Web Session)**

## Usage in Security Copilot Plugin

### Instructions

### Pre-requisites

-   [Security Copilot Enabled](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Access to upload custom plugins](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
-   [Microsoft Sentinel Workspace](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) created.
-   Parameters for KQL Plugin - Microsoft Sentinel Workspace Name, Subscription ID, Resource Group Name and Entra Tenant ID
#### Upload the Custom Plugin

1. Obtain the desired YAML file from this directory: - [DNSEssentials_HuntingQueries.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/ASIM%Hunting%quries/DNSEssentials_HuntingQueries.yaml).

   [NetworkSessionsEssentials_HuntingQueries.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/ASIM%Hunting%quries/NetworkSessionsEssentials_HuntingQueries.yaml).

    [NetworkThreatProtectionEssentials_HuntingQaueries.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/ASIM%Hunting%quries/NetworkThreatProtectionEssentials_HuntingQaueries.yaml).

     [WebSessionEssentials_HuntingQueries.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/ASIM%Hunting%quries/NetworkThreatProtectionEssentials_HuntingQaueries.yaml).

2. Modify the KQL query as needed to suit your specific requirements. 


3. [Upload the custom plugin](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) and enter your Tenant ID, Subscription ID, Workspace name, Resource group that hosts your Sentinel worksapce in the resulting dialog box.  Verify that the plugin is activated.

![CopilotForSecurity](https://learn.microsoft.com/en-us/security-copilot/media/add-plugin-button.png)


