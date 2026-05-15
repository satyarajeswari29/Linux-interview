# Linux Commands Handbook for DevOps Engineers

## Introduction

This handbook contains:

* Important Linux commands for DevOps engineers
* Real-time production use cases
* When and where to use commands
* Practical examples
* Interview questions for each topic

---

# 1. pwd Command

## Purpose

Displays the current working directory.

## Syntax

```bash
pwd
```

## Real-Time Use Case

While troubleshooting production servers, engineers verify the current directory before executing scripts or deleting files.

Example:

```bash
cd /var/log
pwd
```

Output:

```bash
/var/log
```

## Interview Questions

1. What does pwd command do?
2. Difference between absolute and relative paths?
3. Why is knowing current directory important in production?

---

# 2. ls Command

## Purpose

Lists files and directories.

## Common Options

```bash
ls
ls -l
ls -a
ls -lh
ls -lrt
```

## Real-Time Use Case

Used for:

* Verifying deployment artifacts
* Checking log files
* Monitoring file timestamps

Example:

```bash
ls -lrt /var/log
```

## Important Flags

| Option | Purpose             |
| ------ | ------------------- |
| -l     | Long listing        |
| -a     | Hidden files        |
| -h     | Human readable size |
| -t     | Sort by time        |
| -r     | Reverse order       |

## Interview Questions

1. Explain ls -lrt.
2. How to display hidden files?
3. Which option shows human-readable file sizes?

---

# 3. cd Command

## Purpose

Changes directory.

## Examples

```bash
cd /etc
cd ..
cd ~
cd -
```

## Real-Time Use Case

Navigating application directories during deployments.

## Interview Questions

1. Difference between cd .. and cd -?
2. How to move to home directory?

---

# 4. mkdir Command

## Purpose

Creates directories.

## Examples

```bash
mkdir project
mkdir -p app/logs/archive
```

## Real-Time Use Case

Creating application directory structures during server setup.

## Interview Questions

1. Explain mkdir -p.
2. What happens if parent directories do not exist?

---

# 5. rm Command

## Purpose

Deletes files and directories.

## Examples

```bash
rm file.txt
rm -r folder
rm -rf temp
```

## Real-Time Use Case

Cleaning old logs and temporary deployment files.

## WARNING

```bash
rm -rf /
```

can destroy the entire server.

## Interview Questions

1. Difference between rm -r and rm -rf?
2. Why is rm -rf dangerous?
3. How to safely remove files in production?

---

# 6. cp Command

## Purpose

Copies files and directories.

## Examples

```bash
cp file1 file2
cp -r app backup/
```

## Real-Time Use Case

Backing up configuration files before modification.

Example:

```bash
cp /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf.bkp
```

## Interview Questions

1. Why backup config files before changes?
2. Explain cp -r.

---

# 7. mv Command

## Purpose

Moves or renames files.

## Examples

```bash
mv old.txt new.txt
mv app /backup/
```

## Real-Time Use Case

Renaming deployment packages.

## Interview Questions

1. Difference between mv and cp?
2. How does mv help in deployments?

---

# 8. touch Command

## Purpose

Creates empty files.

## Example

```bash
touch app.log
```

## Real-Time Use Case

Creating log files manually for applications.

## Interview Questions

1. Can touch modify timestamps?
2. What happens if file already exists?

---

# 9. cat Command

## Purpose

Displays file contents.

## Example

```bash
cat file.txt
```

## Real-Time Use Case

Reading configuration files quickly.

## Interview Questions

1. Difference between cat and less?
2. When should you avoid cat?

---

# 10. less and more

## Purpose

View large files page by page.

## Examples

```bash
less /var/log/messages
more file.txt
```

## Real-Time Use Case

Analyzing large production logs.

## Interview Questions

1. Difference between less and more?
2. Why use less for logs?

---

# 11. head and tail

## Purpose

Display first or last lines.

## Examples

```bash
head -5 file.txt
tail -10 app.log
tail -f app.log
```

## Real-Time Use Case

Monitoring live application logs.

Example:

```bash
tail -f /var/log/messages
```

## Interview Questions

1. Explain tail -f.
2. How to monitor live logs?
3. Difference between head and tail?

---

# 12. grep Command

## Purpose

Searches patterns in files.

## Examples

```bash
grep error app.log
grep -i failed app.log
grep -r java /opt/apps
```

## Real-Time Use Case

Finding errors during production outages.

Example:

```bash
grep ERROR catalina.out
```

## Interview Questions

1. Explain grep -i.
2. How to search recursively?
3. Difference between grep and egrep?

---

# 13. find Command

