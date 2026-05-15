# DevOps Production Skills — Real-Time Troubleshooting Guide

As a DevOps engineer with 4 years of experience, these are the most important production skills interviewers expect.

---

# 1. Real-Time Troubleshooting

## Goal

Identify and fix production issues quickly.

---

# Scenario 1: Website Not Accessible

## Symptoms

* Site down
* Timeout error
* Users cannot access application

---

## Step-by-Step Troubleshooting

### Step 1: Check Service Status

```bash id="w0m4pl"
systemctl status nginx
```

or

```bash id="y9z2kc"
systemctl status httpd
```

---

### Step 2: Check Listening Port

```bash id="u4q7xr"
ss -tulnp | grep 80
```

---

### Step 3: Check Logs

```bash id="i1k8vq"
tail -f /var/log/nginx/error.log
```

or

```bash id="w7r0mz"
journalctl -xe
```

---

### Step 4: Check Firewall

```bash id="q6n9wd"
firewall-cmd --list-all
```

---

### Step 5: Check EC2 Security Groups

Verify:

* Port 80 open
* Port 443 open

---

# Interview Question

## How do you troubleshoot application downtime?

### Answer

1. Verify service status.
2. Check listening ports.
3. Analyze logs.
4. Check firewall/security groups.
5. Verify DNS and network connectivity.
6. Restart services if required.

---

# 2. Production Scenarios

---

# Scenario 2: High CPU Usage

## Check CPU Usage

```bash id="n3m8xq"
top
```

or

```bash id="l8p1vc"
htop
```

---

## Find High CPU Process

```bash id="q5r2zn"
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head
```

---

## Kill Problematic Process

```bash id="g0v4qt"
kill -9 PID
```

---

# Interview Question

## What causes high CPU usage?

### Answer

* Infinite loops
* Heavy traffic
* Inefficient queries
* Memory leaks
* Too many processes

---

# Scenario 3: Disk Full

## Check Filesystem Usage

```bash id="r1t6kw"
df -h
```

---

## Find Large Directories

```bash id="g4m0xp"
du -sh /*
```

---

## Find Large Files

```bash id="h9q3vb"
find / -type f -size +1G
```

---

## Clear Old Logs

```bash id="j2n7xs"
find /var/log -name "*.log" -mtime +30 -delete
```

---

# Interview Question

## How do you troubleshoot disk full issues?

### Answer

1. Check filesystem usage using `df -h`
2. Identify large directories using `du`
3. Find large files using `find`
4. Archive or remove unnecessary logs/files

---

# 3. Log Analysis

Logs are the heart of troubleshooting.

---

# Important Log Commands

---

## Monitor Logs Live

```bash id="j5v9rk"
tail -f app.log
```

---

## Search Errors

```bash id="j4k8xn"
grep ERROR app.log
```

---

## Search Case Insensitive

```bash id="s7z0vm"
grep -i exception app.log
```

---

## Show Context Around Errors

```bash id="d8m3wr"
grep -C 5 ERROR app.log
```

---

## Count Errors

```bash id="a1x5qv"
grep ERROR app.log | wc -l
```

---

# Real-Time Production Example

## Tomcat Application Failure

```bash id="w8p2yc"
tail -f catalina.out
```

Search exceptions:

```bash id="o0m7zt"
grep Exception catalina.out
```

---

# Interview Question

## How do you analyze production logs?

### Answer

1. Monitor logs using `tail -f`
2. Search errors using `grep`
3. Check timestamps
4. Identify recurring failures
5. Correlate logs with deployments/events

---

# 4. Service Management

Most production systems use systemd.

---

# Important Commands

---

## Check Service Status

```bash id="g9n4xw"
systemctl status nginx
```

---

## Start Service

```bash id="o6v2yk"
systemctl start nginx
```

---

## Restart Service

```bash id="q2m9pv"
systemctl restart nginx
```

---

## Enable Service at Boot

```bash id="b1x8zw"
systemctl enable nginx
```

---

## View Logs

```bash id="m5r0qt"
journalctl -u nginx
```

---

# Production Use Cases

* Restart failed services
* Verify deployments
* Troubleshoot startup issues
* Analyze crashes

---

