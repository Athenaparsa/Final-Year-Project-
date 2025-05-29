# Graywatch Enterprise Security & Analytics Platform (GESAP)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Graylog Version](https://img.shields.io/badge/Graylog-5.1-brightgreen.svg)](https://www.graylog.org/)
[![Ansible Ready](https://img.shields.io/badge/Ansible-Ready-red.svg)](https://www.ansible.com/)
[![Infrastructure as Code](https://img.shields.io/badge/IaC-Terraform-purple.svg)](https://www.terraform.io/)

> A modular SIEM solution designed for educational environments, enabling real-time threat detection, advanced analytics, and hands-on SOC experience with enterprise-grade components.

---

## 📌 Project Information

- **Author:** Athena Parsa  
- **Degree:** BSc Hons Cybersecurity  
- **Institution:** University of Roehampton  
- **Supervisors:** Charles Clarke, Mastaneh Davis  
- **Project Year:** 2024-2025  
- **Dissertation Title:** Graywatch Enterprise Security & Analytics Platform (GESAP)

---

## 🌟 Key Features

- ✅ Real-time security analytics and alerting  
- ✅ Detection rules for brute force, privilege escalation, and data exfiltration  
- ✅ Log ingestion from Linux servers and web infrastructure  
- ✅ Fully open-source stack (Graylog, OpenSearch, MongoDB)  
- ✅ Interactive dashboards for threat visualisation  
- ✅ Automated backups and snapshot scheduling  
- ✅ Resource-efficient design with memory protection  
- ✅ Modular and scalable for future student deployments  

---

## 📚 Table of Contents

1. [Overview](#overview)  
2. [Architecture](#architecture)  
3. [Installation](#installation)  
4. [Log Ingestion](#log-ingestion)  
5. [Threat Detection Rules](#threat-detection-rules)  
6. [Dashboards](#dashboards)  
7. [Disk Management & Backup](#disk-management--backup)  
8. [Role-Based Access Control](#role-based-access-control)  
9. [Performance Tuning](#performance-tuning)  
10. [Usage Guides](#usage-guides)  
11. [Project Planning](#project-planning)  
12. [Academic Context](#academic-context)  
13. [License](#license)  

---

## 🧠 Overview

GESAP is a fully working SIEM system that allows universities to simulate security operations centre (SOC) environments. This solution was developed to bridge the gap between theoretical knowledge and real-world security monitoring practices in academic settings.

---

## 🏗️ Architecture

| Layer                    | Components                                       |
|--------------------------|--------------------------------------------------|
| **Collection Layer**     | Filebeat, Rsyslog, Graylog Syslog UDP Input     |
| **Processing Layer**     | Graylog Server, Pipelines, Streams              |
| **Storage Layer**        | OpenSearch (logs), MongoDB (metadata)           |
| **Interface Layer**      | Graylog Web UI, Nginx reverse proxy             |
| **Control Layer**        | RBAC, Role Management, Security Dashboards      |

**Table 1.** GESAP SIEM Architectural Components.

---

## ⚙️ Installation

### Prerequisites

- **2 VMs** (Ubuntu Desktop + Ubuntu Server)  
- **VirtualBox** with Internal & NAT network adapters  
- Minimum: 4 CPU cores, 8GB RAM, 80GB Disk  

### Setup Summary

```bash
sudo apt update && sudo apt upgrade
sudo apt install mongodb opensearch graylog-server nginx filebeat rsyslog
    Configuration includes SSH setup, dual network interface, and static IP binding between VMs.

For full deployment, see the Admin Guide.
📥 Log Ingestion

Log ingestion is achieved using Filebeat and Rsyslog:

    Rsyslog forwards system logs over UDP to Graylog.

    Filebeat supports structured log delivery from custom services.

    Both are validated using Graylog Inputs and Streams.

Example Rsyslog configuration:

*.* @192.168.123.1:5140;RSYSLOG_SyslogProtocol23Format

🚨 Threat Detection Rules

The following detection pipelines were implemented:
Rule Name	Description
Brute Force Alert	Triggers on multiple failed SSH attempts
Priv Escalation	Alerts on sudo, usermod, or passwd use
Data Exfiltration	Detects unusual file transfer commands
Out of Hours Login	Flags login events outside normal work hours
Log Tampering	Monitors changes to .bash_history, auth.log, etc

Table 2. Implemented Detection Pipelines in GESAP.
📊 Dashboards
Dashboard Title	Purpose
Permission Escalations	Visual audit trail of sudo activity
Suspicious Account Activities	New users and deleted accounts
Log Tampering	Alerts for cleared logs or edits
Sensitive File Access	Access to /etc/passwd, shadow etc.
Off-Hours Login Attempts	Filtered logins by time of day

Table 3. Custom Dashboards Available in GESAP.
🧠 Disk Management & Backup

    Enabled logrotate for local logs

    Configured Graylog index rotation (1GB/14 days)

    Automated backups via tar and Elastic snapshots

    Setup cron jobs for scheduled backup and alert scripts

tar -czvf graylog_backup.tar.gz /etc/graylog /var/lib/elasticsearch

Snapshot storage path was defined in elasticsearch.yml with appropriate permissions.
🔐 Role-Based Access Control (RBAC)

Custom roles were created in Graylog:

    admin – full access to dashboards and system

    analyst – read-only access to monitoring dashboards

    hunter – access to detection rules and alerts

Passwords were removed from all config files. Two users tested concurrently using separate sessions.
🧠 Performance Tuning

    Heap Size optimised in OpenSearch config

    Swap Memory added via:

sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile && mkswap /swapfile && swapon /swapfile

    Enabled log rotation to prevent disk exhaustion

    Configured Elasticsearch and Graylog startup delays in systemd for stable boot

📘 Usage Guides

    Admin Guide: Setup, backup, and user management

    Threat Hunter Guide: Navigating dashboards and tuning alerts

    Incident Response Manual: How to interpret alerts and triage

    Troubleshooting Handbook: Covers errors like index_not_found_exception, MongoDB failures, and snapshot issues

📈 Project Planning

Project managed through GitHub Kanban, based on five structured phases:

    Environment Setup

    Log Ingestion and Indexing

    Detection and Alerting

    User Access and Memory Optimisation

    Backup, Reporting, and Documentation

## 📘 Documentation

Explore detailed guides for setting up, using, and maintaining GESAP:
- [Admin Guide](admin-guide.md)  
- [Threat Hunter Guide](threat-hunter-guide.md)  
- [Incident Response Manual](incident-response.md)  
- [Troubleshooting Handbook](troubleshooting.md)  
- [Handover & Reset Notes](handover-notes.md)


Each task was tracked, updated, and referenced in the final dissertation.
🎓 Academic Context

This project was submitted as a final-year dissertation to the University of Roehampton, demonstrating a modular SIEM platform for academic training. The system is deployable, robust, and intended for multi-user student interaction with built-in performance protections and documentation.
📄 License

This project is licensed under the MIT License. See the LICENSE file for details.
<p align="center"> <sub>Developed as part of the BSc Cybersecurity Final Year Project</sub><br> <sub>© 2025 Athena Parsa | University of Roehampton</sub> </p> ```
