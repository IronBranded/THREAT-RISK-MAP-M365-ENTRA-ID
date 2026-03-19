# Threat & Risk Map — M365 / Entra ID

A practical, interactive reference for DFIR investigators and security analysts working Microsoft 365 and Entra ID incidents. Covers **36 threat scenarios** with IOCs, IOAs, MITRE ATT&CK mappings, KQL detection queries, IR runbooks, and a risk heat map.

---

## Usage

<h3 align="center">
  <a href="https://ironbranded.github.io/THREAT-RISK-MAP-M365-ENTRA-ID/" target="_blank" rel="noopener noreferrer">
    🟢 NAVIGATE THE MAP 🟢
  </a>
</h3>


P.S: You can also download `index.html` and use it locally.

---

## What's New in v2.0

### Workload Identity Risks (7 new scenarios)
Targeting BEC and automated infostealer campaigns, **Workload Identity** is the critical pivot layer attackers exploit after initial user compromise. Service Principals and OAuth applications provide MFA-exempt, password-reset-resistant persistence invisible to user-focused risk policies. v2.0 adds full coverage.

| New Threat | Severity | Key MITRE |
|---|---|---|
| Suspicious Credential Addition to OAuth App | 🔴 Critical | T1098.001 – Additional Cloud Credentials |
| Anomalous API Calls by Service Principal | 🔴 Critical | T1114.002, T1059.009 |
| Illicit OAuth Consent Grant (Consent Phishing) | 🔴 Critical | T1528 – Steal App Access Token |
| Service Principal Privilege Escalation | 🔴 Critical | T1098.003 – Additional Cloud Roles |
| Rogue / Shadow Application Registration | 🟠 High | T1136.003 – Cloud Account |
| Managed Identity Token Exfiltration (SSRF/IMDS) | 🟠 High | T1552.007, T1550 |
| App Governance Policy Gap / Dormant Permissions Abuse | 🟡 Medium | T1530, T1119 |

Detection sources across all 7 scenarios: `AADServicePrincipalSignInLogs`, `AuditLogs` (Application Management), `CloudAppEvents`, **Entra Workload ID Protection**, **App Governance**.

### New Attack Chain
- **Workload Identity Pivot & Persistence** — AiTM → credential addition → SP privilege escalation → anomalous API abuse

### Corrected IR Runbook Phase Order
All 36 runbooks now follow incident response best practice:

```
Triage → Contain → Investigate → Recover → Escalate If
```

> **Why Contain before Investigate?** Containment limits attacker dwell time and stops active data collection while investigation proceeds. Investigation under active compromise risks tipping off a hands-on attacker and allows continued exfiltration.

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
| **Runbook** | Interactive IR checklist — Triage → Contain → Investigate → Recover → Escalate If |

---

## Views

| View | Description |
|---|---|
| **Home** | Threat intelligence search, highest-risk threats, category browser |
| **Grid** | Card-based overview of all threats, filterable by severity and category |
| **Heat Map** | 5×5 Likelihood × Impact matrix — each threat independently scored, click any cell to inspect |
| **Table** | Compact sortable list for quick scanning |
| **Attack Chains** | Pre-built kill chains showing how threats chain together end-to-end |

---

## Threat Scenarios (36)

| Category | Threats |
|---|---|
| **Identity & Account** | User Account Compromise, Entra ID Tenant Reconnaissance, Hybrid Identity Attack / AADConnect, Service Principal / Workload Identity Abuse, Identity Protection Evasion |
| **Email / BEC** | BEC Internal Impact, BEC External Impact, BEC Inbox Rule Manipulation, Malicious Email Forwarding Rules, Teams-Based Phishing |
| **Authentication** | Token Theft / Session Hijacking, AiTM Adversary-in-the-Middle, MFA Fatigue / Push Bombing, Device Code Phishing, Legacy Authentication Exploitation |
| **Access Control** | Conditional Access Policy Gaps |
| **Application & Workload ID** | Illicit Consent Grant / OAuth Phishing, Malicious App Registration, Abnormal User Agent / API Abuse, Power Platform Abuse, **Suspicious Credential Addition to OAuth App** *(new)*, **Anomalous API Calls by Service Principal** *(new)*, **Illicit OAuth Consent Grant (Consent Phishing)** *(new)*, **Service Principal Privilege Escalation** *(new)*, **Rogue / Shadow Application Registration** *(new)*, **Managed Identity Token Exfiltration** *(new)*, **App Governance Policy Gap** *(new)* |
| **Persistence** | Federated Identity / Golden SAML, Ghost Device Registration, Guest Account Abuse, PIM Eligible Role Abuse, Exchange Transport Rule Backdoor |
| **Privilege Escalation** | Privilege Escalation via Role Assignment |
| **Data Exfiltration** | Graph API Bulk Exfiltration, Microsoft Copilot for M365 Abuse, SharePoint / OneDrive Ransomware via Versioning Abuse |

