

# 🐧 Linux 5-Day Learning Plan (80/20 Focus)

> 🎯 **Goal:** Learn the most important 20% of Linux concepts and commands that give 80% of the practical power used in real-world environments.
> ⏰ **Duration:** 5 Days  
> 💪 **Focus:** Hands-on learning → Reflection → Real-world application

---

## ⚙️ 80/20 Core Strategy
Focus only on:
- Top 50 most-used commands  
- Daily Linux operations (navigation, file management, processes, networking, automation)  
- Understanding how Linux works — not memorizing every command

---

## 🗓️ 5-Day Learning Plan

---

### ✅ **[[Day 1 – Foundation & Navigation]]**
**Goal:** Understand what Linux is and how to move around confidently.

**Topics**
- [x] What is Linux and its architecture  
- [x] Linux distributions (Ubuntu, CentOS, Debian)  
- [x] Filesystem hierarchy (`/home`, `/etc`, `/var`, `/bin`)  
- [x] Navigation commands: `pwd`, `ls`, `cd`, `cat`, `less`, `head`, `tail`

**🧩 Activity:**  

Explore your system with:
```bash
pwd
ls -l
cd /etc
ls -a
````

Note how permissions look (`drwxr-xr-x`).

💭 **Reflection:**  
What surprised you about Linux file structure?  
How does it differ from Windows or macOS?

🎯 **XP Earned:** +10 (Navigation Basics)

---

### ✅ **Day 2 – File Management & Permissions**

**Goal:** Learn to manage files and control access like a power user.

**Topics**

-  File operations: `cp`, `mv`, `rm`, `mkdir`, `touch`
    
-  Wildcards (`*`, `?`)
    
-  File permissions: `chmod`, `chown`, `chgrp`
    
-  Viewing hidden files (`ls -a`)
    

**🧩 Activity:**

```bash
mkdir practice
cd practice
touch file1.txt
cp file1.txt file2.txt
chmod 755 file2.txt
ls -l
```

💭 **Reflection:**  
What happens when you use `chmod 777`? Why is it risky?

🎯 **XP Earned:** +15 (File Mastery)

---

### ✅ **Day 3 – Process & System Monitoring**

**Goal:** Understand how Linux runs programs and how to control them.

**Topics**

-  View processes: `ps`, `top`, `htop`
    
-  Manage processes: `kill`, `nice`, `bg`, `fg`
    
-  System info: `df`, `du`, `free`, `uptime`, `uname`, `dmesg`
    

**🧩 Activity:**  
Open multiple terminals:

```bash
top
ps aux | grep firefox
kill <PID>
```

💭 **Reflection:**  
How does Linux manage multiple processes simultaneously?

🎯 **XP Earned:** +20 (Process Guru)

---

### ✅ **Day 4 – Networking, Packages & Users**

**Goal:** Learn networking basics and user management.

**Topics**

-  Network tools: `ping`, `curl`, `wget`, `netstat`
    
-  Package managers: `apt`, `yum`, `dnf`
    
-  User management: `useradd`, `passwd`, `sudo`, `su`
    

**🧩 Activity:**

```bash
sudo apt update
sudo apt install tree
ping google.com
sudo useradd testuser
sudo passwd testuser
```

💭 **Reflection:**  
What’s the purpose of the `sudo` command?  
Why is it safer than using the root account directly?

🎯 **XP Earned:** +25 (Sysadmin Pro)

---

### ✅ **Day 5 – Shell Scripting & Automation**

**Goal:** Use scripting to automate repetitive tasks.

**Topics**

-  Writing shell scripts (`.sh` files)
    
-  Variables, loops, and conditionals
    
-  Cron jobs and environment variables (`PATH`)
    

**🧩 Activity:**  
Create a simple backup script:

```bash
#!/bin/bash
tar -czf backup_$(date +%F).tar.gz /home/$USER/Documents
echo "Backup completed successfully!"
```

Run it with:

```bash
bash backup.sh
```

💭 **Reflection:**  
What’s one repetitive task you could automate with a script?

🎯 **XP Earned:** +30 (Automation Hero)

---

## 🧠 Bonus Commands to Know

`grep`, `find`, `awk`, `sed`, `tar`, `zip`, `ssh`, `scp`, `rsync`, `systemctl`, `journalctl`

💡 _Learn these after completing Day 5 — they are high-value boosters._

---

## 📚 Recommended Resources

- 📺 **Video:** [Linux Crash Course for Beginners — NetworkChuck](https://www.youtube.com/watch?v=ivlT7u7YhDk)
    
- 📘 **Book:** _The Linux Command Line_ — William Shotts
    
- 🕹️ **Hands-On Practice:** [OverTheWire Bandit](https://overthewire.org/wargames/bandit/)
    
- 🧾 **Cheat Sheet:** [Linux Commands PDF](https://cheatography.com/davechild/cheat-sheets/linux-command-line/)
    

---

## 📊 Progress Tracker

| Day | Topic      | Completed | XP  | Notes / Commands to Remember |
| --- | ---------- | --------- | --- | ---------------------------- |
| 1   | Navigation | ☐         | +10 |                              |
| 2   | File Mgmt  | ☐         | +15 |                              |
| 3   | Processes  | ☐         | +20 |                              |
| 4   | Networking | ☐         | +25 |                              |
| 5   | Scripting  | ☐         | +30 |                              |

🏆 **Total XP Goal:** 100 XP → _Linux Power User Achieved!_

---

## 🧩 Reflection Zone (End of Day 5)

Write down your top 3 takeaways:

1. 💡
    
2. 💡
    
3. 💡
    

> 🎉 Congratulations! You’ve mastered Linux basics using the 80/20 rule.  
> You now understand how professionals manage systems, automate tasks, and think in commands.

---

## 🗣 How to Ask This Better Next Time

> “Create a 5-day Linux learning plan using the 80/20 rule — focus only on high-impact commands and concepts with examples, tasks, reflection prompts, and XP tracking (for Obsidian).”

---


