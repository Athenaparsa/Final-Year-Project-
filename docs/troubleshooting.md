# 🛠️ GESAP Troubleshooting Handbook

This guide documents common errors, misconfigurations, and runtime failures encountered during deployment and operation of the Graywatch Enterprise Security & Analytics Platform (GESAP). It is intended for student system administrators and SOC analysts.

---

## 🚫 1. Common Graylog Errors

### ❗ Error: `index_not_found_exception`

**Cause:** Elasticsearch service not ready when Graylog starts  
**Fix:**

```bash
sudo systemctl restart graylog-server
    Add a delay in Graylog’s systemd unit:

sudo systemctl edit graylog-server
# Add:
[Unit]
After=opensearch.service

❗ Error: Graylog UI not loading

Cause: Java version, port binding, or Nginx misconfig
Fix:

    Check port:

sudo netstat -tuln | grep 9000

    Ensure Java 17 is installed:

java -version

    Restart Nginx and Graylog:

sudo systemctl restart nginx
sudo systemctl restart graylog-server

🧱 2. MongoDB and OpenSearch Failures
❗ Error: MongoDB connection refused

Fix:

sudo systemctl start mongodb
sudo systemctl enable mongodb

Check port 27017 is open:

telnet localhost 27017

❗ Error: OpenSearch fails to start

Fix:

    Check logs:

journalctl -u opensearch

    Tune JVM heap size:

Edit /etc/opensearch/jvm.options:

-Xms1g
-Xmx1g

    Set correct ownership:

sudo chown -R opensearch:opensearch /var/lib/opensearch

📥 3. Log Ingestion Issues
❗ Problem: Rsyslog logs not arriving

Checklist:

    Confirm rsyslog is running:

sudo systemctl status rsyslog

    Check sender config:

*.* @192.168.123.1:5140;RSYSLOG_SyslogProtocol23Format

    Check Graylog input:

Go to System > Inputs and verify Syslog UDP 5140 is running
❗ Problem: Filebeat logs missing

Fix:

    Test connection:

filebeat test output

    Restart Filebeat:

sudo systemctl restart filebeat

    Check modules or prospector paths in filebeat.yml

🧠 4. Detection Rules Not Firing
❗ Problem: Brute Force or Exfiltration rules not triggering

Fix:

    Go to System > Pipelines > Manage Rules

    Confirm pipeline is connected to a stream

    Check rule conditions:

when
  count("ssh_failed", within(5m)) > 5

    Ensure logs contain expected fields (e.g., ssh_failed)

💾 5. Backup & Snapshot Failures
❗ Error: Snapshot repository not found

Fix:

    Add this to /etc/opensearch/opensearch.yml:

path.repo: ["/mnt/graylog_snapshots"]

    Create directory and set permissions:

sudo mkdir /mnt/graylog_snapshots
sudo chown -R opensearch:opensearch /mnt/graylog_snapshots

    Restart OpenSearch:

sudo systemctl restart opensearch

🧩 6. Nginx Issues (HTTPS or Proxy)
❗ Problem: Graylog UI not reachable through Nginx

Fix:

    Check site config /etc/nginx/sites-available/graylog

    Ensure the proxy settings match Graylog’s web interface:

location / {
    proxy_pass http://127.0.0.1:9000;
    proxy_http_version 1.1;
    proxy_set_header Host $host;
}

    Restart:

sudo systemctl restart nginx

🧼 7. Cleaning Up Logs and Memory

    Rotate system logs:

sudo logrotate -f /etc/logrotate.conf

    Clear journal logs:

sudo journalctl --vacuum-time=7d

    Monitor memory:

free -h

    Add swap (if missing):

sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