---

## Attack Chains (6)

Pre-built end-to-end kill chains with clickable nodes that link directly to each threat:

1. **BEC Chain** — Account compromise → inbox rules → internal fraud → external wire transfer
2. **AiTM Chain** — Phishing proxy → token theft → malicious app registration → bulk exfiltration
3. **Recon → Escalation → Golden SAML** — Tenant recon → PIM abuse → role escalation → federated identity persistence
4. **Cloud Ransomware** — Account compromise → Graph exfiltration → SharePoint versioning wipe
5. **OAuth App Persistence** — Illicit consent grant → forwarding rules → ongoing exfiltration
6. **Workload Identity Pivot & Persistence** *(new)* — AiTM → credential addition to OAuth app → SP privilege escalation → anomalous API abuse

---

## Risk Heat Map

Threats are independently scored on two axes:

- **Likelihood (1–5)** — How frequently observed across M365 environments in the wild
- **Impact (1–5)** — Blast radius if successfully executed

Risk score = Likelihood × Impact (max 25). New Workload Identity scores:

| Threat | Likelihood | Impact | Risk Score |
|---|---|---|---|
| Suspicious Credential Addition to OAuth App | 4 | 5 | **20** |
| Illicit OAuth Consent Grant | 4 | 5 | **20** |
| Anomalous API Calls by Service Principal | 3 | 5 | **15** |
| Service Principal Privilege Escalation | 3 | 5 | **15** |
| Rogue / Shadow App Registration | 3 | 4 | **12** |
| Managed Identity Token Exfiltration | 2 | 4 | **8** |
| App Governance Policy Gap | 3 | 3 | **9** |

---

## IR Runbook Phase Order

Each threat includes a five-phase interactive IR checklist. The phase order follows containment-first IR practice:

```
Triage → Contain → Investigate → Recover → Escalate If
```

| Phase | Purpose |
|---|---|
| **Triage** | Confirm the alert, assess scope, classify severity |
| **Contain** | Stop active attacker access — disable accounts, revoke tokens, remove persistence |
| **Investigate** | Determine full scope, timeline, and blast radius under controlled conditions |
| **Recover** | Restore access safely, harden controls, verify clean state |
| **Escalate If** | Conditions that require escalation to leadership, legal, DART, or law enforcement |

Check off steps as you work an incident. Progress is tracked per threat during your session.

---

## KQL Requirements

Queries target **Microsoft Sentinel**. Ensure the following connectors are enabled:

- **Microsoft Entra ID** — Sign-in Logs & Audit Logs (`SigninLogs`, `AuditLogs`, `AADServicePrincipalSignInLogs`, `AADNonInteractiveUserSignInLogs`)
- **Microsoft 365 Defender** — `CloudAppEvents`, `EmailEvents`, `DeviceEvents`
- **Unified Audit Log** — Exchange, SharePoint, Teams, Copilot (`OfficeActivity`)
- **Microsoft Graph Activity Logs** — required for Graph API abuse detections
- **Azure Activity** — for role assignment and PIM events

> For Workload Identity detections, `AADServicePrincipalSignInLogs` and **App Governance** (Defender for Cloud Apps) are essential. Entra Workload ID Protection (P2 license) provides additional risk signals for service principals.

---

## References

- [MITRE ATT&CK for Enterprise](https://attack.mitre.org/matrices/enterprise/)
- [Azure Threat Research Matrix (MSTIC)](https://microsoft.github.io/Azure-Threat-Research-Matrix/)
- [Microsoft Entra ID Attack & Defense Playbook](https://github.com/Cloud-Architekt/AzureAD-Attack-Defense)
- [Microsoft Incident Response Playbooks](https://learn.microsoft.com/en-us/security/operations/incident-response-playbooks)
- [CISA — Microsoft 365 Security Auditing (ScubaGear)](https://github.com/cisagov/ScubaGear/blob/main/README.md)
- [Microsoft App Governance Documentation](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-app-governance)
- [Entra Workload ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/concept-workload-identity-risk)

---

> For defensive and incident response use only.
