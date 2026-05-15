# Daily Used Linux Commands for DevOps Engineers in Production

These are the most commonly used Linux commands in real-time DevOps production environments for:

* Server troubleshooting
* Application monitoring
* Deployment
* Networking
* Logs analysis
* Disk/Memory management
* Service management

---

# 1. pwd → Present Working Directory

## Purpose

Shows current directory.

```bash id="ptv1l4"
pwd
```

## Production Use Case

Before deleting files or running scripts, engineers verify current location.

---

# 2. ls → List Files

## Common Commands

```bash id="xj6c2m"
ls
ls -l
ls -lrt
ls -lh
ls -a
```

## Production Use Case

* Check deployment files
* Verify logs
* Identify latest modified files

### Most used:

```bash id="6ol9qx"
ls -lrt
```

Shows latest modified files at bottom.

---

# 3. cd → Change Directory

```bash id="r0h2sd"
cd /var/log
cd ..
cd ~
cd -
```

## Production Use Case

Navigate between application directories.

---

# 4. cat → View File Content

```bash id="10sh1t"
cat file.txt
```

## Production Use Case

Quickly check configuration files.

Example:

```bash id="6ndfdb"
cat /etc/httpd/conf/httpd.conf
```

---

# 5. less / more → View Large Files

```bash id="3zd0qc"
less app.log
```

## Production Use Case

Analyze large logs safely.

---

# 6. tail → Monitor Logs

## Most Important DevOps Command

```bash id="p6t8m7"
tail -f app.log
```

## Production Use Case

Monitor live application logs during:

* deployments
* outages
* incidents
* troubleshooting

Example:

```bash id="cxoj7r"
tail -f /var/log/messages
```

---

# 7. grep → Search Logs

```bash id="q0gjck"
grep ERROR app.log
grep -i failed app.log
```

## Production Use Case

Find:

* errors
* exceptions
* failed requests
* warnings

Example:

```bash id="km7mno"
grep ERROR catalina.out
```

---

# 8. find → Search Files

```bash id="szuv4o"
find / -name "*.log"
find / -size +1G
```

## Production Use Case

Find:

* large files
* logs
* backup files

Example:

```bash id="k92ctn"
find / -type f -size +1G
```

Used when disk becomes full.

---

# 9. df → Disk Space

```bash id="c6d3vr"
df -h
```

## Production Use Case

Check filesystem usage.

Critical during:

* outages
* deployments
* log issues

---

# 10. du → Directory Size

```bash id="s0zuvm"
du -sh *
```

## Production Use Case

Find which directory consumes more disk space.

---

# 11. top → Real-Time Monitoring

```bash id="ep9dzt"
top
```

## Production Use Case

Monitor:

* CPU usage
* memory
* load average
* processes

---

# 12. ps → Running Processes

```bash id="78q2df"
ps -ef
ps aux
```

## Production Use Case

Check if application process is running.

Example:

```bash id="llgn93"
ps -ef | grep tomcat
```

---

# 13. kill → Stop Process

```bash id="e1m8zl"
kill PID
kill -9 PID
```

## Production Use Case

Terminate hung applications.

---

# 14. systemctl → Manage Services

## Most Used Command in Production

```bash id="gc6p9t"
systemctl status nginx
systemctl restart httpd
systemctl stop docker
systemctl start jenkins
```

## Production Use Case

Manage:

* nginx
* apache
* docker
* jenkins
* tomcat
* kubelet

---

# 15. journalctl → Service Logs

```bash id="rx9om7"
journalctl -u nginx
journalctl -xe
```

## Production Use Case

Troubleshoot failed services.

---

# 16. ss → Check Ports

```bash id="v6j3wq"
ss -tulnp
```

## Production Use Case

Verify application is listening on required port.

Example:

```bash id="eknkgx"
ss -tulnp | grep 8080
```

---

# 17. curl → Test Application/API

```bash id="70e60i"
curl localhost:8080
curl -I google.com
```

## Production Use Case

Check:

* app health
* API response
* server availability

