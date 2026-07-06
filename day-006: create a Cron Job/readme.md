# 🚀 Day 006 – Create a Cron Job

## 📖 Overview

Today, I learned how to automate repetitive tasks in Linux using **Cron**, one of the most widely used job schedulers in Unix/Linux systems. Cron allows administrators to schedule commands or scripts to run automatically at specified intervals, reducing manual effort and ensuring routine tasks are executed consistently.

In this lab, I installed the **cronie** package, started the **crond** service, and created a cron job for the **root** user that executes every **5 minutes**.

---

## 🎯 Objective

- Understand what Cron is.
- Install the `cronie` package.
- Start and enable the `crond` service.
- Create a cron job for the root user.
- Verify that the cron job is scheduled correctly.
- Learn real-world use cases of Cron.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Operating System | Linux (RHEL/CentOS/Rocky/AlmaLinux) |
| Service | Cron (`crond`) |
| Package | `cronie` |
| Platform | KodeKloud |
| Category | Linux Automation |

---

## 📌 Task

Perform the following tasks:

1. Install the **cronie** package.
2. Start and enable the **crond** service.
3. Create the following cron job for the **root** user:

```cron
*/5 * * * * echo hello > /tmp/cron_text
```

This job writes the word **hello** into the `/tmp/cron_text` file every **5 minutes**.

---

## 💻 Commands Used

### Install Cronie

```bash
sudo yum install -y cronie
```

or

```bash
sudo dnf install -y cronie
```

---

### Start and Enable Cron Service

```bash
sudo systemctl enable --now crond
```

---

### Verify Cron Service

```bash
sudo systemctl status crond
```

---

### Edit Root Crontab

```bash
sudo crontab -e
```

---

### Add the Cron Job

```cron
*/5 * * * * echo hello > /tmp/cron_text
```

---

### View Scheduled Cron Jobs

```bash
sudo crontab -l
```

---

## 📚 Concepts Learned

### What is Cron?

Cron is a **time-based job scheduler** in Linux that automatically executes commands or scripts at scheduled intervals.

It is commonly used for:

- System backups
- Log rotation
- Monitoring scripts
- Cleanup tasks
- Database backups
- Automated deployments

---

### What is Cronie?

**Cronie** is the package that provides the Cron daemon (`crond`) and related utilities on many Linux distributions.

It manages scheduled jobs defined in users' crontab files.

---

### What is `crond`?

`crond` is the background service responsible for checking cron schedules and executing jobs at the specified times.

Without this service running, cron jobs will not execute.

---

### Cron Syntax

A cron expression consists of five time fields followed by the command to execute.

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of Week (0–7)
│ │ │ └──── Month (1–12)
│ │ └────── Day of Month (1–31)
│ └──────── Hour (0–23)
└────────── Minute (0–59)
```

---

### Understanding the Expression

```cron
*/5 * * * * echo hello > /tmp/cron_text
```

Meaning:

| Field | Value | Meaning |
|--------|-------|---------|
| Minute | `*/5` | Every 5 minutes |
| Hour | `*` | Every hour |
| Day of Month | `*` | Every day |
| Month | `*` | Every month |
| Day of Week | `*` | Every day of the week |

The command:

```bash
echo hello > /tmp/cron_text
```

writes the text **hello** into `/tmp/cron_text` every five minutes.

---

## 🌍 Real-World Use Case

Imagine a DevOps team needs to back up application logs every night.

Instead of manually running a backup script, they schedule it with Cron:

```cron
0 2 * * * /opt/scripts/backup.sh
```

This automatically executes the backup every day at **2:00 AM**, ensuring consistency and reducing manual effort.

---

## 🔍 Verification

Verify the Cron service:

```bash
systemctl status crond
```

List scheduled cron jobs:

```bash
crontab -l
```

Check the output file after the scheduled time:

```bash
cat /tmp/cron_text
```

Expected output:

```text
hello
```

---

## 🔐 Best Practices

- Keep cron jobs simple and well-documented.
- Use absolute paths in cron commands.
- Redirect output to log files for troubleshooting.
- Regularly review scheduled jobs.
- Ensure the `crond` service is enabled after system reboots.
- Use dedicated scripts for complex automation tasks.

---

## 🧠 Key Takeaways

- Learned how Cron automates repetitive Linux tasks.
- Installed and configured the `cronie` package.
- Started and enabled the `crond` service.
- Created a cron job using `crontab`.
- Understood cron expression syntax.
- Learned how to verify scheduled jobs.

---

## 🚀 Skills Practiced

- Linux Administration
- Cron Jobs
- Linux Automation
- Task Scheduling
- System Services
- Command-Line Operations
- DevOps Fundamentals

---



## 📖 Commands Reference

| Command | Purpose |
|----------|---------|
| `yum install -y cronie` | Install the Cron package |
| `systemctl enable --now crond` | Start and enable the Cron service |
| `systemctl status crond` | Verify the Cron service |
| `crontab -e` | Edit the current user's cron jobs |
| `crontab -l` | List scheduled cron jobs |

---

## 💡 Interview Questions

### Q1. What is Cron?

Cron is a time-based job scheduler in Linux used to automatically execute commands or scripts at specified times or intervals.

---

### Q2. What is the purpose of the `crond` service?

`crond` is the daemon that monitors cron schedules and executes scheduled jobs automatically.

---

### Q3. What does the following cron expression mean?

```cron
*/5 * * * *
```

It runs the specified command **every 5 minutes**.

---

### Q4. How do you list scheduled cron jobs?

```bash
crontab -l
```

---

### Q5. Where are user-specific cron jobs stored?

User cron jobs are managed through **crontab** and stored in system-managed spool directories (such as `/var/spool/cron` on many Linux distributions).

---

## 📌 Resources

- Cron Manual (`man 5 crontab`)
- Cronie Documentation
- Linux `crontab` Manual
- KodeKloud Linux Labs

---

## ⭐ Day 006 Summary

Today's hands-on exercise introduced me to **Cron**, one of the most essential automation tools in Linux. I learned how to install the **cronie** package, start the **crond** service, and schedule recurring tasks using cron expressions. Automating routine operations with Cron is a fundamental DevOps skill that improves efficiency, reduces manual work, and ensures reliable execution of scheduled tasks.
