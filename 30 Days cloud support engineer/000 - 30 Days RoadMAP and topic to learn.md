# 🚀 Complete 30-Day DevOps Support Engineer Learning Roadmap v2.0

**11 Topics | 30 Days | 3.5 Hours/Day | Job-Ready Focus**

---

## 📊 SECTION 1: TOPIC PRIORITIZATION & TIME ALLOCATION

|#|Topic|Priority|Days Allocated|Daily Hours|
|---|---|---|---|---|
|1|Linux & OS Fundamentals|🔴 Must Learn|Days 1–5|3.5 hrs|
|2|Scripting & Automation|🔴 Must Learn|Days 6–8|3.5 hrs|
|3|Networking Fundamentals|🔴 Must Learn|Days 9–11|3.5 hrs|
|4|Git & Version Control|🔴 Must Learn|Days 12–13|3.5 hrs|
|5|Docker|🔴 Must Learn|Days 14–16|3.5 hrs|
|6|CI/CD Pipelines|🔴 Must Learn|Days 17–19|3.5 hrs|
|7|Monitoring & Observability|🔴 Must Learn|Days 20–22|3.5 hrs|
|8|Cloud Platforms (AWS)|🟡 Good to Learn|Days 23–24|3.5 hrs|
|9|IaC (Terraform)|🟡 Good to Learn|Day 25|3.5 hrs|
|10|Kubernetes|🟡 Good to Learn|Day 26|3.5 hrs|
|11|Security (DevSecOps)|🟡 Good to Learn|Day 27|3.5 hrs|
|—|Final Project|🏗️|Days 28–29|3.5 hrs|
|—|Interview Prep|🎯|Day 30|3.5 hrs|

---

## 📚 SECTION 2: PER-TOPIC DEEP BREAKDOWN

---

### ━━━ TOPIC 1: Linux & OS Fundamentals 🔴

**Days 1–5 | Priority: MUST LEARN**

#### 80/20 Concepts

- Filesystem hierarchy (`/etc`, `/var`, `/tmp`, `/home`, `/proc`)
- Navigation (`ls`, `cd`, `pwd`, `find`, `locate`, `tree`)
- File operations (`cp`, `mv`, `rm`, `touch`, `cat`, `less`, `head`, `tail`)
- Permissions (`chmod`, `chown`, `umask`, `sudo`, `sudoers`)
- Process management (`ps`, `top`, `htop`, `kill`, `nice`, `systemctl`)
- Disk & memory (`df`, `du`, `free`, `lsblk`, `mount`)
- User management (`useradd`, `usermod`, `passwd`, `groups`)
- Package management (`apt`, `yum`, `dnf`)
- Log management (`/var/log/`, `journalctl`, `tail -f`, `grep`)
- Cron jobs (`crontab -e`, timing syntax)
- SSH (`ssh`, `scp`, `rsync`, `ssh-keygen`, `authorized_keys`)
- Text processing (`grep`, `awk`, `sed`, `cut`, `sort`, `wc`)

#### Theory

- **What:** Linux is the operating system that powers ~90% of all production servers, containers, and cloud infrastructure
- **Why:** Every DevOps tool — Docker, Jenkins, Kubernetes, Ansible — runs on Linux. Support Engineers SSH into Linux servers dozens of times a day
- **Where:** Web servers (nginx, apache), application servers, CI/CD agents, containers, cloud VMs, database servers
- **Common Interview Questions:**
    - "How do you find which process is using port 8080?"
    - "A server's disk is 100% full. Walk me through your steps."
    - "Explain what file permission 755 means."
    - "How do you check why a service failed to start?"
    - "What's the difference between `kill` and `kill -9`?"
    - "How do you find files modified in the last 24 hours?"

#### Practical Labs

```bash
# ── LAB 1: Filesystem Exploration ──────────────────────────────
ls -la /etc /var /tmp /home /proc
find /var/log -name "*.log" -size +10M
locate nginx.conf    # run: sudo updatedb first
du -sh /var/log/* | sort -rh | head -10

# ── LAB 2: Permissions Deep Dive ───────────────────────────────
# Create test structure
mkdir -p ~/permlab/{public,private,shared}
touch ~/permlab/public/index.html
touch ~/permlab/private/secret.key
touch ~/permlab/shared/data.csv

# Set different permissions
chmod 755 ~/permlab/public/index.html      # rwxr-xr-x
chmod 600 ~/permlab/private/secret.key     # rw-------
chmod 664 ~/permlab/shared/data.csv        # rw-rw-r--

# Verify
ls -la ~/permlab/

# ── LAB 3: Process Management ──────────────────────────────────
# Start a background process
sleep 300 &
sleep 400 &
ps aux | grep sleep
kill %1                         # kill by job number
kill -9 $(pgrep sleep)          # kill all sleep processes

# Service management
sudo systemctl status nginx
sudo systemctl stop nginx
sudo systemctl start nginx
sudo systemctl restart nginx
sudo systemctl enable nginx     # auto-start on boot
sudo journalctl -u nginx -n 50 --no-pager

# ── LAB 4: Disk Investigation ──────────────────────────────────
df -h                           # all filesystems
df -h /                         # root only
du -sh /var/log/*               # size of each log dir
du -ah /tmp | sort -rh | head -20
# Find files > 100MB
find / -type f -size +100M 2>/dev/null

# ── LAB 5: Log Analysis ────────────────────────────────────────
# Generate some nginx traffic first
curl localhost/ 2>/dev/null

# Read logs
tail -f /var/log/nginx/access.log
tail -f /var/log/nginx/error.log
grep "404" /var/log/nginx/access.log | wc -l
grep "500" /var/log/nginx/error.log
journalctl --since "1 hour ago" --until "now"
journalctl -p err -n 20         # only errors

# ── LAB 6: User Management ─────────────────────────────────────
sudo useradd -m -s /bin/bash devopsuser
sudo passwd devopsuser
sudo usermod -aG sudo devopsuser
su - devopsuser                 # switch to user
groups                          # verify sudo group
exit

# ── LAB 7: Text Processing (Critical for log analysis) ─────────
# Parse access log for top IPs
cat /var/log/nginx/access.log | awk '{print $1}' | sort | uniq -c | sort -rn | head -10

# Extract all 5xx errors
grep " 5[0-9][0-9] " /var/log/nginx/access.log

# Replace config value with sed
sed -i 's/worker_processes 1/worker_processes 4/' /etc/nginx/nginx.conf

# Count errors per hour
grep "error" /var/log/syslog | awk '{print $3}' | cut -d: -f1 | sort | uniq -c
```

#### Learning Through Mistakes

| Mistake                | Error Message                     | Troubleshooting              | Fix                                                    |
| ---------------------- | --------------------------------- | ---------------------------- | ------------------------------------------------------ |
| Delete wrong file      | Silent (no error)                 | `ls` shows it's gone         | `sudo extundelete` or restore from backup              |
| Wrong chmod on SSH     | `Permission denied (publickey)`   | `ls -la ~/.ssh/`             | `chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys` |
| Kill wrong process     | Service down unexpectedly         | `ps aux` shows missing       | `systemctl restart <service>`                          |
| Cron doesn't run       | No output, no errors              | `grep CRON /var/log/syslog`  | Check PATH, use full binary paths                      |
| Disk 100% full         | `No space left on device`         | `du -sh /* \| sort -rh`      | Find & remove large files/old logs                     |
| sudo permission denied | `user is not in the sudoers file` | `groups username`            | `usermod -aG sudo username`                            |
| Wrong port in firewall | `Connection refused`              | `netstat -tlnp \| grep PORT` | Open port in UFW/iptables                              |