## Purpose

Search files and directories.

## Examples

```bash
find / -name test.txt
find /var -size +100M
find . -type f
```

## Real-Time Use Case

Finding large files filling server disk.

Example:

```bash
find / -type f -size +1G
```

## Interview Questions

1. How to find files larger than 1GB?
2. Difference between -type f and -type d?
3. Explain find with exec.

---

# 14. chmod Command

## Purpose

Changes permissions.

## Examples

```bash
chmod 777 file
chmod 755 script.sh
chmod +x deploy.sh
```

## Real-Time Use Case

Making deployment scripts executable.

## Interview Questions

1. Explain chmod 777.
2. What is symbolic mode?
3. Why avoid 777 in production?

---

# 15. chown Command

## Purpose

Changes ownership.

## Examples

```bash
chown apache:apache app.log
chown -R tomcat:tomcat /opt/tomcat
```

## Real-Time Use Case

Fixing permission issues for applications.

## Interview Questions

1. Difference between chmod and chown?
2. Why recursive ownership change is important?

---

# 16. df Command

## Purpose

Shows filesystem disk usage.

## Example

```bash
df -h
```

## Real-Time Use Case

Checking disk space before deployments.

## Interview Questions

1. Explain df -h.
2. What causes disk full issues?

---

# 17. du Command

## Purpose

Shows file/directory sizes.

## Examples

```bash
du -sh *
du -sh /var/log
```

## Real-Time Use Case

Finding which directory consumes maximum disk.

## Interview Questions

1. Difference between df and du?
2. How to find largest directory?

---

# 18. ps Command

## Purpose

Displays running processes.

## Examples

```bash
ps -ef
ps aux
```

## Real-Time Use Case

Checking application process status.

## Interview Questions

1. Difference between ps -ef and ps aux?
2. How to identify zombie process?

---

# 19. top Command

## Purpose

Real-time process monitoring.

## Example

```bash
top
```

## Real-Time Use Case

Monitoring CPU and memory spikes.

## Interview Questions

1. What is load average?
2. How to identify high CPU process?

---

# 20. kill Command

## Purpose

Terminates processes.

## Examples

```bash
kill PID
kill -9 PID
```

## Real-Time Use Case

Stopping hung applications.

## Interview Questions

1. Difference between kill and kill -9?
2. Why should SIGKILL be avoided?

---

# 21. systemctl Command

## Purpose

Manage services.

## Examples

```bash
systemctl status httpd
systemctl start nginx
systemctl restart docker
systemctl enable jenkins
```

## Real-Time Use Case

Managing production services.

## Interview Questions

1. Difference between restart and reload?
2. What does enable do?
3. Explain systemd.

---

# 22. netstat / ss

## Purpose

Check ports and network connections.

## Examples

```bash
ss -tulnp
netstat -tulnp
```

## Real-Time Use Case

Checking whether application is listening on required port.

## Interview Questions

1. Difference between netstat and ss?
2. How to identify listening ports?

---

# 23. curl Command

## Purpose

Tests APIs and URLs.

## Examples

```bash
curl google.com
curl -I google.com
curl http://localhost:8080
```

## Real-Time Use Case

Testing application health endpoints.

## Interview Questions

1. Explain curl -I.
2. Why curl is important in DevOps?

---

# 24. wget Command

## Purpose

Downloads files.

## Example

```bash
wget https://example.com/app.zip
```

## Real-Time Use Case

Downloading deployment artifacts.

## Interview Questions

1. Difference between curl and wget?
2. Which tool is preferred for downloads?

---

# 25. tar Command

## Purpose

Archive and compress files.

## Examples

```bash
tar -cvf app.tar app/
tar -xvf app.tar
```

## Real-Time Use Case

Packaging deployments and backups.

## Interview Questions

1. Explain tar -cvf.
2. Difference between tar and zip?

---

# 26. zip and unzip

## Examples

```bash
zip -r app.zip app/
unzip app.zip
```

## Real-Time Use Case

Sharing compressed deployment packages.

## Interview Questions

1. Difference between tar.gz and zip?

---

# 27. ssh Command

## Purpose

Remote server login.

## Example

```bash
ssh ec2-user@65.0.85.109
```

## Real-Time Use Case

Accessing production servers.

## Interview Questions

1. What is SSH?
2. How SSH key authentication works?
3. Difference between public and private key?

---

# 28. scp Command

## Purpose

Copy files between servers.

## Example

```bash
scp app.war ec2-user@server:/opt/apps
```

## Real-Time Use Case

Deployment artifact transfer.

## Interview Questions

