# 🧠 GESAP Threat Hunter Guide

This guide supports cybersecurity analysts and students using the GESAP platform for threat detection, investigation, and incident response activities within a simulated SOC environment.

---

## 🧑‍💻 1. Role Description: Threat Hunter

The `hunter` role in GESAP is responsible for:

- Monitoring dashboards for anomalies
- Investigating detection rule triggers
- Tuning and proposing new alert rules
- Assisting in triaging incidents
- Documenting threat patterns and outcomes

---

## 📊 2. Accessing Dashboards

Log into Graylog and navigate to:

```text
Search > Dashboards
Then select from the custom dashboards below:
Dashboard Name	Purpose
Permission Escalations	Sudo usage and access control changes
Suspicious Account Activities	New/deleted users and login anomalies
Log Tampering	Alerts for edited or deleted logs
Sensitive File Access	Reads of /etc/passwd, shadow, and sudoers files
Off-Hours Login Attempts	Logins detected outside 08:00–18:00 work hours

Table 1. GESAP Dashboards for Threat Hunting.
🚨 3. Investigating Alerts

To examine an alert:

    Go to Search > Streams

    Click a stream such as Brute Force Alerts or Data Exfiltration

    View log details, timestamps, and source IPs

    Correlate with other logs from the same user or machine

⚠️ 4. Common Threat Scenarios
Scenario	Indicator	Next Action
Brute Force SSH	Repeated failed logins from same IP	Review /var/log/auth.log and block if needed
Privilege Escalation	sudo or usermod by unexpected user	Check login history, confirm user role
Log Tampering	.bash_history cleared or modified	Cross-reference with auth.log entries
Data Exfiltration	scp, curl, or large file transfers	Compare outbound IPs and confirm destinations
Login Outside Hours	Login between 00:00–06:00	Investigate user justification or alert admin

Table 2. Threat Patterns and Responses.
🔍 5. Search Queries & Techniques

You can use these queries in the Search tab to detect patterns:

message:"sudo" AND source:ubuntu-desktop
source:ubuntu-server AND sshd AND failed
timestamp:[now-1d TO now] AND user_name:"root"
message:/etc/shadow OR message:/etc/passwd

Useful tools:

    Use Histogram View to spot log spikes

    Apply Highlight Terms to trace specific commands

    Export logs as .csv for offline analysis

⚙️ 6. Rule Tuning (Advanced)

To tune detection logic:

    Go to System > Pipelines

    Select a rule, e.g., GESAP-Brute-Force

    Edit logic block such as:

rule "Brute Force"
when
  count("ssh_failed", within(5m)) > 5
then
  set_field("alert", "brute_force_detected");
end

📝 Note: Always notify the admin team before disabling or adjusting rules.
🧪 7. Validating Fixes

After responding to an alert:

    Reproduce the scenario (e.g., simulate a failed login)

    Confirm that the alert is now suppressed or behaves correctly

    Document your response in the SOC log or on GitHub Issues if using for team practice

🧭 8. Best Practices

    Do not silence alerts without root cause analysis

    Always keep investigation notes in a central log

    Avoid modifying infrastructure unless authorised

    Treat every alert as an opportunity to learn or improve detection

    Stay up to date on current threat intelligence feeds (e.g., AlienVault OTX)

📚 Further Reading

    Admin Guide

    Incident Response Manual 

    Troubleshooting Handbook 

<p align="center"> <sub>Developed as part of the BSc Cybersecurity Final Year Project</sub><br> <sub>© 2025 Athena Parsa | University of Roehampton</sub> </p> ```