#### Real DevOps Support Scenarios

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCENARIO 1: "Application returning 502 Bad Gateway"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Step 1: ssh user@server-ip
Step 2: systemctl status nginx        # Is nginx running?
Step 3: systemctl status myapp        # Is app running?
Step 4: journalctl -u myapp -n 50     # Read app logs
Step 5: netstat -tlnp | grep 8080     # Is app listening?
Step 6: curl localhost:8080           # Direct test bypassing nginx
Step 7: nginx -t                      # Test nginx config

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCENARIO 2: "Server extremely slow"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Step 1: top                           # See CPU/memory live
Step 2: ps aux --sort=-%cpu | head -5 # Top CPU consumers
Step 3: free -h                       # Memory usage
Step 4: df -h                         # Disk full = slow
Step 5: iostat -x 1 5                 # Disk I/O wait
Step 6: netstat -an | grep ESTABLISHED | wc -l  # Connection count
Step 7: dmesg | tail -20              # Kernel OOM killer?
```

---

### ━━━ TOPIC 2: Scripting & Automation 🔴

**Days 6–8 | Priority: MUST LEARN**

#### 80/20 Concepts

- Variables, `$1 $2 $@`, quoting rules
- Conditionals — `if/elif/else`, `[[ ]]` vs `[ ]`
- Loops — `for`, `while`, `until`
- Functions — definition, arguments, return values
- Exit codes — `$?`, `exit 0`, `exit 1`
- Error handling — `set -e`, `set -u`, `trap`
- String operations — `${#var}`, `${var%suffix}`, `${var//find/replace}`
- File testing — `-f`, `-d`, `-e`, `-r`, `-w`, `-x`
- Input/output — `read`, `echo`, `printf`, redirects `>`, `>>`, `2>&1`
- Real scripts — health check, backup, log cleaner, disk alert

#### Theory

- **What:** Bash scripting automates repetitive operational tasks
- **Why:** A support engineer who can script saves hours daily — instead of manually checking 50 servers, one script does it in seconds
- **Where:** Deployment automation, health monitoring, backup jobs, incident response, cleanup tasks
- **Common Interview Questions:**
    - "Write a script to check if a service is running and restart it if not"
    - "How do you handle errors in a bash script?"
    - "What is `$?` and when do you use it?"
    - "How do you read a file line by line in bash?"
    - "What is the difference between `[ ]` and `[[ ]]`?"

#### Practical Labs

```bash
# ── LAB 1: Variables & Quoting ─────────────────────────────────
#!/bin/bash
NAME="DevOps"
COUNT=5
FILE_PATH="/var/log/nginx/access.log"

echo "Hello, $NAME"              # Variable expansion
echo "Count: ${COUNT}"           # Explicit braces
echo "Path: ${FILE_PATH}"
echo 'No expansion: $NAME'       # Single quotes = literal

# Argument variables
echo "Script name: $0"
echo "First arg: $1"
echo "All args: $@"
echo "Arg count: $#"

# ── LAB 2: Conditionals ────────────────────────────────────────
#!/bin/bash
# File/directory checks
check_file() {
    local FILE=$1
    if [[ -f "$FILE" ]]; then
        echo "[OK] File exists: $FILE"
    elif [[ -d "$FILE" ]]; then
        echo "[INFO] That's a directory, not a file"
    else
        echo "[ERROR] Not found: $FILE"
        exit 1
    fi
}
check_file "/etc/nginx/nginx.conf"
check_file "/nonexistent/path"

# ── LAB 3: Loops ───────────────────────────────────────────────
#!/bin/bash
SERVERS=("web1" "web2" "web3" "db1")

# For loop over array
for SERVER in "${SERVERS[@]}"; do
    echo "Checking: $SERVER"
    # ping -c 1 $SERVER.company.com > /dev/null 2>&1
    # if [[ $? -eq 0 ]]; then echo "UP"; else echo "DOWN"; fi
done

# While loop reading file
while IFS= read -r LINE; do
    echo "Processing: $LINE"
done < /etc/hosts

# C-style for loop
for i in {1..5}; do
    echo "Iteration: $i"
done

# ── LAB 4: Production-Grade Health Check Script ────────────────
cat > /usr/local/bin/health_check.sh << 'SCRIPT'
#!/bin/bash
set -euo pipefail

# Configuration
SERVICES=("nginx" "postgresql" "redis")
DISK_THRESHOLD=85
MEM_THRESHOLD=90
LOG_FILE="/var/log/health_check.log"
TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

log() {
    echo "[$TIMESTAMP] $1" | tee -a "$LOG_FILE"
}

check_service() {
    local SERVICE=$1
    if systemctl is-active --quiet "$SERVICE"; then
        log "[OK] Service running: $SERVICE"
        return 0
    else
        log "[CRITICAL] Service DOWN: $SERVICE — attempting restart"
        systemctl restart "$SERVICE"
        sleep 3
        if systemctl is-active --quiet "$SERVICE"; then
            log "[RECOVERED] $SERVICE restarted successfully"
        else
            log "[FAILED] $SERVICE could not restart — manual intervention needed"
            return 1
        fi
    fi
}

check_disk() {
    local USAGE
    USAGE=$(df / | awk 'NR==2{print $5}' | tr -d '%')
    if [[ "$USAGE" -gt "$DISK_THRESHOLD" ]]; then
        log "[WARNING] Disk usage at ${USAGE}% (threshold: ${DISK_THRESHOLD}%)"
        # Find top 5 disk consumers
        log "Top disk consumers:"
        du -sh /var/log/* 2>/dev/null | sort -rh | head -5 | tee -a "$LOG_FILE"
    else
        log "[OK] Disk usage: ${USAGE}%"
    fi
}

check_memory() {
    local USAGE
    USAGE=$(free | awk 'NR==2{printf "%.0f", $3/$2*100}')
    if [[ "$USAGE" -gt "$MEM_THRESHOLD" ]]; then
        log "[WARNING] Memory usage at ${USAGE}%"
        ps aux --sort=-%mem | head -5 | tee -a "$LOG_FILE"
    else
        log "[OK] Memory usage: ${USAGE}%"
    fi
}

# Run all checks
log "=== Health Check Started ==="
for svc in "${SERVICES[@]}"; do
    check_service "$svc" || true
done
check_disk
check_memory
log "=== Health Check Complete ==="
SCRIPT
chmod +x /usr/local/bin/health_check.sh

# ── LAB 5: Backup Script ───────────────────────────────────────
cat > /usr/local/bin/backup.sh << 'SCRIPT'
#!/bin/bash
set -euo pipefail

BACKUP_DIR="/backup/$(date +%Y/%m)"
SOURCE_DIR="/var/www/html"
DB_NAME="myapp"
RETENTION_DAYS=7
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p "$BACKUP_DIR"

# Backup files
tar -czf "${BACKUP_DIR}/files_${TIMESTAMP}.tar.gz" "$SOURCE_DIR"
echo "Files backed up: ${BACKUP_DIR}/files_${TIMESTAMP}.tar.gz"

# Backup database
pg_dump "$DB_NAME" | gzip > "${BACKUP_DIR}/db_${TIMESTAMP}.sql.gz"
echo "DB backed up: ${BACKUP_DIR}/db_${TIMESTAMP}.sql.gz"

# Clean old backups
find /backup -name "*.tar.gz" -mtime +$RETENTION_DAYS -delete
find /backup -name "*.sql.gz" -mtime +$RETENTION_DAYS -delete
echo "Old backups cleaned (>${RETENTION_DAYS} days)"

echo "Backup complete at $(date)"
SCRIPT
chmod +x /usr/local/bin/backup.sh
```

#### Learning Through Mistakes

|Mistake|Error|Troubleshooting|Fix|
|---|---|---|---|
|Missing shebang|Runs with wrong shell|`head -1 script.sh`|Add `#!/bin/bash` as line 1|
|Not executable|`Permission denied`|`ls -la script.sh`|`chmod +x script.sh`|
|Wrong quotes|Variable not expanding|`bash -x script.sh`|Use `"$VAR"` not `'$VAR'`|
|Spaces around `=`|`command not found`|`bash -x script.sh`|`VAR="value"` no spaces|
|No full paths in cron|Script works manually, fails in cron|`grep CRON /var/log/syslog`|Use `/usr/bin/systemctl` not just `systemctl`|
|Unbound variable|`unbound variable: NAME`|`set -u` catches it|Always initialize: `NAME=${1:-"default"}`|

---

### ━━━ TOPIC 3: Networking Fundamentals 🔴

**Days 9–11 | Priority: MUST LEARN**

#### 80/20 Concepts

- OSI model (layers 3–7 matter most for support)
- IP addressing — IPv4, CIDR notation, private ranges
- DNS — how resolution works, A/CNAME/MX/TXT records, TTL
- TCP/UDP — ports, connection states, handshake
- HTTP/HTTPS — status codes, headers, methods
- Tools — `ping`, `traceroute`, `dig`, `nslookup`, `curl`, `wget`, `netstat`, `ss`, `tcpdump`, `nmap`
- Firewalls — `ufw`, `iptables`, security groups
- Load balancers — what they do, health checks
- SSL/TLS — certificates, chain of trust, expiry

#### Theory

- **What:** Networking is how computers communicate — understanding it helps diagnose connectivity failures, DNS issues, SSL problems, and port conflicts
- **Why:** 40% of production incidents are network-related — DNS failure, firewall blocking, SSL expiry, wrong port
- **Where:** Between services, between servers, between users and servers, between cloud regions
- **Common Interview Questions:**
    - "A user says they can't reach the website. Walk me through your troubleshooting."
    - "What happens when you type google.com in a browser?"
    - "How do you check if a remote port is open?"
    - "DNS is not resolving. How do you investigate?"
    - "What is the difference between TCP and UDP?"
    - "HTTP 503 vs 502 — what's the difference?"

#### Practical Labs

```bash
# ── LAB 1: DNS Investigation ───────────────────────────────────
# Query DNS records
dig google.com                    # Full DNS response
dig google.com +short             # Just the IP
dig google.com A                  # A record only
dig google.com MX                 # Mail records
dig google.com TXT                # Text/SPF records
dig @8.8.8.8 google.com           # Query specific DNS server
nslookup google.com 8.8.8.8
dig -x 142.250.80.46              # Reverse lookup

# Trace DNS resolution path
dig +trace google.com

# Check your DNS servers
cat /etc/resolv.conf
cat /etc/hosts                    # Local overrides

# ── LAB 2: Port & Connectivity Testing ─────────────────────────
# Ping (ICMP — Layer 3 test)
ping -c 4 google.com
ping -c 4 8.8.8.8

# Trace route to destination
traceroute google.com
mtr google.com                    # Better than traceroute

# Test TCP connectivity
nc -zv google.com 443             # Is port 443 open?
nc -zv 10.0.0.5 5432             # Is postgres reachable?
telnet google.com 80              # Old school method

# Check who is listening on ports
netstat -tlnp                     # All listening ports
ss -tlnp                          # Modern replacement
ss -tlnp | grep :8080             # Specific port
lsof -i :8080                     # Process using port

# ── LAB 3: HTTP Debugging with curl ────────────────────────────
# Basic GET
curl https://httpbin.org/get

# See headers
curl -I https://google.com        # HEAD request (headers only)
curl -v https://google.com        # Verbose — see full negotiation

# Check SSL certificate
curl -vI https://google.com 2>&1 | grep -A5 "SSL"
openssl s_client -connect google.com:443 -servername google.com
# Check cert expiry:
echo | openssl s_client -connect google.com:443 2>/dev/null \
  | openssl x509 -noout -dates

# Test with custom headers
curl -H "Authorization: Bearer TOKEN" https://api.example.com/v1/data
curl -X POST -H "Content-Type: application/json" \
     -d '{"key":"value"}' https://httpbin.org/post

# Follow redirects
curl -L http://google.com -o /dev/null -w "%{http_code}\n"

# ── LAB 4: Firewall Management ─────────────────────────────────
# UFW (Ubuntu)
sudo ufw status verbose
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw allow 22/tcp             # ALWAYS allow SSH first!
sudo ufw deny 3306/tcp            # Block MySQL from outside
sudo ufw enable

# iptables view
sudo iptables -L -n -v

# ── LAB 5: SSL Certificate Troubleshooting ─────────────────────
# Install certbot and get cert (on a domain you own)
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d yourdomain.com
sudo certbot renew --dry-run      # Test auto-renewal

# Check cert validity manually
openssl x509 -in /etc/ssl/certs/ca-certificates.crt -noout -text | head -30
```

#### HTTP Status Codes — Must Know

|Code|Meaning|Common Cause|
|---|---|---|
|200|OK|All good|
|301/302|Redirect|URL changed|
|400|Bad Request|Malformed request|
|401|Unauthorized|Missing/wrong auth|
|403|Forbidden|Permission denied|
|404|Not Found|Wrong URL or missing file|
|429|Too Many Requests|Rate limited|
|500|Internal Server Error|App crash|
|502|Bad Gateway|Upstream app not responding|
|503|Service Unavailable|Overloaded or down|
|504|Gateway Timeout|Upstream too slow|

#### Learning Through Mistakes

|Mistake|Error|Troubleshooting|Fix|
|---|---|---|---|
|UFW blocks SSH|Can't connect to server!|Need console/VNC access|`ufw allow 22` BEFORE `ufw enable`|
|Wrong DNS record|Site resolves to wrong IP|`dig domain.com`|Update A record, wait TTL|
|SSL cert expired|Browser warning, curl fails|`openssl s_client ...`|`certbot renew`|
|Port not open|`Connection refused`|`ss -tlnp \| grep PORT`|Start the service or open firewall|
|DNS cache stale|Old IP resolving|`dig @8.8.8.8 domain.com`|Flush DNS cache or wait TTL|

#### Real DevOps Support Scenarios

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCENARIO: "Website not loading for users"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Step 1: Can YOU access it? (rules out user-specific issue)
  curl -I https://yoursite.com

Step 2: DNS resolving?
  dig yoursite.com +short
  # Expected: your server IP
  # If wrong: DNS misconfigured

Step 3: Server reachable?
  ping yourserver-ip
  nc -zv yourserver-ip 443

Step 4: SSL valid?
  openssl s_client -connect yoursite.com:443

Step 5: Web server running?
  ssh user@server
  systemctl status nginx
  curl localhost:80

Step 6: App running?
  systemctl status myapp
  curl localhost:3000

Step 7: Firewall blocking?
  ufw status
  iptables -L | grep DROP
```

---

### ━━━ TOPIC 4: Git & Version Control 🔴

**Days 12–13 | Priority: MUST LEARN**

#### 80/20 Concepts

- Core workflow — `clone`, `add`, `commit`, `push`, `pull`
- Branching — `branch`, `checkout`, `merge`, `rebase`
- Undoing mistakes — `revert`, `reset`, `stash`
- Remote operations — `remote`, `fetch`, `pull`, `push`
- Merge conflicts — how to resolve
- `.gitignore` — what to exclude
- Tags — `git tag v1.0`
- Git log — `git log --oneline --graph`

#### Theory

- **What:** Git tracks every change to every file over time, enabling collaboration and rollback
- **Why:** All code, config files, Dockerfiles, and IaC live in Git. Support engineers use Git to deploy fixes and rollback bad changes
- **Where:** Every software company uses Git — GitHub, GitLab, Bitbucket
- **Common Interview Questions:**
    - "How do you rollback a bad deployment commit?"
    - "What is the difference between `git merge` and `git rebase`?"
    - "How do you resolve a merge conflict?"
    - "What is `git stash` used for?"
    - "How do you see what changed between two commits?"

#### Practical Labs

```bash
# ── LAB 1: Core Git Workflow ───────────────────────────────────
# Setup
git config --global user.name "Your Name"
git config --global user.email "you@email.com"
git config --global core.editor "vim"

# Create repo and first commit
mkdir myapp && cd myapp
git init
echo "# My DevOps App" > README.md
git add README.md
git commit -m "feat: initial commit"

# Check status and history
git status
git log --oneline
git diff HEAD~1 HEAD

# ── LAB 2: Branching & Merging ─────────────────────────────────
git checkout -b feature/add-health-endpoint
# Make changes
echo "GET /health → 200 OK" >> README.md
git add .
git commit -m "feat: add health check endpoint"

# Merge back
git checkout main
git merge feature/add-health-endpoint
git branch -d feature/add-health-endpoint

# ── LAB 3: Undoing Mistakes ────────────────────────────────────
# Undo last commit (keep changes)
git reset HEAD~1

# Undo last commit (discard changes) — DESTRUCTIVE
git reset --hard HEAD~1

# Revert a specific commit (safe — creates new commit)
git revert abc1234

# Stash work in progress
git stash
git stash list
git stash pop

# ── LAB 4: Merge Conflict Resolution ──────────────────────────
# Intentionally create a conflict
git checkout -b branch-a
echo "Line from branch A" >> conflict.txt
git add . && git commit -m "branch-a change"

git checkout main
echo "Line from main" >> conflict.txt
git add . && git commit -m "main change"

git merge branch-a
# CONFLICT! Edit conflict.txt:
# <<<<<<< HEAD
# Line from main
# =======
# Line from branch A
# >>>>>>> branch-a

# Keep what you want, remove markers, then:
git add conflict.txt
git commit -m "resolve: merge conflict in conflict.txt"

# ── LAB 5: Useful Git Commands ─────────────────────────────────
git log --oneline --graph --all  # Visual branch history
git diff main..feature/branch     # Diff between branches
git blame README.md               # Who changed each line
git bisect start                  # Binary search for bug commit
git shortlog -sn                  # Commits per author
git tag v1.0.0                    # Create tag
git tag -a v1.0.0 -m "Release"   # Annotated tag
```

#### Learning Through Mistakes

|Mistake|Error|Troubleshooting|Fix|
|---|---|---|---|
|Push to wrong branch|Code in wrong branch|`git log --oneline`|`git reset`, create correct branch|
|Commit secrets|API key in git history|`git log` shows secret|`git-secrets` scan, rotate credentials, `git filter-branch`|
|Force push breaks team|Others lose commits|`git reflog` on their machine|Never force push to `main`|
|Merge conflict marks left|App won't start|`grep -r "<<<<<<" .`|Find and fix all conflict markers|

---

### ━━━ TOPIC 5: Docker 🔴

**Days 14–16 | Priority: MUST LEARN**

#### 80/20 Concepts

- Image vs Container vs Registry
- `docker build`, `docker run`, `docker ps`, `docker logs`, `docker exec`
- Port mapping `-p`, volumes `-v`, env vars `-e`
- `docker-compose up/down/logs/ps`
- `docker inspect`, `docker stats`, `docker system prune`
- Dockerfile — `FROM`, `WORKDIR`, `COPY`, `RUN`, `ENV`, `EXPOSE`, `CMD`, `ENTRYPOINT`
- Docker networking — bridge, host, none, custom networks
- Container debugging workflow

#### Theory

- **What:** Docker packages applications with all their dependencies into portable containers that run identically everywhere
- **Why:** Eliminates "works on my machine" problem, enables consistent deployments, makes scaling easy
- **Where:** Every microservice, CI/CD pipeline stage, development environment
- **Common Interview Questions:**
    - "A container keeps restarting. How do you debug it?"
    - "Difference between `CMD` and `ENTRYPOINT` in Dockerfile?"
    - "How do you pass secrets to a container safely?"
    - "What is `docker-compose` and when would you use it?"
    - "How do you see real-time resource usage of containers?"

#### Practical Labs

```bash
# ── LAB 1: Container Lifecycle ─────────────────────────────────
docker pull nginx:latest
docker run -d -p 8080:80 --name webserver nginx
docker ps                                    # Running containers
docker ps -a                                 # All including stopped
docker logs webserver
docker logs webserver --tail=50 -f           # Follow logs
docker exec -it webserver bash               # Shell into container
docker stats                                 # Live resource usage
docker inspect webserver                     # Full JSON config
docker stop webserver
docker rm webserver

# ── LAB 2: Dockerfile Writing ──────────────────────────────────
mkdir myapp && cd myapp
cat > app.py << 'EOF'
from flask import Flask, jsonify
app = Flask(__name__)

@app.route('/health')
def health():
    return jsonify({"status": "healthy", "version": "1.0"})

@app.route('/')
def home():
    return "Hello from Docker!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
EOF

cat > requirements.txt << 'EOF'
flask==3.0.0
EOF

cat > Dockerfile << 'EOF'
FROM python:3.11-slim

# Non-root user (security best practice)
RUN useradd -m appuser

WORKDIR /app

# Copy requirements first (layer caching)
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Switch to non-root user
USER appuser

EXPOSE 5000

HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD curl -f http://localhost:5000/health || exit 1

CMD ["python", "app.py"]
EOF

# Build and run
docker build -t myapp:v1 .
docker run -d -p 5000:5000 --name myapp myapp:v1
curl localhost:5000/health

# ── LAB 3: Docker Compose ──────────────────────────────────────
cat > docker-compose.yml << 'EOF'
version: '3.8'
services:
  app:
    build: .
    ports:
      - "5000:5000"
    environment:
      - DATABASE_URL=postgresql://user:password@db:5432/myapp
      - REDIS_URL=redis://cache:6379
    depends_on:
      db:
        condition: service_healthy
      cache:
        condition: service_started
    restart: unless-stopped
    volumes:
      - ./logs:/app/logs

  db:
    image: postgres:15-alpine
    environment:
      - POSTGRES_DB=myapp
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U user -d myapp"]
      interval: 10s
      timeout: 5s
      retries: 5

  cache:
    image: redis:7-alpine
    ports:
      - "6379:6379"

volumes:
  postgres_data:
EOF

docker-compose up -d
docker-compose ps
docker-compose logs -f
docker-compose logs app --tail=20
docker-compose exec app bash          # Shell into running service
docker-compose down
docker-compose down -v                # Also remove volumes

# ── LAB 4: Intentional Breaking & Fixing ───────────────────────
# Break 1: Missing env variable
docker run myapp:v1                   # DATABASE_URL missing — app crashes
docker logs <id>                      # Read error → fix: add -e flag

# Break 2: Port conflict
docker run -p 5000:5000 myapp:v1
docker run -p 5000:5000 myapp:v1      # FAILS: port already in use
# Fix:
docker ps | grep 5000
docker stop <container_using_5000>

# Break 3: Container OOM
docker run --memory=10m myapp:v1      # Very low memory limit
docker stats                           # See it get killed
# Fix: increase --memory=256m

# Break 4: Entrypoint wrong
docker run myapp:v1 /bin/nonexistent  # No such file
docker logs <id>                       # Shows exact error
```

#### Learning Through Mistakes

|Mistake|Error|Troubleshooting|Fix|
|---|---|---|---|
|Container exits instantly|`Exited (1)` immediately|`docker logs <id>`|Read the error — usually missing env var or wrong CMD|
|Can't reach container|`Connection refused`|`docker ps` check port mapping|Verify `-p hostport:containerport`|
|Build fails|`COPY failed: file not found`|Check Dockerfile COPY paths|Ensure source file exists relative to build context|
|Volume permissions|`Permission denied` in container|`docker exec -it <c> ls -la /data`|Match user UID or `chmod` host dir|
|Image too large|Slow builds, high storage|`docker image ls`|Use Alpine base, multi-stage builds|

#### Real DevOps Support Scenarios

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCENARIO: "Container crashlooping in production"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
docker ps -a                                # Confirm Restarting status
docker logs myapp --tail=100                # First: read the error!
docker logs myapp --tail=100 2>&1 | grep -i "error\|fatal\|exception"
docker inspect myapp | grep -A5 "State"   # Exit code, OOM killed?

# Common causes and fixes:
# Exit Code 1 → App error → check logs for exception
# Exit Code 137 → OOM killed → increase memory limit
# Exit Code 139 → Segfault → app/dependency bug
# Exit Code 127 → Command not found → fix Dockerfile CMD

# If app starts but immediately fails:
docker run -it --entrypoint sh myapp:v1   # Override CMD, get shell
# Then manually run the app to see exact error
```

---

### ━━━ TOPIC 6: CI/CD Pipelines 🔴

**Days 17–19 | Priority: MUST LEARN**

#### 80/20 Concepts

- CI vs CD (Continuous Integration vs Delivery vs Deployment)
- Pipeline stages: Source → Build → Test → Package → Deploy → Verify
- GitHub Actions — syntax, triggers, jobs, steps, secrets
- Jenkins — installation, jobs, Jenkinsfile, plugins
- Pipeline-as-code (`Jenkinsfile`, `.github/workflows/*.yml`)
- Artifacts — what they are, storing them
- Rollback strategies — how to revert bad deployments
- Environment variables and secrets in pipelines

#### Theory

- **What:** CI/CD automates the process of testing and deploying code changes from developer commit to production
- **Why:** Manual deployments are error-prone and slow. CI/CD makes deployments consistent, fast, and reversible
- **Where:** Every software company — triggered on every git push
- **Common Interview Questions:**
    - "Pipeline failed at deploy stage. How do you debug it?"
    - "What is the difference between CI and CD?"
    - "How do you store secrets in a pipeline securely?"
    - "How do you rollback a bad deployment?"
    - "Explain a typical CI/CD pipeline from commit to production"

#### Practical Labs

```yaml
# ── LAB 1: GitHub Actions Pipeline ────────────────────────────
# File: .github/workflows/ci-cd.yml
name: CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

env:
  IMAGE_NAME: myapp
  REGISTRY: ghcr.io

jobs:
  lint-and-test:
    name: Test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.11'

      - name: Install dependencies
        run: |
          pip install -r requirements.txt
          pip install pytest flake8

      - name: Lint code
        run: flake8 . --max-line-length=100

      - name: Run tests
        run: pytest tests/ -v --tb=short

  build:
    name: Build & Push
    needs: lint-and-test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    outputs:
      image-tag: ${{ steps.meta.outputs.tags }}

    steps:
      - uses: actions/checkout@v4

      - name: Build Docker image
        run: docker build -t $IMAGE_NAME:${{ github.sha }} .

      - name: Run container health check
        run: |
          docker run -d -p 5000:5000 --name test-app \
            $IMAGE_NAME:${{ github.sha }}
          sleep 5
          curl -f http://localhost:5000/health || exit 1
          docker stop test-app

  deploy:
    name: Deploy to Production
    needs: build
    runs-on: ubuntu-latest
    environment: production

    steps:
      - uses: actions/checkout@v4

      - name: Deploy via SSH
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.SERVER_HOST }}
          username: ${{ secrets.SERVER_USER }}
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          script: |
            cd /app
            docker pull ${{ env.IMAGE_NAME }}:${{ github.sha }}
            docker-compose down
            IMAGE_TAG=${{ github.sha }} docker-compose up -d
            sleep 10
            curl -f http://localhost:5000/health || \
              (docker-compose down && docker-compose up -d && exit 1)

      - name: Notify on failure
        if: failure()
        run: |
          curl -X POST ${{ secrets.SLACK_WEBHOOK }} \
            -H 'Content-type: application/json' \
            -d '{"text":"❌ Deploy FAILED for commit ${{ github.sha }}"}'
```

```groovy
// ── LAB 2: Jenkinsfile ─────────────────────────────────────────
// File: Jenkinsfile
pipeline {
    agent any

    environment {
        IMAGE_NAME = 'myapp'
        DOCKER_REGISTRY = 'registry.company.com'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yourorg/myapp.git'
                sh 'git log --oneline -5'
            }
        }

        stage('Test') {
            steps {
                sh '''
                    pip install -r requirements.txt
                    pytest tests/ --junitxml=test-results.xml
                '''
            }
            post {
                always {
                    junit 'test-results.xml'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    def imageTag = "${env.IMAGE_NAME}:${env.BUILD_NUMBER}"
                    sh "docker build -t ${imageTag} ."
                    env.IMAGE_TAG = imageTag
                }
            }
        }

        stage('Deploy Staging') {
            steps {
                sh """
                    docker stop myapp-staging || true
                    docker rm myapp-staging || true
                    docker run -d --name myapp-staging \
                        -p 5001:5000 \
                        ${env.IMAGE_TAG}
                """
                sh 'sleep 5 && curl -f http://localhost:5001/health'
            }
        }

        stage('Deploy Production') {
            when { branch 'main' }
            input {
                message "Deploy to production?"
                ok "Deploy"
            }
            steps {
                sh './scripts/deploy-prod.sh ${env.IMAGE_TAG}'
            }
        }
    }

    post {
        failure {
            mail to: 'devops@company.com',
                 subject: "Pipeline FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Check: ${env.BUILD_URL}"
        }
        success {
            echo "✅ Pipeline succeeded!"
        }
    }
}
```

#### Real DevOps Support Scenarios

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCENARIO: "Deploy pipeline failed, prod is on old version"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Step 1: Open Jenkins/GitHub Actions → find failed build
Step 2: Identify failed stage — Build? Test? Deploy?
Step 3: Read the FULL console output of that stage
Step 4: Common failures:

  BUILD FAILS:
  → Missing dependency → check requirements.txt/package.json
  → Docker build error → check Dockerfile syntax
  → No space on CI server → df -h on Jenkins agent

  TEST FAILS:
  → Find failing test name
  → Read assertion error
  → Check if env variable missing (DB connection?)

  DEPLOY FAILS:
  → SSH connection refused → check server is running
  → Permission denied → check SSH key in secrets
  → Docker pull failed → check registry credentials
  → Health check failed → new version has a bug → ROLLBACK

Step 5: Rollback procedure:
  docker-compose down
  IMAGE_TAG=<last_known_good_sha> docker-compose up -d
  curl localhost/health  # Verify rollback worked
```

---

### ━━━ TOPIC 7: Monitoring & Observability 🔴

**Days 20–22 | Priority: MUST LEARN**

#### 80/20 Concepts

- The 3 Pillars: **Metrics** (numbers over time), **Logs** (events), **Traces** (request flow)
- The 4 Golden Signals: Latency, Traffic, Errors, Saturation
- **Prometheus** — pull-based metrics scraping
- **Grafana** — dashboards and alerting
- **Node Exporter** — Linux system metrics
- **ELK Stack** — Elasticsearch, Logstash, Kibana
- Alert routing — who gets notified, when, how
- SLI / SLO / SLA — what they mean
- On-call basics — incident severity, escalation

#### Theory

- **What:** Observability is the ability to understand what's happening inside your system from its external outputs (metrics, logs, traces)
- **Why:** You cannot fix what you cannot see. Monitoring catches problems before users do and helps diagnose incidents faster
- **Where:** Every production system — uptime monitoring, performance dashboards, alert firing to on-call engineers
- **Common Interview Questions:**
    - "What are the 4 Golden Signals?"
    - "Difference between monitoring and observability?"
    - "A Grafana alert fires at 3am for high CPU. Walk through your response."
    - "What is Prometheus and how does it collect metrics?"
    - "What is the difference between a metric, a log, and a trace?"

#### Practical Labs

```yaml
# ── LAB 1: Full Monitoring Stack with Docker Compose ──────────
cat > monitoring/docker-compose.yml << 'EOF'
version: '3.8'
services:
  prometheus:
    image: prom/prometheus:latest
    ports:
      - "9090:9090"
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
      - prometheus_data:/prometheus
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
      - '--storage.tsdb.retention.time=15d'

  grafana:
    image: grafana/grafana:latest
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_PASSWORD=admin123
      - GF_USERS_ALLOW_SIGN_UP=false
    volumes:
      - grafana_data:/var/lib/grafana
      - ./grafana/dashboards:/var/lib/grafana/dashboards

  node-exporter:
    image: prom/node-exporter:latest
    ports:
      - "9100:9100"
    volumes:
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /:/rootfs:ro
    command:
      - '--path.procfs=/host/proc'
      - '--path.sysfs=/host/sys'

  alertmanager:
    image: prom/alertmanager:latest
    ports:
      - "9093:9093"
    volumes:
      - ./alertmanager.yml:/etc/alertmanager/alertmanager.yml

volumes:
  prometheus_data:
  grafana_data:
EOF
```

```yaml
# ── LAB 2: Prometheus Configuration ───────────────────────────
# monitoring/prometheus.yml
global:
  scrape_interval: 15s
  evaluation_interval: 15s

rule_files:
  - "alerts.yml"

alerting:
  alertmanagers:
    - static_configs:
        - targets: ['alertmanager:9093']

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node-exporter'
    static_configs:
      - targets: ['node-exporter:9100']

  - job_name: 'myapp'
    static_configs:
      - targets: ['app:5000']
    metrics_path: '/metrics'
```

```yaml
# ── LAB 3: Alert Rules ─────────────────────────────────────────
# monitoring/alerts.yml
groups:
  - name: infrastructure
    rules:
      - alert: HighCPUUsage
        expr: 100 - (avg by(instance)(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100) > 85
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "High CPU on {{ $labels.instance }}"
          description: "CPU usage is {{ $value }}%"

      - alert: DiskSpaceLow
        expr: (node_filesystem_avail_bytes / node_filesystem_size_bytes) * 100 < 15
        for: 1m
        labels:
          severity: critical
        annotations:
          summary: "Low disk space on {{ $labels.instance }}"
          description: "Only {{ $value }}% disk space remaining"

      - alert: ServiceDown
        expr: up == 0
        for: 1m
        labels:
          severity: critical
        annotations:
          summary: "Service {{ $labels.job }} is DOWN"

      - alert: HighMemoryUsage
        expr: (1 - (node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes)) * 100 > 90
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "High memory usage: {{ $value }}%"
```

```yaml
# ── LAB 4: Alertmanager → Slack ────────────────────────────────
# monitoring/alertmanager.yml
global:
  slack_api_url: 'https://hooks.slack.com/services/YOUR/WEBHOOK/URL'

route:
  group_by: ['alertname', 'instance']
  group_wait: 10s
  group_interval: 10m
  repeat_interval: 1h
  receiver: 'slack-alerts'
  routes:
    - match:
        severity: critical
      receiver: 'slack-critical'

receivers:
  - name: 'slack-alerts'
    slack_configs:
      - channel: '#devops-alerts'
        title: '{{ .GroupLabels.alertname }}'
        text: '{{ range .Alerts }}{{ .Annotations.description }}{{ end }}'

  - name: 'slack-critical'
    slack_configs:
      - channel: '#devops-critical'
        title: '🚨 CRITICAL: {{ .GroupLabels.alertname }}'
```

```bash
# ── LAB 5: Useful Prometheus Queries (PromQL) ──────────────────
# CPU usage % per instance
100 - (avg by(instance)(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)

# Memory usage %
(1 - (node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes)) * 100

# Disk usage %
100 - ((node_filesystem_avail_bytes / node_filesystem_size_bytes) * 100)

# HTTP requests per second
rate(http_requests_total[5m])

# Error rate %
rate(http_requests_total{status=~"5.."}[5m]) / rate(http_requests_total[5m]) * 100

# Services that are DOWN
up == 0
```

---

### ━━━ TOPIC 8: Cloud Platforms (AWS) 🟡

**Days 23–24 | Priority: GOOD TO LEARN**

#### 80/20 Concepts

- **EC2** — virtual machines, instance types, SSH access, security groups
- **S3** — object storage, buckets, permissions, lifecycle rules
- **IAM** — users, roles, policies, least privilege
- **VPC** — subnets, security groups, NACLs, Internet Gateway
- **RDS** — managed databases, backups, connection
- **CloudWatch** — logs, metrics, alarms
- **AWS CLI** — essential commands for support work

#### Practical Labs

```bash
# ── LAB 1: AWS CLI Setup ───────────────────────────────────────
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o aws.zip
unzip aws.zip && sudo ./aws/install
aws configure
# Enter: Access Key ID, Secret Key, Region (ap-south-1), Output (json)

# ── LAB 2: EC2 Operations ─────────────────────────────────────
# List instances
aws ec2 describe-instances \
  --query 'Reservations[].Instances[].[InstanceId,State.Name,PublicIpAddress,Tags[?Key==`Name`].Value|[0]]' \
  --output table

# Start/stop instance
aws ec2 start-instances --instance-ids i-1234567890abcdef0
aws ec2 stop-instances --instance-ids i-1234567890abcdef0

# Get instance public IP
aws ec2 describe-instances --instance-ids i-xxx \
  --query 'Reservations[0].Instances[0].PublicIpAddress' --output text

# SSH into EC2
ssh -i ~/.ssh/mykey.pem ubuntu@$(aws ec2 describe-instances \
  --instance-ids i-xxx \
  --query 'Reservations[0].Instances[0].PublicIpAddress' \
  --output text)

# ── LAB 3: S3 Operations ──────────────────────────────────────
aws s3 mb s3://my-devops-bucket-$(date +%s)  # Create bucket
aws s3 ls                                     # List buckets
aws s3 ls s3://my-bucket/ --recursive         # List contents
aws s3 cp myfile.txt s3://my-bucket/          # Upload
aws s3 sync /local/dir s3://my-bucket/backup/ # Sync directory
aws s3 rm s3://my-bucket/oldfile.txt          # Delete

# ── LAB 4: CloudWatch Logs ────────────────────────────────────
aws logs describe-log-groups
aws logs tail /aws/ec2/myapp --follow
aws logs filter-log-events \
  --log-group-name /var/log/nginx \
  --filter-pattern "ERROR" \
  --start-time $(date -d "1 hour ago" +%s)000

# ── LAB 5: IAM Troubleshooting ────────────────────────────────
# Check your current identity
aws sts get-caller-identity

# List policies attached to a role
aws iam list-attached-role-policies --role-name my-ec2-role

# Simulate IAM permission check
aws iam simulate-principal-policy \
  --policy-source-arn arn:aws:iam::123456789:user/myuser \
  --action-names s3:GetObject \
  --resource-arns arn:aws:s3:::my-bucket/*
```

---

### ━━━ TOPIC 9: IaC (Terraform) 🟡

**Day 25 | Priority: GOOD TO LEARN**

#### 80/20 Concepts

- `terraform init` → `plan` → `apply` → `destroy`
- Resources, variables, outputs, data sources
- State file — what it is, why it matters
- Remote state (S3 backend)
- Modules — basic understanding
- Import existing resources

#### Practical Labs

```hcl
# ── LAB 1: Basic EC2 with Terraform ───────────────────────────
# main.tf
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
  # Remote state (uncomment when you have S3 bucket)
  # backend "s3" {
  #   bucket = "my-terraform-state"
  #   key    = "prod/terraform.tfstate"
  #   region = "ap-south-1"
  # }
}

provider "aws" {
  region = var.aws_region
}

# Variables
variable "aws_region" {
  default = "ap-south-1"
}

variable "instance_type" {
  default = "t2.micro"
}

variable "environment" {
  default = "dev"
}

# Data source — get latest Ubuntu AMI
data "aws_ami" "ubuntu" {
  most_recent = true
  owners      = ["099720109477"]  # Canonical
  filter {
    name   = "name"
    values = ["ubuntu/images/hvm-ssd/ubuntu-*-22.04-amd64-server-*"]
  }
}

# Security Group
resource "aws_security_group" "web" {
  name        = "${var.environment}-web-sg"
  description = "Web server security group"

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

# EC2 Instance
resource "aws_instance" "web" {
  ami                    = data.aws_ami.ubuntu.id
  instance_type          = var.instance_type
  vpc_security_group_ids = [aws_security_group.web.id]

  user_data = <<-EOF
    #!/bin/bash
    apt-get update
    apt-get install -y nginx
    systemctl enable nginx
    systemctl start nginx
    echo "Deployed by Terraform at $(date)" > /var/www/html/index.html
  EOF

  tags = {
    Name        = "${var.environment}-web-server"
    Environment = var.environment
    ManagedBy   = "Terraform"
  }
}

# Outputs
output "server_public_ip" {
  value = aws_instance.web.public_ip
}

output "ssh_command" {
  value = "ssh ubuntu@${aws_instance.web.public_ip}"
}
```

```bash
# Terraform workflow
terraform init          # Download providers
terraform validate      # Check syntax
terraform fmt           # Format code
terraform plan          # Preview changes (ALWAYS review!)
terraform apply         # Apply changes
terraform output        # Show outputs
terraform show          # Show current state
terraform destroy       # Remove all resources (careful!)

# Common support tasks
terraform state list    # List all managed resources
terraform state show aws_instance.web  # Show resource details
terraform import aws_instance.web i-1234567890abcdef0  # Import existing
```

---

### ━━━ TOPIC 10: Kubernetes 🟡

**Day 26 | Priority: GOOD TO LEARN (Basics Only)**

#### 80/20 Concepts (Support Engineer Level)

- **Pod** — smallest unit, runs containers
- **Deployment** — manages pod replicas, rolling updates
- **Service** — exposes pods on network (ClusterIP, NodePort, LoadBalancer)
- **Namespace** — logical isolation
- **ConfigMap & Secret** — configuration and secrets
- `kubectl` essential commands for debugging
- Reading pod logs, events, and descriptions

#### Practical Labs

```bash
# ── LAB 1: Setup with minikube (local K8s) ────────────────────
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
kubectl get nodes

# ── LAB 2: Deploy an Application ──────────────────────────────
# deployment.yml
cat > deployment.yml << 'EOF'
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
  namespace: default
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
        - name: myapp
          image: nginx:latest
          ports:
            - containerPort: 80
          resources:
            requests:
              memory: "64Mi"
              cpu: "100m"
            limits:
              memory: "128Mi"
              cpu: "200m"
          readinessProbe:
            httpGet:
              path: /
              port: 80
            initialDelaySeconds: 5
            periodSeconds: 10
---
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  selector:
    app: myapp
  ports:
    - port: 80
      targetPort: 80
  type: NodePort
EOF

kubectl apply -f deployment.yml

# ── LAB 3: Essential kubectl Debug Commands ────────────────────
kubectl get pods                              # List pods
kubectl get pods -A                           # All namespaces
kubectl get pods -o wide                      # With node and IP
kubectl describe pod myapp-xxx-yyy            # Detailed info + events
kubectl logs myapp-xxx-yyy                    # Pod logs
kubectl logs myapp-xxx-yyy --previous         # Previous crashed pod
kubectl logs -f myapp-xxx-yyy                 # Follow live
kubectl exec -it myapp-xxx-yyy -- bash        # Shell into pod
kubectl get events --sort-by='.lastTimestamp' # Cluster events
kubectl top pods                              # Resource usage
kubectl top nodes

# ── LAB 4: Rollout & Rollback ─────────────────────────────────
kubectl set image deployment/myapp myapp=nginx:1.25  # Update
kubectl rollout status deployment/myapp              # Watch rollout
kubectl rollout history deployment/myapp             # See history
kubectl rollout undo deployment/myapp                # Rollback!
kubectl rollout undo deployment/myapp --to-revision=2
```

#### Real DevOps Support Scenarios

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SCENARIO: "Pod in CrashLoopBackOff"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
kubectl get pods                        # Confirm CrashLoopBackOff
kubectl describe pod <pod-name>         # Check Events section
kubectl logs <pod-name>                 # Current crash logs
kubectl logs <pod-name> --previous      # Previous crash logs

Common causes:
1. App error → fix code, push new image
2. Missing ConfigMap/Secret → kubectl get configmap,secret
3. OOMKilled → increase memory limit in deployment
4. Liveness probe failing → check probe path/port
5. Wrong image → kubectl set image deployment/...
```

---

### ━━━ TOPIC 11: Security (DevSecOps) 🟡

**Day 27 | Priority: GOOD TO LEARN**

#### 80/20 Concepts

- Never hardcode secrets (use env vars, Vault, AWS Secrets Manager)
- Principle of least privilege (IAM, Linux users, Docker)
- SSH hardening — key-only auth, disable root, change default port
- SSL/TLS — certificate management, Let's Encrypt
- `ufw`/`iptables` — firewall basics
- Container security — non-root user, read-only filesystem
- Secret scanning — git-secrets, truffleHog
- OWASP Top 10 — awareness level

#### Practical Labs

```bash
# ── LAB 1: SSH Hardening ───────────────────────────────────────
# Edit: /etc/ssh/sshd_config
sudo vim /etc/ssh/sshd_config

# Change these settings:
# PermitRootLogin no
# PasswordAuthentication no
# PubkeyAuthentication yes
# Port 2222            # Non-default port
# MaxAuthTries 3
# ClientAliveInterval 300

sudo systemctl restart sshd
# TEST: open new terminal, verify you can still login before closing old one!

# ── LAB 2: UFW Firewall ────────────────────────────────────────
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 2222/tcp          # SSH (new port)
sudo ufw allow 80/tcp            # HTTP
sudo ufw allow 443/tcp           # HTTPS
sudo ufw enable
sudo ufw status numbered

# ── LAB 3: Secret Scanning ────────────────────────────────────
# Install truffleHog
pip install trufflehog

# Scan a git repo for secrets
trufflehog git https://github.com/yourorg/yourrepo

# Install git-secrets to prevent committing secrets
git clone https://github.com/awslabs/git-secrets.git
cd git-secrets && make install
git secrets --install            # Install hooks in repo
git secrets --register-aws       # Add AWS patterns

# ── LAB 4: SSL with Let's Encrypt ─────────────────────────────
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
sudo certbot renew --dry-run

# Check cert expiry
openssl x509 -in /etc/letsencrypt/live/yourdomain.com/cert.pem \
  -noout -dates

# ── LAB 5: Find Hardcoded Secrets in Files ─────────────────────
# Search for potential secrets
grep -rn "password\s*=\s*" ./src --include="*.py"
grep -rn "api_key\s*=\s*" ./src --include="*.js"
grep -rn "secret\s*=\s*" ./config --include="*.yml"
grep -rn "AWS_SECRET" . --include="*.env"
```

---

## 📅 SECTION 3: COMPLETE 30-DAY STUDY PLAN

### ⏱️ Daily Time Budget

```
┌─────────────────────────────────────────┐
│  DAILY SCHEDULE (3.5 Hours)             │
│                                         │
│  Theory        │ 1.0 hr  │ 30%         │
│  Hands-on Labs │ 2.0 hrs │ 57%         │
│  Break & Fix   │ 0.5 hr  │ 13%         │
└─────────────────────────────────────────┘
```

---

### 🐧 WEEK 1: Linux Foundation (Days 1–7)

**Day 1 — Linux Filesystem & Navigation**

- Theory: Filesystem hierarchy, what lives where, why
- Practical: Navigate the full system, use `find`, `locate`, `tree`, read man pages
- Troubleshooting: Delete a test file, try to recover it, understand why you can't
- Expected Outcome: Comfortable moving around any Linux system confidently

**Day 2 — File Permissions & Users**

- Theory: rwx model, numeric vs symbolic, `sudo`, `sudoers`
- Practical: Create 3 users, set different permissions, test access denial
- Troubleshooting: Intentionally create "Permission denied" — diagnose and fix
- Expected Outcome: Understand and fix any Linux permission issue

**Day 3 — Process & Service Management**

- Theory: Process states, `systemctl`, PID, signals
- Practical: Start/stop/restart nginx, track processes, use `kill` and `nice`
- Troubleshooting: Stop nginx → see 502 error → restart → verify recovery
- Expected Outcome: Manage Linux services confidently

**Day 4 — Disk, Memory & Cron**

- Theory: Filesystem types, `df` vs `du`, cron timing syntax
- Practical: Fill /tmp artificially, investigate with `du`, clean it, set up 3 cron jobs
- Troubleshooting: Create failing cron, debug via syslog, fix PATH issue
- Expected Outcome: Handle disk full incidents and automate scheduled tasks

**Day 5 — Log Analysis & Text Processing**

- Theory: Log levels, log rotation, syslog, journald
- Practical: Generate nginx traffic/errors, analyze logs with `grep/awk/sed`
- Troubleshooting: Find root cause of a 500 error using only log files
- Expected Outcome: Diagnose any issue from logs alone

**Day 6 — SSH & Remote Access**

- Theory: How SSH works, key-based auth, `known_hosts`, `config` file
- Practical: Generate SSH key pair, configure `~/.ssh/config`, use `scp`, `rsync`
- Troubleshooting: Break SSH auth (wrong permissions) → fix `chmod 600 ~/.ssh/id_rsa`
- Expected Outcome: Set up and troubleshoot SSH access reliably

**Day 7 — Week 1 Review & Mini Project**

- Revision: All Linux commands from Days 1–6
- Mini Project: Complete System Health Report script
    
    ```bash
    #!/bin/bash# Outputs: uptime, disk, memory, CPU load, failed services, last logins, top processes
    ```
    
- Mock Troubleshooting: "Production server is slow and a service is down" — diagnose with only Linux tools
- Expected Outcome: Can handle any basic Linux support incident independently

---

### 🔧 WEEK 2: Scripting, Networking & Git (Days 8–14)

**Day 8 — Bash Scripting Basics**

- Theory: Variables, quoting, arguments, conditionals
- Practical: Write 5 small scripts (file checker, user validator, greeter, arg parser, error handler)
- Troubleshooting: Script works in terminal but fails in cron — find and fix
- Expected Outcome: Write reliable bash scripts from scratch

**Day 9 — Bash Scripting Advanced**

- Theory: Loops, functions, exit codes, `set -e`, `trap`, error handling
- Practical: Build the complete health_check.sh and backup.sh from Topic 2
- Troubleshooting: Script with missing error handling — add it, see difference
- Expected Outcome: Write production-grade automation scripts

**Day 10 — Networking Fundamentals**

- Theory: OSI layers, IP/CIDR, TCP/UDP, DNS resolution flow
- Practical: Use `dig`, `traceroute`, `nc`, `ss` to analyze connectivity
- Troubleshooting: Break local DNS (`/etc/resolv.conf`), diagnose, fix
- Expected Outcome: Trace and diagnose any network path

**Day 11 — HTTP, SSL & Firewalls**

- Theory: HTTP methods, status codes, TLS handshake, certificate chain
- Practical: Debug with `curl -v`, inspect SSL cert, set up UFW rules
- Troubleshooting: UFW blocks port 80 → investigate → fix → verify
- Expected Outcome: Diagnose SSL, HTTP, and firewall issues

**Day 12 — Git Fundamentals**

- Theory: Git internals, branching model, distributed workflow
- Practical: Create repo, practice full git flow: branch → commit → PR → merge
- Troubleshooting: Create a merge conflict → resolve it correctly
- Expected Outcome: Use Git confidently in team workflows

**Day 13 — Git Advanced + DevOps Use Cases**

- Theory: Revert vs reset, git bisect, tags, release workflow
- Practical: Rollback a bad commit, use `git bisect` to find bug commit, tag a release
- Troubleshooting: Accidental commit to main, undo safely without losing work
- Expected Outcome: Handle Git emergencies (rollback, conflict, wrong branch)

**Day 14 — Week 2 Review & Mini Project**

- Revision: Scripting + Networking + Git
- Mini Project: Write a `server_setup.sh` script that installs nginx, configures UFW, creates a deploy user, and sets up SSH key auth
- Mock Troubleshooting: "Website unreachable — could be DNS, firewall, or service" — diagnose systematically
- Expected Outcome: Automate server configuration from scratch

---

### 🐳 WEEK 3: Docker & CI/CD (Days 15–21)

**Day 15 — Docker Basics**

- Theory: Images vs containers, layers, registry, Docker Hub
- Practical: Pull images, run containers, use exec, manage lifecycle
- Troubleshooting: Container exits immediately — debug via logs
- Expected Outcome: Basic Docker operations without looking up docs

**Day 16 — Dockerfile & Docker Compose**

- Theory: Dockerfile best practices, layer caching, multi-stage builds
- Practical: Write Dockerfile for Flask app, build it, run it, compose with Postgres
- Troubleshooting: Build fails, DB connection refused — fix both
- Expected Outcome: Containerize any application

**Day 17 — Docker Debugging Deep Dive**

- Theory: Container networking, volumes, resource limits
- Practical: Simulate all common Docker failures from Topic 5 labs
- Troubleshooting: Memory limit causing OOM kill — detect, increase, verify
- Expected Outcome: Debug any container issue in production

**Day 18 — CI/CD Concepts & GitHub Actions**

- Theory: CI/CD stages, why pipelines exist, artifact management
- Practical: Create GitHub repo, write full GitHub Actions pipeline
- Troubleshooting: Pipeline YAML syntax error — read error, fix indentation
- Expected Outcome: Working CI/CD pipeline on GitHub

**Day 19 — Jenkins**

- Theory: Jenkins architecture, job types, plugins, credentials
- Practical: Run Jenkins in Docker, create job, write Jenkinsfile
- Troubleshooting: Jenkins plugin conflict, agent offline — fix both
- Expected Outcome: Create and debug Jenkins pipelines

**Day 20 — Monitoring Stack Setup**

- Theory: 3 pillars, 4 golden signals, SLI/SLO/SLA
- Practical: Deploy Prometheus + Grafana + Node Exporter with Docker Compose
- Troubleshooting: Prometheus can't scrape target — fix scrape config
- Expected Outcome: Full monitoring stack running locally

**Day 21 — Week 3 Review & Mini Project**

- Revision: Docker + CI/CD + Monitoring basics
- Mini Project: Complete pipeline — GitHub push triggers build → Docker image built → Deployed → Health check runs → Slack notified on failure
- Mock Troubleshooting: "Staging deploy pipeline broke, urgent PR needs to go to prod"
- Expected Outcome: Can maintain and fix a CI/CD pipeline end-to-end

---

### ☁️ WEEK 4: Monitoring + Cloud + Interview Prep (Days 22–30)

**Day 22 — Grafana Dashboards & Alerting**

- Theory: Dashboard design, PromQL queries, alert routing
- Practical: Build CPU/Memory/Disk/Error Rate dashboard, configure Slack alerts
- Troubleshooting: Alert not firing — debug threshold, label matchers, routing
- Expected Outcome: Build and configure production-grade dashboards

**Day 23 — AWS Core Services**

- Theory: EC2, S3, IAM, VPC, security groups
- Practical: Launch EC2, configure security group, SSH in, install app
- Troubleshooting: Can't SSH → wrong security group → fix inbound rule
- Expected Outcome: Provision and access cloud resources

**Day 24 — AWS CloudWatch & CLI**

- Theory: CloudWatch logs, metrics, alarms, AWS CLI
- Practical: Set up CloudWatch alarm for CPU, tail logs with CLI
- Troubleshooting: Access denied on S3 → fix IAM policy → verify with simulator
- Expected Outcome: Monitor and operate AWS resources via CLI

**Day 25 — Terraform**

- Theory: IaC benefits, state management, plan/apply/destroy
- Practical: Provision EC2 + security group with Terraform
- Troubleshooting: State conflict after manual change → `terraform refresh` to fix
- Expected Outcome: Use Terraform to provision basic infrastructure

**Day 26 — Kubernetes Basics**

- Theory: K8s architecture, Pod/Deployment/Service, control plane
- Practical: Deploy app to minikube, scale it, perform rolling update + rollback
- Troubleshooting: CrashLoopBackOff — read events and logs, fix
- Expected Outcome: Debug Kubernetes issues at support engineer level

**Day 27 — Security & DevSecOps**

- Theory: Secrets management, least privilege, SSH hardening, OWASP Top 10
- Practical: Harden server (SSH config, UFW, non-root users, cert setup)
- Troubleshooting: Locked yourself out of SSH → recover via console
- Expected Outcome: Apply basic security hardening to any server

**Day 28 — Final Project (Part 1)**

- Build infrastructure: EC2 (or VM), Docker Compose app stack
- Set up monitoring stack (Prometheus + Grafana)
- Configure CI/CD pipeline (GitHub Actions)
- Expected Outcome: Core infrastructure and deployment working

**Day 29 — Final Project (Part 2)**

- Add health check scripts (cron scheduled)
- Add backup automation
- Add alerting (Slack notifications)
- Write complete `README.md` documenting everything
- Push all code to GitHub
- Expected Outcome: Complete portfolio project documented and live

**Day 30 — Interview Preparation**

- Morning: 25 rapid-fire Q&A (speak answers aloud)
- Afternoon: 5 full scenario walkthroughs
- Evening: Resume review, LinkedIn update, job application checklist
- Expected Outcome: Job-ready, confident, portfolio live

---

## 🏗️ SECTION 4: FINAL JOB READINESS PROJECT

### "Full-Stack DevOps Lab Environment"

#### Complete Architecture

```
┌─────────────────────────────────────────────────────────┐
│                   DEVELOPER'S MACHINE                    │
│    git push → GitHub → GitHub Actions Pipeline          │
└─────────────────────┬───────────────────────────────────┘
                      │ SSH Deploy
                      ▼
┌─────────────────────────────────────────────────────────┐
│                   PRODUCTION SERVER                      │
│                                                         │
│  ┌─────────────────────────────────────────────────┐   │
│  │           Docker Compose Stack                   │   │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────────┐  │   │
│  │  │  nginx   │  │  myapp   │  │  postgres    │  │   │
│  │  │ (proxy)  │  │ (flask)  │  │  (database)  │  │   │
│  │  └──────────┘  └──────────┘  └──────────────┘  │   │
│  └─────────────────────────────────────────────────┘   │
│                                                         │
│  ┌─────────────────────────────────────────────────┐   │
│  │           Monitoring Stack                       │   │
│  │  ┌──────────────┐  ┌────────────┐  ┌────────┐  │   │
│  │  │  Prometheus  │  │  Grafana   │  │ Alert  │  │   │
│  │  │  :9090       │  │  :3000     │  │ Manager│  │   │
│  │  └──────────────┘  └────────────┘  └────────┘  │   │
│  └─────────────────────────────────────────────────┘   │
│                                                         │
│  ┌─────────────────────────────────────────────────┐   │
│  │           Automation (Cron)                      │   │
│  │  health_check.sh   (every 5 min)                │   │
│  │  backup.sh         (daily 2am)                  │   │
│  │  disk_alert.sh     (every hour)                 │   │
│  │  log_cleaner.sh    (weekly)                     │   │
│  └─────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
                      │ Alerts
                      ▼
              Slack #devops-alerts
```

#### Project File Structure (Push to GitHub)

```
devops-lab/
├── README.md                    # Full documentation
├── Dockerfile                   # App container
├── docker-compose.yml           # App stack
├── docker-compose.monitoring.yml # Monitoring stack
├── .github/
│   └── workflows/
│       └── deploy.yml           # CI/CD pipeline
├── monitoring/
│   ├── prometheus.yml           # Scrape config
│   ├── alerts.yml               # Alert rules
│   └── alertmanager.yml         # Alert routing
├── scripts/
│   ├── health_check.sh          # Service monitoring
│   ├── backup.sh                # Backup automation
│   ├── disk_alert.sh            # Disk monitoring
│   └── deploy.sh                # Deployment script
├── terraform/
│   ├── main.tf                  # AWS infrastructure
│   ├── variables.tf
│   └── outputs.tf
└── nginx/
    └── nginx.conf               # Reverse proxy config
```

---

## 🎯 SECTION 5: INTERVIEW PREPARATION

### Master Question Bank by Topic

#### Linux

|Question Type|Question|Key Answer Points|
|---|---|---|
|Practical|"Disk is 100% full, app is down. Steps?"|`df -h` → `du -sh /* \| sort -rh` → find large files → delete safely → verify service recovers|
|Practical|"Can't SSH into server. Debug steps?"|Ping → port check → security group → SSH service → key permissions → logs|
|Conceptual|"What is zombie process?"|Finished but not reaped by parent. `ps aux \| grep Z`. Fix: restart parent or reboot|
|Conceptual|"Explain `2>&1` in a command"|Redirects stderr (fd 2) to wherever stdout (fd 1) is going. Both streams combined|
|Scenario|"App is slow, CPU at 95%"|`top` → identify process → `strace -p PID` → check logs → notify dev team|

#### Docker

|Question Type|Question|Key Answer Points|
|---|---|---|
|Practical|"Container in restart loop. Debug?"|`docker ps -a` → `docker logs` → `docker inspect` → fix cause → rebuild|
|Conceptual|"CMD vs ENTRYPOINT difference?"|ENTRYPOINT = fixed executable. CMD = default arguments (overridable). Together: ENTRYPOINT ["python"], CMD ["app.py"]|
|Scenario|"Docker build succeeds but app crashes at runtime"|Runtime env vars missing, wrong port, DB unreachable. Check docker logs|
|Practical|"How to pass secrets to container?"|`-e VAR=value`, `--env-file .env`, Docker Secrets (Swarm), or fetch from Vault/AWS SSM at startup|

#### CI/CD

|Question Type|Question|Key Answer Points|
|---|---|---|
|Conceptual|"CI vs CD vs CD?"|CI=auto test on every commit. Continuous Delivery=auto to staging. Continuous Deployment=auto to prod|
|Scenario|"Pipeline passed but prod is broken"|Tests didn't cover the bug. Add integration/smoke tests. Implement blue-green or canary deployments|
|Practical|"How do you store secrets in GitHub Actions?"|Repository Settings → Secrets → use `${{ secrets.MY_SECRET }}` in workflow YAML|
|Scenario|"How do you rollback a bad production deploy?"|Run rollback pipeline with previous image tag OR `kubectl rollout undo` OR `git revert` + redeploy|

#### Networking

|Question Type|Question|Key Answer Points|
|---|---|---|
|Scenario|"User says website slow from India but fast from US"|CDN issue, routing, DNS TTL, origin latency. Use `mtr` from both locations|
|Conceptual|"What happens when you type google.com?"|DNS lookup → TCP connection → TLS handshake → HTTP GET → response rendered|
|Practical|"SSL cert expired in prod. Fix?"|`certbot renew` → `nginx -t` → `systemctl reload nginx` → verify with `openssl s_client`|
|Practical|"Port 5432 not reachable from app server"|`nc -zv db-server 5432` → check DB listening (`ss -tlnp`) → check firewall → check security group|

#### Monitoring

|Question Type|Question|Key Answer Points|
|---|---|---|
|Conceptual|"4 Golden Signals?"|Latency (response time), Traffic (requests/sec), Errors (error rate %), Saturation (resource usage %)|
|Scenario|"Alert fires at 3am: high memory. Steps?"|Acknowledge → check Grafana → `top`/`free` on server → identify process → OOM kill check → dmesg → resolve or escalate|
|Conceptual|"Difference: metric vs log vs trace?"|Metric=number over time. Log=text event. Trace=request path through multiple services|
|Practical|"App slow but no alerts firing. Why?"|Wrong alert thresholds, wrong metric, alert rule broken. Add latency-based alert (p99 response time)|

### Complete Scenario Interview Answers

**"Walk me through your troubleshooting process when you receive an alert that a service is down"**

```
1. ACKNOWLEDGE — Note the time, alert details, and affected service
2. ASSESS — Is it truly down? (false alert?) Check monitoring dashboard
3. COMMUNICATE — Post in #incidents: "Investigating alert for [service] at [time]"
4. INVESTIGATE:
   → SSH to server
   → systemctl status <service>
   → journalctl -u <service> -n 100
   → Check dependencies (DB, cache, upstream services)
   → df -h (disk full?), free -h (OOM?), top (CPU spike?)
5. REMEDIATE:
   → Restart service if safe
   → Rollback if recent deployment caused it
   → Increase resources if resource exhaustion
6. VERIFY — Test the service, check monitoring returns to green
7. COMMUNICATE — "Service restored at [time], root cause: [X]"
8. DOCUMENT — Write incident report with timeline and action items
```

---

## ✅ SECTION 6: JOB READINESS CHECKLIST

### Technical Skills Verified

```
LINUX
□ Navigate and manage files without looking up commands
□ Diagnose and fix permission issues
□ Read and parse log files to find root cause
□ Manage services with systemctl
□ Write cron jobs
□ Debug disk, memory, CPU issues

SCRIPTING
□ Write a service health check script from memory
□ Add proper error handling to scripts
□ Debug a failing cron job
□ Write a backup script with retention

NETWORKING
□ Trace DNS resolution with dig
□ Check port connectivity with nc/ss
□ Debug SSL certificate issues with openssl
□ Manage UFW firewall rules

GIT
□ Full git workflow (branch, commit, PR, merge)
□ Resolve merge conflicts
□ Rollback a bad commit safely
□ Set up git-secrets hooks

DOCKER
□ Build and run containers from scratch
□ Debug crashlooping containers
□ Write docker-compose for multi-service apps
□ Debug OOM killed containers

CI/CD
□ Write a GitHub Actions pipeline
□ Debug a failed pipeline stage
□ Set up pipeline secrets correctly
□ Execute a deployment rollback

MONITORING
□ Query Prometheus with PromQL
□ Build a Grafana dashboard
□ Configure alert rules and routing
□ Respond to an alert correctly

CLOUD & IaC
□ Launch and SSH into EC2
□ Manage S3 with CLI
□ Run terraform plan/apply/destroy
□ Debug IAM permission issues

KUBERNETES
□ Debug CrashLoopBackOff pods
□ Read pod logs and events
□ Execute a rollback with kubectl

SECURITY
□ Harden SSH configuration
□ Manage UFW firewall
□ Handle secrets properly (never hardcode)
□ Set up SSL certificate with certbot
```

### Portfolio Checklist

```
□ GitHub profile with all scripts and configs
□ Final project with complete README
□ Documented troubleshooting runbooks
□ LinkedIn: DevOps Support Engineer title
□ Resume: Updated with tools and projects
□ Can demo the project in an interview
```

---

**You now have a complete, structured, 30-day path from zero to job-ready DevOps Support Engineer. Follow the daily plan strictly, break things deliberately, and fix them — that's how real DevOps skills are built. Good luck! 💪**