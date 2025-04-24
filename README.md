# 🛡️ LetsDefend Investigation – SOC246: Forced Authentication Detected

### 📅 Date: December 12, 2023 – 02:15 PM  
### 🧑‍💻 Role: Security Analyst  
### 🚨 Alert Rule: SOC246 – Forced Authentication Detected  

---

## 📊 Incident Summary

At 02:15 PM, the SIEM triggered an alert for multiple suspicious POST requests from a single IP targeting the login endpoint of a web server. This pattern closely matches brute force behavior, where an attacker attempts various username and password combinations in a short period.

| Field               | Details                                              |
|--------------------|------------------------------------------------------|
| **Event ID**        | 208                                                  |
| **Source IP**       | `120.48.36.175` (Beijing, China)                    |
| **Destination IP**  | `104.26.15.61`                                       |
| **Target Host**     | `WebServer_Test`                                     |
| **URL Targeted**    | `http://test-frontend.letsdefend.io/accounts/login` |
| **Request Method**  | POST                                                 |
| **Device Action**   | Permitted                                            |
| **Number of Requests** | 22 POST attempts                                  |

### 🧠 Alert Trigger Reason:
> Multiple POST requests were seen from the same IP to the fixed URI `/accounts/login`. These repeated login attempts point to a likely **brute force attack** scenario.

---

## 🧪 Investigation Notes

- Confirmed attack pattern via **SIEM logs**
- Observed sequential POST requests with varied credential payloads
- Matched brute-force behavior
- Source IP lookup via **AbuseIPDB** confirmed malicious activity

---

## 🔧 Tools Used

- [VirusTotal](https://www.virustotal.com/)
- [AbuseIPDB](https://www.abuseipdb.com/)
- [ChatGPT](https://chat.openai.com/) (used to analyze behavioral patterns & validate attack vectors)

---

## 🔐 Response Actions

- Isolated and monitored the affected endpoint (`WebServer_Test`)
- Escalated to Tier 2 SOC team for deep dive and potential credential compromise follow-up

---

## 🖼️ Screenshots

### SIEM Alert Panel
![SIEM Alert](screenshots/soc246-alert.png)

### IP Lookup in AbuseIPDB
![AbuseIPDB Screenshot](screenshots/ip-lookup.png)

### Log Sample - Brute Force Attempt
![Log Sample](screenshots/post-log.png)

---

## 🧠 Learning Outcome

This hands-on case improved my understanding of:
- Brute Force Attack detection through HTTP logs
- Threat actor fingerprinting via IP intelligence tools
- Collaboration between Tier 1 and Tier 2 in escalation flow
- Alert triage, threat enrichment, and incident response documentation

---

## 🧩 MITRE ATT&CK Mapping
| Tactic | Technique |
|--------|-----------|
| Credential Access | Brute Force (T1110) |

---

> 👣 Getting 1% better each day through real-world SOC simulations via LetsDefend!
