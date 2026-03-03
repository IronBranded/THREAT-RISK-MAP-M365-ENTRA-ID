# Threat & Risk Map — M365 / Entra ID

A practical, interactive reference for DFIR investigators and security analysts working Microsoft 365 and Entra ID incidents. Covers 21 threat scenarios with IOCs, IOAs, MITRE ATT&CK mappings, KQL detection queries, and mitigations — all in a single HTML file.

---

## Usage

Download `m365-dfir-threat-map.html` and open it in any browser. No install, no dependencies, no server required.

---

## What's Inside

Each threat card includes five tabs:

- **Overview** — what the attack is and how it works
- **IOCs / IOAs** — specific log entries and behavioral patterns to hunt for
- **MITRE & Azure** — ATT&CK technique IDs and Azure Threat Research Matrix phases
- **KQL Detection** — ready-to-use queries for Microsoft Sentinel
- **Mitigations** — prioritized remediation steps

---

## Threat Scenarios

| Category | Threats |
|---|---|
| Identity & Account | User Account Compromise, Tenant Reconnaissance |
| Email / BEC | BEC Internal, BEC External, Inbox Rule Manipulation, Malicious Forwarding Rules |
| Authentication | Token Theft, AiTM, MFA Fatigue, Device Code Phishing, Legacy Auth Exploitation |
| Access Control | Conditional Access Policy Gaps |
| Application Abuse | Illicit Consent Grant, Malicious App Registration, Abnormal User Agent |
| Persistence | Federated Identity / Golden SAML, Ghost Device Registration, Guest Account Abuse |
| Privilege Escalation | Role Assignment Abuse / PIM Escalation |
| Data Exfiltration | Copilot for M365 Abuse, Graph API Bulk Exfiltration |

---

## KQL Requirements

Queries target Microsoft Sentinel. Ensure the following connectors are enabled:

- Microsoft Entra ID — Sign-in Logs & Audit Logs
- Microsoft 365 Defender — CloudAppEvents, EmailEvents
- Unified Audit Log — Exchange, SharePoint, Copilot
- Microsoft Graph Activity Logs

---

## References

- [MITRE ATT&CK for Enterprise](https://attack.mitre.org/matrices/enterprise/)
- [Azure Threat Research Matrix (MSTIC)](https://microsoft.github.io/Azure-Threat-Research-Matrix/)
- [Microsoft Entra ID Attack & Defense Playbook](https://github.com/Cloud-Architekt/AzureAD-Attack-Defense)

---

> For defensive and incident response use only.