1. Difference between scp and rsync?
2. Advantages of rsync?

---

# 29. rsync Command

## Purpose

Efficient file synchronization.

## Example

```bash
rsync -avz app/ backup/
```

## Real-Time Use Case

Incremental backups.

## Interview Questions

1. Why rsync faster than cp?
2. Explain rsync flags.

---

# 30. vi / vim Editor

## Purpose

Edit files.

## Common Commands

```bash
:i
ESC
:wq
:q!
```

## Real-Time Use Case

Editing configuration files in servers.

## Interview Questions

1. Difference between command mode and insert mode?
2. Explain :wq.

---

# 31. sed Command

## Purpose

Stream editor for modifying text.

## Example

```bash
sed 's/8080/9090/g' server.xml
```

## Real-Time Use Case

Automating configuration updates.

## Interview Questions

1. Explain substitute command in sed.
2. Difference between sed and awk?

---

# 32. awk Command

## Purpose

Pattern scanning and processing.

## Example

```bash
awk '{print $1}' file.txt
```

## Real-Time Use Case

Log parsing and report generation.

## Interview Questions

1. Explain fields in awk.
2. Difference between grep and awk?

---

# 33. crontab Command

## Purpose

Schedule jobs.

## Example

```bash
crontab -e
```

Cron Format:

```bash
* * * * * command
```

## Real-Time Use Case

Automated backups and cleanup jobs.

## Interview Questions

1. Explain cron syntax.
2. Difference between cron and anacron?

---

# 34. free Command

## Purpose

Check memory usage.

## Example

```bash
free -m
```

## Real-Time Use Case

Investigating memory issues.

## Interview Questions

1. Difference between free and available memory?
2. What causes memory leaks?

---

# 35. uname Command

## Purpose

Displays OS and kernel info.

## Example

```bash
uname -a
```

## Real-Time Use Case

Verifying server kernel during troubleshooting.

## Interview Questions

1. What is Linux kernel?
2. Explain uname -a.

---

# 36. hostname Command

## Purpose

Displays system hostname.

## Example

```bash
hostname
hostnamectl
```

## Real-Time Use Case

Identifying servers in clusters.

## Interview Questions

1. Difference between hostname and hostnamectl?

---

# 37. ping Command

## Purpose

Tests connectivity.

## Example

```bash
ping google.com
```

## Real-Time Use Case

Checking network reachability.

## Interview Questions

1. What protocol does ping use?
2. Why ping may fail?

---

# 38. traceroute Command

## Purpose

Tracks packet route.

## Example

```bash
traceroute google.com
```

## Real-Time Use Case

Diagnosing network latency.

## Interview Questions

1. How traceroute works?
2. Difference between ping and traceroute?

---

# 39. journalctl Command

## Purpose

View systemd logs.

## Example

```bash
journalctl -u nginx
```

## Real-Time Use Case

Analyzing service failures.

## Interview Questions

1. What is journalctl?
2. Difference between syslog and journalctl?

---

# 40. history Command

## Purpose

Displays command history.

## Example

```bash
history
```

## Real-Time Use Case

Auditing executed commands.

## Interview Questions

1. Where history stored?
2. How to clear history?

---

# DevOps Production Scenario Questions

## Linux Troubleshooting

1. Server disk is 100%. How will you troubleshoot?
2. Application is not accessible. What commands will you use?
3. CPU usage is high. How to identify root cause?
4. Tomcat service failed. How to troubleshoot?
5. Jenkins is not running after reboot. What will you check?
6. Port 8080 is inaccessible. How to debug?
7. How do you monitor logs in real time?
8. How to identify largest files in Linux?
9. How to check failed login attempts?
10. How to automate cleanup jobs?

---

# Common DevOps Linux Command Combination

## Check disk usage

```bash
df -h
```

## Find large files

```bash
find / -type f -size +1G
```

## Check running services

```bash
systemctl status nginx
```

## Monitor logs

```bash
tail -f /var/log/messages
```

## Check listening ports

```bash
ss -tulnp
```

## Check memory

```bash
free -m
```

## Check CPU usage

```bash
top
```

## Restart service

```bash
systemctl restart httpd
```

---

# Linux DevOps Interview Questions With Answers

## 1. What does pwd command do?

### Answer

The `pwd` command displays the present working directory. It helps users identify their current location in the Linux filesystem.

---

## 2. Difference between absolute and relative paths?

### Answer

* Absolute path starts from root (`/`) directory.
* Relative path starts from current directory.

Example:

```bash
Absolute: /var/log/httpd
Relative: ../log/httpd
```

---

## 3. Explain ls -lrt.

### Answer

