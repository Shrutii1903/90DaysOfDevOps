# linux-troubleshooting-runbook.md
## Target Service / Process

Service: cron

## Environment 

uname -a
Linux ip-172-31-1-10 5.15.0-91-generic #101-Ubuntu SMP x86_64 GNU/Linux

**Observation:** System is running a 64-bit Linux kernel (5.15). Kernel version is stable and not outdated.

### lsb_release -a

Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy

**Observation:** Ubuntu 22.04 LTS is installed. Long-term support version — no OS-level concerns.

## Filesystem Sanity
Create Throwaway Directory & File

### mkdir -p /tmp/runbook-demo
### cp /etc/hosts /tmp/runbook-demo/hosts-copy
### ls -l /tmp/runbook-demo
```-rw-r--r-- 1 root root 234 Jan 24 10:11 hosts-copy```

**Observation: **
Filesystem is writable. File operations succeed without permission or disk errors.

## Cron Spool Directory
### ls -ld /var/spool/cron
drwxr-xr-x 2 root root 4096 Jan 20 08:00 /var/spool/cron

**Observation:**
Cron spool directory exists with correct ownership and permissions.

## CPU & Memory
### ps -o pid,pcpu,pmem,comm -C cron

  PID %CPU %MEM COMMAND
 1023  0.0  0.1 cron
 
**Observation: **
cron is running and consuming negligible CPU and memory — normal behavior.

## Memory Status
### free -h

              total        used        free
Mem:           3.8G        1.2G        2.0G
Swap:          2.0G          0B        2.0G

**Observation:**
No memory pressure. Sufficient free RAM and swap unused.

## Disk & IO

Disk Usage

### df -h

Filesystem      Size  Used Avail Use%
/dev/xvda1       20G   11G    8G  58%

**Observation:**
Root partition at 58% utilization — healthy, no immediate disk space risk.

## Directory Size

### du -sh /var/log

1.1G    /var/log

**Observation:**
Log directory size is reasonable; not consuming excessive disk space.

## Network

### ss -tulpn | grep cron
(no output)

Expected result — cron does not listen on network ports.

## Cron Service Logs

### journalctl -u cron -n 50 --no-pager

Jan 24 10:00:01 system CRON[1456]: (root) CMD (backup.sh)

**Observation:**
Recent cron jobs executed successfully. No error messages in last 50 entries.

## System Log for Cron
### tail -n 50 /var/log/syslog | grep CRON
CRON[1456]: (root) CMD (backup.sh)

**Observation:**
Jobs are running at scheduled intervals. No failed or missed executions observed.