---

# 18. ping → Network Connectivity

```bash id="cmvjqr"
ping google.com
```

## Production Use Case

Verify internet/network connectivity.

---

# 19. traceroute → Network Path

```bash id="5b0ezv"
traceroute google.com
```

## Production Use Case

Diagnose network latency.

---

# 20. free → Memory Usage

```bash id="quq5lk"
free -m
```

## Production Use Case

Check RAM utilization.

---

# 21. chmod → File Permissions

```bash id="b0htk0"
chmod 755 script.sh
chmod +x deploy.sh
```

## Production Use Case

Grant execution permission to scripts.

---

# 22. chown → Change Ownership

```bash id="sww9nh"
chown apache:apache app.log
```

## Production Use Case

Fix application permission issues.

---

# 23. tar → Backup & Archive

```bash id="rmzjzc"
tar -cvf backup.tar app/
tar -xvf backup.tar
```

## Production Use Case

Take backups before deployments.

---

# 24. zip / unzip

```bash id="jlwmgb"
zip -r app.zip app/
unzip app.zip
```

## Production Use Case

Transfer compressed deployment files.

---

# 25. ssh → Remote Login

```bash id="w1bxt9"
ssh ec2-user@server-ip
```

## Production Use Case

Access production servers securely.

---

# 26. scp → Copy Files to Server

```bash id="6y18zb"
scp app.war ec2-user@server:/opt/apps
```

## Production Use Case

Deploy artifacts to servers.

---

# 27. rsync → Fast Synchronization

```bash id="9cn1kj"
rsync -avz app/ backup/
```

## Production Use Case

Incremental backup and deployment.

---

# 28. crontab → Schedule Jobs

```bash id="wjlwmx"
crontab -e
```

## Production Use Case

Automate:

* backups
* cleanup
* monitoring scripts

---

# 29. vi / vim → Edit Files

```bash id="9f0rqs"
vi file.txt
```

## Production Use Case

Modify:

* configs
* scripts
* application properties

---

# 30. history → Command History

```bash id="gyfqlr"
history
```

## Production Use Case

Audit executed commands.

---

# 31. uname → OS Information

```bash id="vfh1xq"
uname -a
```

## Production Use Case

Check kernel version during troubleshooting.

---

# 32. hostnamectl → Server Info

```bash id="g79v0t"
hostnamectl
```

## Production Use Case

Verify hostname and OS details.

---

# 33. uptime → Server Uptime

```bash id="y8opxf"
uptime
```

## Production Use Case

Check:

* server uptime
* load average

---

# 34. whoami → Current User

```bash id="m7hjlwm"
whoami
```

## Production Use Case

Verify logged-in user before critical actions.

---

# 35. sudo → Execute as Root

```bash id="brpq8n"
sudo systemctl restart nginx
```

## Production Use Case

Run admin commands securely.

---

# Most Common Production Troubleshooting Flow

## Application Down

```bash id="pvjlwm"
systemctl status nginx
ss -tulnp
curl localhost
journalctl -xe
tail -f /var/log/messages
```

---

# Disk Full Issue

```bash id="onl07n"
df -h
du -sh *
find / -type f -size +1G
```

---

# High CPU Usage

```bash id="4d9jho"
top
ps -ef
```

---

# Memory Issue

```bash id="3ixgkw"
free -m
top
```

---

# Port Not Accessible

```bash id="f2z0on"
ss -tulnp
firewall-cmd --list-all
```

---

# Daily Commands Every DevOps Engineer Must Master

| Area            | Important Commands     |
| --------------- | ---------------------- |
| Logs            | tail, grep, less       |
| Monitoring      | top, ps, free, uptime  |
| Disk            | df, du, find           |
| Services        | systemctl, journalctl  |
| Networking      | ss, ping, curl         |
| Files           | cp, mv, rm, chmod      |
| Remote Access   | ssh, scp, rsync        |
| Automation      | crontab                |
| Editing         | vi/vim                 |
| Troubleshooting | grep, tail, journalctl |