* `l` → long listing
* `r` → reverse order
* `t` → sort by modification time

Used to view latest modified files at bottom.

---

## 4. Difference between rm -r and rm -rf?

### Answer

* `rm -r` removes directories recursively.
* `rm -rf` forcefully removes directories without confirmation.

---

## 5. Why is rm -rf dangerous?

### Answer

It can permanently delete critical system files without confirmation.

Example:

```bash
rm -rf /
```

can destroy the Linux system.

---

## 6. Difference between cp and mv?

### Answer

* `cp` copies files.
* `mv` moves or renames files.

---

## 7. Explain tail -f.

### Answer

`tail -f` continuously monitors log files in real time.

Example:

```bash
tail -f /var/log/messages
```

Used heavily in production troubleshooting.

---

## 8. Explain grep -i.

### Answer

`-i` performs case-insensitive search.

Example:

```bash
grep -i error app.log
```

---

## 9. How to find files larger than 1GB?

### Answer

```bash
find / -type f -size +1G
```

Used when server disk becomes full.

---

## 10. Difference between chmod and chown?

### Answer

* `chmod` changes file permissions.
* `chown` changes file ownership.

---

## 11. Why avoid chmod 777 in production?

### Answer

It gives read, write, execute access to everyone, causing security risks.

---

## 12. Difference between df and du?

### Answer

* `df` shows filesystem disk usage.
* `du` shows directory/file usage.

---

## 13. Difference between ps -ef and top?

### Answer

* `ps -ef` gives snapshot of running processes.
* `top` provides real-time monitoring.

---

## 14. Difference between kill and kill -9?

### Answer

* `kill` sends graceful termination signal.
* `kill -9` forcefully kills process.

---

## 15. What is load average in Linux?

### Answer

Load average represents CPU workload over:

* 1 minute
* 5 minutes
* 15 minutes

High load average may indicate CPU bottleneck.

---

## 16. Difference between restart and reload in systemctl?

### Answer

* `restart` completely stops and starts service.
* `reload` reloads configuration without stopping service.

---

## 17. Difference between netstat and ss?

### Answer

`ss` is modern and faster replacement for `netstat`.

---

## 18. Explain curl -I.

### Answer

Fetches only HTTP headers.

Used for:

* checking status code
* verifying server response
* testing APIs

---

## 19. Difference between curl and wget?

### Answer

* `curl` mainly for APIs and requests.
* `wget` mainly for downloading files.

---

## 20. Explain tar -cvf.

### Answer

* `c` → create archive
* `v` → verbose output
* `f` → filename

Example:

```bash
tar -cvf app.tar app/
```

---

## 21. What is SSH?

### Answer

SSH (Secure Shell) is a secure protocol used for remote server access.

---

## 22. Difference between scp and rsync?

### Answer

* `scp` copies complete files.
* `rsync` transfers only changed portions.

`rsync` is faster for backups.

---

## 23. Explain sed substitute command.

### Answer

```bash
sed 's/old/new/g' file
```

* `s` → substitute
* `g` → global replacement

---

## 24. Difference between sed and awk?

### Answer

* `sed` modifies text.
* `awk` processes columns and patterns.

---

## 25. Explain cron syntax.

### Answer

```bash
* * * * * command
```

Fields:

```text
minute hour day month weekday
```

---

## 26. What causes high CPU usage?

### Answer

* Infinite loops
* High traffic
* Memory leaks
* Inefficient applications
* Too many processes

---

## 27. How to troubleshoot server disk full issue?

### Answer

Commands used:

```bash
df -h
du -sh *
find / -type f -size +1G
```

Steps:

1. Check filesystem usage.
2. Identify large directories.
3. Find large files.
4. Delete/archive unnecessary files.

---

## 28. How to troubleshoot application not accessible?

### Answer

Commands used:

```bash
systemctl status httpd
ss -tulnp
curl localhost
journalctl -xe
```

Steps:

1. Verify service running.
2. Check listening ports.
3. Verify firewall/security groups.
4. Check logs.

---

## 29. How to monitor logs in real time?

### Answer

```bash
tail -f app.log
```

---

## 30. How to check memory usage?

### Answer

```bash
free -m
```

or

```bash
top
```

---

# Final Advice for DevOps Interviews

Focus on:

* Real-time troubleshooting
* Production scenarios
* Log analysis
* Service management
* Networking basics
* Disk and memory troubleshooting
* Automation using shell scripting
* File permissions and security

Most interviewers expect:

1. Command knowledge
2. Why command is used
3. Real-time production examples
4. Troubleshooting ability
5. Root cause analysis approach
