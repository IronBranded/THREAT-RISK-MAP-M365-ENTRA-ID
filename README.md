# Threat & Risk Map — M365 / Entra ID

A practical, interactive reference for DFIR investigators and security analysts working Microsoft 365 and Entra ID incidents. Covers **29 threat scenarios** with IOCs, IOAs, MITRE ATT&CK mappings, KQL detection queries, IR runbooks, and a risk heat map.

---

## Usage

Download `m365-dfir-threat-map.html` and open it in any browser. No install, no dependencies, no server required.

**OR** run it directly:
👉 [https://ironbranded.github.io/THREAT-RISK-MAP-M365-ENTRA-ID/](https://ironbranded.github.io/THREAT-RISK-MAP-M365-ENTRA-ID/)

---

## What's Inside

Each threat card includes six tabs:

| Tab | Contents |
|---|---|
| **Overview** | What the attack is, how it works, and common vectors |
| **IOCs / IOAs** | Specific log entries and behavioral patterns to hunt for |
| **MITRE & Azure** | ATT&CK technique IDs and Azure Threat Research Matrix phases |
| **KQL Detection** | Ready-to-use queries for Microsoft Sentinel (copy with one click) |
| **Mitigations** | Prioritized remediation steps |
| **Runbook** | Interactive IR checklist — Triage → Investigate → Contain → Recover → Escalate |

---

## Views

| View | Description |
|---|---|
| **Grid** | Card-based overview of all threats, filterable by severity and category |
| **Heat Map** | 5×5 Likelihood × Impact matrix — each threat independently scored, click any cell to inspect |
| **Table** | Compact sortable list for quick scanning |
| **Attack Chains** | Pre-built kill chains showing how threats chain together end-to-end |

---

## Threat Scenarios (29)

| Category | Threats |
|---|---|
| **Identity & Account** | User Account Compromise, Entra ID Tenant Reconnaissance, Hybrid Identity Attack / AADConnect, Service Principal / Workload Identity Abuse, Identity Protection Evasion |
| **Email / BEC** | BEC Internal Impact, BEC External Impact, BEC Inbox Rule Manipulation, Malicious Email Forwarding Rules, Teams-Based Phishing |
| **Authentication** | Token Theft / Session Hijacking, AiTM Adversary-in-the-Middle, MFA Fatigue / Push Bombing, Device Code Phishing, Legacy Authentication Exploitation |
| **Access Control** | Conditional Access Policy Gaps |
| **Application Abuse** | Illicit Consent Grant / OAuth Phishing, Malicious App Registration, Abnormal User Agent / API Abuse, Power Platform Abuse |
| **Persistence** | Federated Identity / Golden SAML, Ghost Device Registration, Guest Account Abuse, PIM Eligible Role Abuse, Exchange Transport Rule Backdoor |
| **Privilege Escalation** | Privilege Escalation via Role Assignment |
| **Data Exfiltration** | Graph API Bulk Exfiltration, Microsoft Copilot for M365 Abuse, SharePoint / OneDrive Ransomware via Versioning Abuse |

---

## Attack Chains

Five pre-built end-to-end kill chains with clickable nodes that link directly to each threat:

1. **BEC Chain** — Account compromise → inbox rules → internal fraud → external wire transfer
2. **AiTM Chain** — Phishing proxy → token theft → malicious app registration → bulk exfiltration
3. **Recon → Escalation → Golden SAML** — Tenant recon → PIM abuse → role escalation → federated identity persistence
4. **Cloud Ransomware** — Account compromise → Graph exfiltration → SharePoint versioning wipe
5. **OAuth App Persistence** — Illicit consent grant → forwarding rules → ongoing exfiltration

---

## Risk Heat Map

Threats are independently scored on two axes:

- **Likelihood (1–5)** — How frequently observed across M365 environments in the wild
- **Impact (1–5)** — Blast radius if successfully executed

Risk score = Likelihood × Impact (max 25). The matrix surfaces your highest-priority threats at a glance — from User Account Compromise (L5/I5 = 25) down to low-likelihood, low-impact indicators.

---

## IR Runbooks

Each threat includes a five-phase interactive IR checklist:

```
Triage → Investigate → Contain → Recover → Escalate If
```

Check off steps as you work an incident. Progress is tracked per threat during your session.

---

## KQL Requirements

Queries target **Microsoft Sentinel**. Ensure the following connectors are enabled:

- **Microsoft Entra ID** — Sign-in Logs & Audit Logs
- **Microsoft 365 Defender** — CloudAppEvents, EmailEvents, DeviceEvents
- **Unified Audit Log** — Exchange, SharePoint, Teams, Copilot
- **Microsoft Graph Activity Logs**
- **Azure Activity** — for role assignment and PIM events

---

## References

- [MITRE ATT&CK for Enterprise](https://attack.mitre.org/matrices/enterprise/)
- [Azure Threat Research Matrix (MSTIC)](https://microsoft.github.io/Azure-Threat-Research-Matrix/)
- [Microsoft Entra ID Attack & Defense Playbook](https://github.com/Cloud-Architekt/AzureAD-Attack-Defense)
- [Microsoft Incident Response Playbooks](https://learn.microsoft.com/en-us/security/operations/incident-response-playbooks)
- [CISA — Microsoft 365 Security Best Practices](https://www.cisa.gov/resources-tools/resources/secure-cloud-business-applications-scuba-project)

---

> For defensive and incident response use only.
