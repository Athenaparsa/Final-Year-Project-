# 🛡️ GESAP Incident Response Manual

This guide provides structured procedures for responding to security incidents detected via the Graywatch Enterprise Security & Analytics Platform (GESAP). It is designed for use in an educational SOC environment by students and junior analysts.

---

## 📋 1. Incident Response Workflow

| Phase          | Description                                   |
|----------------|-----------------------------------------------|
| **Preparation**   | System hardened, backups enabled, users trained     |
| **Detection**     | Alert raised via dashboards or streams             |
| **Analysis**      | Root cause identified through log investigation     |
| **Containment**   | Limit impact (user lockdown, traffic filtering)     |
| **Eradication**   | Remove cause (e.g. malware, misconfigurations)      |
| **Recovery**      | Restore affected systems from backup                |
| **Lessons Learned** | Document incident and update detection rules     |

**Table 1.** GESAP Incident Response Lifecycle.

---

## 🚨 2. Alert Types and Typical Actions

| Alert Type                 | Immediate Action                            |
|----------------------------|---------------------------------------------|
| Brute Force SSH            | Block IP, notify admin, check auth logs     |
| Privilege Escalation       | Lock user account, review command history   |
| Data Exfiltration          | Kill process, trace outbound connection     |
| Log Tampering              | Hash log files, check system integrity      |
| Off-Hours Login            | Confirm intent, cross-check with supervisor |

**Table 2.** Example Incidents and Initial Responses.

---

## 🧪 3. Investigating an Incident

Steps:

1. Navigate to **Search > Streams** in Graylog
2. Select relevant stream (e.g., `GESAP-Data-Exfiltration`)
3. Review matching logs, timestamps, source IPs, and user data
4. Pivot into broader log context using filters:

```text
source:ubuntu-desktop AND user_name:student1
message:"scp" OR     Document findings in a log or GitHub Issue (if in a team project)

🧰 4. Containment Techniques
Scenario	Containment Option
Ongoing SSH attack	Add IP to firewall deny list (ufw deny)
Unauthorised user	Disable account: usermod -L username
Suspicious process	Kill PID: kill -9 <pid>
Malware detection	Isolate VM by disabling interface (ifdown)

Always confirm changes with system administrator before enforcing critical actions.
♻️ 5. Recovery Procedure

If damage has occurred:

    Restore affected files from local backup:

tar -xzvf graylog_backup.tar.gz -C /

    For log database issues, restore OpenSearch snapshot:

POST /_snapshot/gesap_backup/snapshot-001/_restore

    Reboot services:

sudo systemctl restart graylog-server
sudo systemctl restart opensearch

📝 6. Documentation and Lessons Learned

After the incident:

    Record event summary (time, impact, response)

    Highlight root cause and resolution steps

    Recommend detection rule improvement

    File a report in /docs/IR-logs/ or as a GitHub Issue

Optional template:

**Incident Summary**:  
**Detection Time**:  
**Analyst**:  
**Root Cause**:  
**Response Actions Taken**:  
**Prevention Steps Added**:  

📦 7. Practice Scenarios

Use GESAP to simulate these:

    10 failed SSH logins → Trigger brute force alert

    sudo su - followed by a usermod command

    Use scp to move /etc/passwd to a remote IP

    Edit .bash_history file with echo >

These help train detection accuracy and analyst response time.
📚 Related Guides

    Admin Guide

    Threat Hunter Guide

    Troubleshooting Handbook 

<p align="center"> <sub>Developed as part of the BSc Cybersecurity Final Year Project</sub><br> <sub>© 2025 Athena Parsa | University of Roehampton</sub> </p> ```"curl" OR "wget"
