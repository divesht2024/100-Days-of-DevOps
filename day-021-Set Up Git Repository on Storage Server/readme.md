
# 🚀 Day 021 – Set Up Git Repository on Storage Server

## 📖 Overview

Today, I learned how to set up a **Git repository on a Linux storage server**. Git is a distributed version control system used by developers and DevOps teams to track code changes, collaborate, and manage application source code.

In this hands-on exercise, I installed Git, created a bare repository on a storage server, configured permissions, and verified repository access.

This task improved my understanding of Git server setup, repository management, Linux permissions, and source code version control workflows.

---

# 🎯 Objective

* Install Git on the storage server.
* Create a Git repository.
* Configure repository permissions.
* Initialize a bare repository.
* Verify Git repository access.

---

# 🛠️ Environment

| Component       | Details             |
| --------------- | ------------------- |
| Platform        | Linux (CentOS/RHEL) |
| Version Control | Git                 |
| Server Type     | Storage Server      |
| Repository Type | Bare Repository     |
| Category        | DevOps Tools        |

---

# 📌 Task

Set up a Git repository on the storage server so that developers can use it as a centralized remote repository for code collaboration.

---

# 💻 Steps Performed

## 1️⃣ Connect to Storage Server

Login using SSH:

```bash
ssh user@storage-server
```

Example:

```bash
ssh natasha@ststor01
```

---

# 2️⃣ Install Git

### CentOS / RHEL

```bash
sudo dnf install git -y
```

### Ubuntu

```bash
sudo apt update
sudo apt install git -y
```

Verify installation:

```bash
git --version
```

Example output:

```text
git version 2.x.x
```

---

# 3️⃣ Create Repository Directory

Create a directory for storing Git repositories:

```bash
sudo mkdir -p /opt/git
```

Change ownership:

```bash
sudo chown -R git:git /opt/git
```

---

# 4️⃣ Create a Git User (If Required)

Create a dedicated Git user:

```bash
sudo useradd git
```

Set password:

```bash
sudo passwd git
```

---

# 5️⃣ Initialize a Bare Git Repository

Navigate to repository location:

```bash
cd /opt/git
```

Create repository:

```bash
sudo git init --bare project.git
```

Example output:

```text
Initialized empty Git repository in /opt/git/project.git/
```

---

# 6️⃣ Verify Repository Structure

Check files:

```bash
ls -l /opt/git/project.git
```

A bare repository contains:

```text
HEAD
branches
config
description
hooks
info
objects
refs
```

---

# 7️⃣ Configure Repository Permissions

Set ownership:

```bash
sudo chown -R git:git /opt/git/project.git
```

Set appropriate permissions:

```bash
sudo chmod -R 755 /opt/git/project.git
```

---

# 8️⃣ Clone Repository From Client Machine

On developer machine:

```bash
git clone git@storage-server:/opt/git/project.git
```

Example:

```bash
git clone git@ststor01:/opt/git/project.git
```

---

# 9️⃣ Add Code and Push

Move into repository:

```bash
cd project
```

Create a file:

```bash
echo "Hello DevOps" > README.md
```

Add file:

```bash
git add README.md
```

Commit:

```bash
git commit -m "Initial commit"
```

Push:

```bash
git push origin main
```

---

# 📚 Concepts Learned

## What is Git?

Git is a distributed version control system that tracks changes in source code and enables collaboration between developers.

---

## What is a Git Repository?

A Git repository stores:

* Source code
* Commit history
* Branch information
* Configuration
* Metadata

---

## What is a Bare Repository?

A bare repository contains only Git metadata and does not contain a working directory.

It is mainly used as a remote repository.

Example:

```text
project.git
│
├── HEAD
├── objects
├── refs
├── hooks
└── config
```

---

# 🏗️ Git Server Architecture

```text
        Developer 1
             |
             |
        git push/pull
             |
             |
     Storage Server
             |
     Bare Git Repository
             |
             |
        Developer 2
```

---

# 🌍 Real-World Use Case

In an organization:

* Developers write application code.
* Code is pushed to a centralized Git repository.
* CI/CD tools like Jenkins or GitHub Actions pull the latest code.
* Applications are automatically built and deployed.

Example workflow:

```text
Developer
    |
    |
Git Commit
    |
    |
Git Repository
    |
    |
Jenkins Pipeline
    |
    |
Production Deployment
```

---

# 🔍 Verification

Verify:

✅ Git installed successfully.
✅ Repository created.
✅ Bare repository initialized.
✅ Permissions configured.
✅ Repository accessible remotely.

Useful commands:

```bash
git --version
```

```bash
git status
```

```bash
git log
```

```bash
ls -la project.git
```

---

# 🔐 Best Practices

* Use SSH authentication instead of passwords.
* Create dedicated Git users.
* Restrict repository permissions.
* Take regular backups of repositories.
* Use branch protection policies.
* Avoid storing secrets in Git repositories.
* Integrate Git with CI/CD pipelines.

---

# 🧠 Key Takeaways

* Installed Git on a storage server.
* Created a centralized Git repository.
* Learned bare repository concepts.
* Configured Linux permissions.
* Understood Git-based collaboration workflow.

---

# 🚀 Skills Practiced

* Git
* Linux Administration
* Repository Management
* SSH Authentication
* File Permissions
* DevOps Workflow


---

# 💡 Interview Questions

### Q1. What is Git?

Git is a distributed version control system used to track source code changes and support collaboration.

---

### Q2. What is the difference between normal and bare Git repositories?

| Normal Repository        | Bare Repository                  |
| ------------------------ | -------------------------------- |
| Contains working files   | Contains only Git metadata       |
| Used by developers       | Used as remote server repository |
| Created using `git init` | Created using `git init --bare`  |

---

### Q3. Why are bare repositories used on servers?

Bare repositories do not have a working directory, making them suitable as centralized repositories where multiple developers can push and pull code.

---

### Q4. How do you create a Git repository?

Normal repository:

```bash
git init
```

Bare repository:

```bash
git init --bare repo.git
```

---

### Q5. How does Jenkins use Git repositories?

Jenkins connects to Git repositories, pulls the latest source code, builds applications, runs tests, and deploys software automatically through CI/CD pipelines.

---

# 📌 Resources

* Git Documentation
* Linux Administration Guide
* SSH Documentation
* DevOps CI/CD Best Practices

---

# ⭐ Day 021 Summary

Today's hands-on exercise focused on **setting up a Git repository on a storage server**. I installed Git, created a bare repository, configured permissions, and learned how centralized Git repositories support collaboration and CI/CD workflows. This is a fundamental skill for DevOps engineers managing source code and automation pipelines.
