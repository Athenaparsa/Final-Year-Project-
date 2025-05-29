# 🔐 GESAP Handover & Account Reset Instructions

This document provides handover information and secure credential reset instructions for future users and administrators of the Graywatch Enterprise Security & Analytics Platform (GESAP).

---

## 👥 Default Roles & Assigned Responsibilities

| Username | Role    | Description                                |
|----------|---------|--------------------------------------------|
| `admin`  | Admin   | Full access to system configuration         |
| `analyst`| Analyst | Read-only access to dashboards              |
| `hunter` | Hunter  | Access to detection rules and alert streams |

**Table 1.** GESAP Default Users and Roles.

---

## 🔄 Account Reset Instructions

### 🛠️ Method 1: Using Graylog Command-Line (Preferred)

```bash
graylogctl users list
graylogctl users reset-password <username>
    Replace <username> with admin, analyst, or hunter

    Follow the on-screen prompt to set a new password

🧮 Method 2: MongoDB Manual Reset (Advanced)

Only use if Graylog CLI is unavailable:

    Access MongoDB:

mongo

    Select the Graylog database:

use graylog

    Replace the password hash manually (example shown below):

db.users.updateOne(
  { "username": "admin" },
  { $set: { "password": "<bcrypt_hash_here>" } }
)

⚠️ Always generate a valid bcrypt hash using secure tools such as bcrypt-generator.com or a secure Python script. Do not use plaintext passwords.
🧳 Additional Handover Notes

    🗃️ System backup is scheduled via cron using graylog_backup.sh

    🧠 Detection rules are stored under System > Pipelines

    🛡️ RBAC is configured and enforced across users

    📦 Log rotation, snapshot, and resource protection are enabled

    🎓 This system is safe for educational reuse in virtual lab environments

🔄 Recommended Actions for New Term

    Reset all user passwords

    Clear detection logs older than 90 days

    Review snapshot storage capacity

    Rotate access credentials and update recovery keys

    Re-validate RBAC permissions for any new student users

<p align="center"> <sub>Handover prepared by Athena Parsa | Final Year Cybersecurity Project | University of Roehampton</sub> </p> ```