# Interview Question

## Difference between restart and reload?

### Answer

* `restart` stops and starts service completely
* `reload` reloads configuration without downtime

---

# 5. Networking Basics

Very important for DevOps troubleshooting.

---

# Check Open Ports

```bash id="w3q7zn"
ss -tulnp
```

---

# Check Specific Port

```bash id="h7m2xr"
ss -tulnp | grep 8080
```

---

# Ping Connectivity

```bash id="i5x8vt"
ping google.com
```

---

# DNS Testing

```bash id="j9r1wm"
nslookup google.com
```

---

# API Testing

```bash id="x2n6qv"
curl localhost:8080
```

---

# Trace Network Path

```bash id="u4k9pz"
traceroute google.com
```

---

# Production Scenario

## Port 8080 Not Accessible

### Troubleshooting

```bash id="e7m3wc"
systemctl status tomcat
ss -tulnp | grep 8080
firewall-cmd --list-all
```

Check:

* service running?
* firewall?
* security groups?
* app crash?

---

# Interview Question

## Difference between TCP and UDP?

### Answer

### TCP

* Connection-oriented
* Reliable
* Slower
* Used in HTTP, HTTPS, SSH

### UDP

* Connectionless
* Faster
* No guarantee
* Used in streaming, DNS

---

# 6. Disk and Memory Troubleshooting

---

# Check Memory

```bash id="r8p0xw"
free -m
```

---

# Real-Time Monitoring

```bash id="n0v5zt"
top
```

---

# Check Swap Usage

```bash id="m3k9qx"
swapon -s
```

---

# Check Load Average

```bash id="s2q7wr"
uptime
```

---

# Find Memory-Hungry Processes

```bash id="u7x1zn"
ps aux --sort=-%mem | head
```

---

# Interview Question

## What is load average?

### Answer

Load average represents system workload over:

* 1 minute
* 5 minutes
* 15 minutes

High load indicates CPU bottleneck.

---

# 7. Automation Using Shell Scripting

Automation is core DevOps skill.

---

# Basic Script Example

```bash id="t9m4xw"
#!/bin/bash

DATE=$(date)

echo "Backup started at $DATE"

tar -cvf backup.tar /opt/apps

echo "Backup completed"
```

---

# Make Script Executable

```bash id="g6v1pz"
chmod +x backup.sh
```

---

# Run Script

```bash id="n2k8qx"
./backup.sh
```

---

# Automate Using Cron

```bash id="q9x4wr"
crontab -e
```

Example:

```bash id="v5m0zn"
0 2 * * * /opt/scripts/backup.sh
```

Runs daily at 2 AM.

---

# Production Use Cases

* Automated backups
* Health monitoring
* Cleanup jobs
* Deployment automation

---

# Interview Question

## Why shell scripting important in DevOps?

### Answer

Shell scripting automates repetitive tasks, reduces manual effort, improves consistency, and speeds up operations.

---

# 8. File Permissions and Security

Critical in production systems.

---

# Check Permissions

```bash id="f3v8qx"
ls -l
```

---

# Change Permissions

```bash id="m6x1zt"
chmod 755 script.sh
```

---

# Change Ownership

```bash id="q0n4wr"
chown nginx:nginx app.log
```

---

# Add Execute Permission

```bash id="s8k2pv"
chmod +x deploy.sh
```

---

# Secure SSH Key

```bash id="v1q7mx"
chmod 400 mykey.pem
```

---

# Production Use Cases

* Fix application access issues
* Secure sensitive files
* Prevent unauthorized access

---

# Interview Question

## Explain chmod 777.

### Answer

```text id="f8m3zn"
Owner  : rwx
Group  : rwx
Others : rwx
```

Everyone gets full access.

⚠ Avoid in production due to security risks.

---

# Most Important Daily Production Commands

| Area            | Commands                 |
| --------------- | ------------------------ |
| Logs            | tail, grep, journalctl   |
| CPU/Memory      | top, free, ps            |
| Disk            | df, du, find             |
| Networking      | ss, curl, ping           |
| Services        | systemctl                |
| Automation      | crontab, shell scripting |
| Security        | chmod, chown             |
| Troubleshooting | grep, tail, curl         |
