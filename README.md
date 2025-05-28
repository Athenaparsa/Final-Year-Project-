# Graywatch Enterprise Security & Analytics Platform (GESAP): A Modular SIEM Solution for Academic Use

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Graylog Version](https://img.shields.io/badge/Graylog-5.1-brightgreen.svg)](https://www.graylog.org/)
[![Ansible Ready](https://img.shields.io/badge/Ansible-Ready-red.svg)](https://www.ansible.com/)
[![Infrastructure as Code](https://img.shields.io/badge/IaC-Terraform-purple.svg)](https://www.terraform.io/)

> A comprehensive enterprise-grade log management, security analytics, and monitoring solution with advanced ML capabilities and high availability design.

## Project Information

**Author:** Athena Parsa  
**Major:** Cybersecurity  
**Supervisors:** Charles Clarke, Mastanhe Davis  
**Project Type:** Final Year Cybersecurity Project  
**Year:** 2025

## 🌟 Features

- **Centralized Log Management** - Collect, parse, and normalize logs from all your systems
- **Advanced Security Analytics** - Real-time threat detection with customizable detection rules
- **Threat Hunting Capabilities** - Tools for proactive threat discovery and incident investigation
- **Machine Learning Integration** - Anomaly detection and predictive security analysis
- **High Availability Cluster** - Multi-node architecture for enterprise reliability
- **Infrastructure as Code** - Fully automated deployment with Terraform and Ansible
- **Comprehensive Security Alerting** - Multi-channel notifications with custom escalation policies
- **Dynamic Visualization** - Interactive dashboards with 3D security event mapping
- **Compliance Reporting** - Built-in templates for GDPR, PCI-DSS, HIPAA, and ISO27001
- **Security Intelligence Integration** - Connect with threat feeds, OSINT sources, and security platforms
- **Automated Backup & DR** - Scheduled backups with documented recovery procedures

## 📚 Table of Contents

1. [Project Overview](#project-overview)
2. [System Architecture](#system-architecture)
3. [Key Features](#key-features)
4. [Security Capabilities](#security-capabilities)
5. [Deployment Methods](#deployment-methods)
6. [Installation Guide](#installation-guide)
7. [Threat Detection Rules](#threat-detection-rules)
8. [Dashboards & Visualisations](#dashboards--visualisations)
9. [Log Ingestion Pipelines](#log-ingestion-pipelines)
10. [Backup & Disaster Recovery](#backup--disaster-recovery)
11. [User Access Control (RBAC)](#user-access-control-rbac)
12. [Performance Tuning & Memory Management](#performance-tuning--memory-management)
13. [Project Management Board (GitHub)](#project-management-board-github)
14. [Usage Guides](#usage-guides)
15. [Academic Context & Supervisors](#academic-context--supervisors)
16. [License](#license)

## 🏛️ Architecture

GESAP implements a secure, multi-tier architecture with defense-in-depth principles:

- **Data Collection Layer** - Secure Graylog Sidecars and encrypted input channels
- **Processing Layer** - Graylog server cluster with RBAC and security event routing
- **Storage Layer** - Encrypted MongoDB (metadata) and OpenSearch (log data)
- **Presentation Layer** - Secured web interface with custom security dashboards
- **Security Integration Layer** - APIs and connectors for security tools and SIEM platforms

## 📥 Installation Guide

GESAP can be installed through multiple deployment methods, with security-focused configurations.

### Prerequisites

- Ubuntu Server 22.04 LTS or later (hardened configuration)
- Minimum 8GB RAM, 4 CPU cores
- 80GB+ available storage (encrypted)
- Secured network environment with proper segmentation

### Deployment Options

- **Standard** - Single server deployment with full security hardening
- **Clustered** - Multi-node deployment for high availability and incident resilience
- **Containerized** - Security-enhanced Docker-based deployment
- **IaC** - Terraform and Ansible automated deployment with security compliance

## 🛡️ Security Features

GESAP offers advanced security capabilities:

- **Security Information & Event Management (SIEM)** - Comprehensive security event correlation
- **User & Entity Behavior Analytics (UEBA)** - Detect anomalous user activities
- **Threat Intelligence Platform (TIP) Integration** - Connect with OSINT and commercial threat feeds
- **Security Orchestration & Response (SOAR)** - Automated incident response workflows
- **Vulnerability Management Integration** - Correlate logs with vulnerability data
- **Forensic Analysis** - Advanced tools for security investigations

## 🔍 Threat Detection

Built-in detection capabilities include:

- Pre-configured detection rules for common attack patterns
- Brute force attack detection
- Privilege escalation monitoring
- Data exfiltration detection
- Network scanning and reconnaissance alerts
- Malware and C2 communication detection
- Zero-day attack anomaly detection

## 📊 Custom Dashboards

GESAP includes security-focused dashboards:

- Security Operations Center (SOC) Overview
- Threat Intelligence Dashboard
- Network Security Monitoring
- Cloud Security Posture
- Compliance Status Dashboard
- Advanced Threat Hunting Interface

## 🔒 Security Hardening

Defense-in-depth security implementation:

- TLS 1.3 encryption for all communications
- Advanced role-based access control
- Two-factor authentication with hardware token support
- Comprehensive security audit logging
- Network traffic encryption and segmentation
- Content security policies and WAF integration

## 🤖 Machine Learning Features

GESAP integrates advanced security analytics capabilities:

- Behavioral anomaly detection
- Predictive threat analytics
- Attack pattern recognition
- Automated threat classification
- Security-focused clustering analysis
- Outlier detection for zero-day threats

## 🛡️ SIEM Capabilities

Full-featured SIEM functionality:

- Real-time security event correlation
- Custom correlation rules engine
- Incident case management
- Automated security reporting
- Compliance monitoring and alerting
- Threat intelligence enrichment

## 🛠️ Maintenance

Security-focused maintenance features:

- Secure automated backup processes
- Encrypted index management
- Security performance monitoring
- Secure upgrade procedures
- Continuous integrity checking

## 📚 User Guides

Cybersecurity-focused documentation:

- Security Administrator Guide
- SOC Analyst Handbook
- Threat Hunting Procedures
- Security Developer Integration Manual
- Incident Response Workflows

## 🎓 Academic Context

This project was developed as part of a final year cybersecurity degree program. The GESAP platform demonstrates advanced implementation of security monitoring, threat detection, and incident response capabilities. The solution is designed to provide enterprise-grade security visibility while showcasing technical proficiency in modern cybersecurity operations center (SOC) practices.

## 🤝 Contributing

We welcome contributions to GESAP! Please read our Contributing Guidelines before submitting a pull request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

<p align="center">
  <sub>Developed as part of a Final Year Cybersecurity Project</sub><br>
  <sub>© 2025 Athena Parsa</sub>
</p>
