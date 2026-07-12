# 🚀 Day 010 – Website Content Backup Automation Using Bash Script

## 📖 Overview

Today, I learned how to automate website content backup using a **Bash script**. In this task, I created a script to archive the website files from an application server, store the backup locally, and transfer it securely to a remote storage server.

This exercise improved my understanding of Linux automation, file compression, SSH authentication, and secure file transfer, which are essential skills for a DevOps Engineer.

---

## 🎯 Objective

* Create a Bash script for website backup automation.
* Compress website files into a ZIP archive.
* Store backups in a designated archive directory.
* Transfer backup files to a remote storage server.
* Configure password-less SSH authentication.
* Execute automation scripts without using sudo inside the script.

---

## 🛠️ Environment

| Component          | Details            |
| ------------------ | ------------------ |
| Platform           | KodeKloud Engineer |
| Server             | App Server 1       |
| Operating System   | Linux              |
| Scripting Language | Bash               |
| Archive Tool       | zip                |
| Transfer Method    | SCP                |
| Category           | DevOps Automation  |

---

## 📌 Task

Create a script named:

```bash
news_archive.sh
```

Location:

```bash
/scripts/news_archive.sh
```

The script should:

1. Create a ZIP archive of:

```text
/var/www/html/news
```

2. Store the archive in:

```text
/archives/
```

3. Copy the archive to:

```text
Nautilus Storage Server:/archives/
```

4. Allow execution without password prompts.

---

# 🧰 Prerequisites

Install zip package manually before running the script.

```bash
sudo yum install zip -y
```

Verify:

```bash
zip --version
```

---

# 🔐 Configure Password-less SSH

Generate SSH key:

```bash
ssh-keygen -t rsa
```

Copy public key to storage server:

```bash
ssh-copy-id natasha@ststor01
```

Test:

```bash
ssh natasha@ststor01
```

The connection should work without asking for a password.

---

# 📝 Script Creation

Create the script:

```bash
vi /scripts/news_archive.sh
```

Add the following:

```bash
#!/bin/bash

SOURCE_DIR="/var/www/html/news"
ARCHIVE_NAME="xfusioncorp_news.zip"
LOCAL_PATH="/archives/$ARCHIVE_NAME"

REMOTE_USER="natasha"
REMOTE_SERVER="ststor01"
REMOTE_PATH="/archives"

mkdir -p /archives

zip -r $LOCAL_PATH $SOURCE_DIR

scp $LOCAL_PATH $REMOTE_USER@$REMOTE_SERVER:$REMOTE_PATH/
```

---

# 🔑 Give Execute Permission

```bash
chmod +x /scripts/news_archive.sh
```

---

# ▶️ Execute Script

Run:

```bash
/scripts/news_archive.sh
```

---

# 🔍 Verification

## Check Local Archive

```bash
ls -l /archives
```

Expected:

```text
xfusioncorp_news.zip
```

---

## Verify Storage Server

Login:

```bash
ssh natasha@ststor01
```

Check:

```bash
ls -l /archives
```

Expected:

```text
xfusioncorp_news.zip
```

---

# 📚 Concepts Learned

## Bash Automation

Bash scripting allows administrators and DevOps engineers to automate repetitive tasks.

Examples:

* Backup automation
* Log rotation
* Server monitoring
* Deployment scripts

---

## ZIP Compression

The `zip` command combines multiple files and directories into a compressed archive.

Example:

```bash
zip -r backup.zip directory/
```

The `-r` option recursively includes all files and subdirectories.

---

## SCP (Secure Copy Protocol)

SCP securely transfers files between Linux systems using SSH.

Example:

```bash
scp file user@server:/path
```

Advantages:

* Encrypted transfer
* Secure authentication
* Simple file movement

---

## SSH Key Authentication

SSH keys allow servers to communicate securely without password authentication.

Used in:

* Automation scripts
* CI/CD pipelines
* Ansible
* Server backups

---

# 🌍 Real-World Use Case

A company hosts a production website.

Every day, the DevOps team needs backups of website files.

Instead of manually creating backups:

* A Bash script creates the archive automatically.
* The backup is stored locally.
* The archive is copied to a centralized storage server.

This reduces manual effort and improves reliability.

---

# 🔐 Best Practices

* Never store passwords inside scripts.
* Use SSH keys for automation.
* Store backups in a separate location.
* Use meaningful backup names.
* Schedule scripts using cron jobs.
* Monitor backup success and failures.

---

# 🧠 Key Takeaways

* Learned how to automate backups using Bash.
* Created ZIP archives using Linux commands.
* Used SCP for secure file transfer.
* Configured password-less SSH authentication.
* Improved Linux automation skills.

---

# 🚀 Skills Practiced

* Linux Administration
* Bash Scripting
* SSH Authentication
* SCP File Transfer
* Backup Automation
* DevOps Fundamentals

---
# 💡 Interview Questions

### Q1. Why do we use Bash scripts in DevOps?

Bash scripts automate repetitive administrative tasks such as backups, deployments, monitoring, and server configuration.

---

### Q2. What is SCP?

SCP is a secure file transfer protocol that copies files between Linux systems using SSH.

---

### Q3. Why use SSH keys instead of passwords?

SSH keys provide secure, automated authentication without requiring manual password entry.

---

### Q4. What does `zip -r` do?

It recursively compresses a directory and all its contents into a ZIP archive.

---

### Q5. Why should sudo not be used inside automation scripts?

Automation scripts should run with proper permissions instead of depending on elevated privileges, improving security and maintainability.

---

# ⭐ Day 010 Summary

Today's challenge helped me understand how DevOps engineers automate backup operations using Bash scripting. I created a script to archive website content, securely transfer backups using SCP, and configure password-less SSH authentication. This task strengthened my Linux automation and scripting fundamentals, which are essential for cloud and DevOps roles.
