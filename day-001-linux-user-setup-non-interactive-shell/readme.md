# 🚀 Day 001 – Linux User Setup with Non-Interactive Shell

## 📖 Overview

Today's task focused on creating a Linux user with a **non-interactive shell**. This type of user is commonly used for service accounts, automation tools, backup agents, and applications that require system access but should **not** be allowed to log into the server.

This exercise helped me understand Linux user management, shell types, and a basic security best practice used in production environments.

---

## 🎯 Objective

- Create a Linux user named `jim`.
- Assign a non-interactive shell to prevent login access.
- Verify that the user was created successfully.

---

## 🛠️ Environment

- Operating System: Linux
- Distribution: Ubuntu/CentOS (Lab Environment)
- Platform: KodeKloud

---

## 📌 Task

Create a user named **jim** with a **non-interactive shell**.

---

## 💻 Commands Used

### Create the user

```bash
sudo useradd -s /sbin/nologin jim
```

### Verify the user

```bash
grep jim /etc/passwd
```

Example Output

```text
jim:x:1005:1005::/home/jim:/sbin/nologin
```

---

## 📚 Concepts Learned

### What is a Linux User?

A Linux user is an account that allows a person or application to access system resources. Every user has a unique username, user ID (UID), home directory, and default shell.

---

### What is a Shell?

A shell is a command-line interface that allows users to interact with the Linux operating system.

Common interactive shells include:

- `/bin/bash`
- `/bin/sh`
- `/bin/zsh`

These shells allow users to execute commands after logging in.

---

### What is a Non-Interactive Shell?

A non-interactive shell prevents a user from logging into the system.

Common examples include:

```text
/sbin/nologin
/usr/sbin/nologin
/bin/false
```

These shells are mainly assigned to:

- Service accounts
- Backup agents
- Monitoring tools
- Database users
- Automation scripts

---

## 🔍 Why Use a Non-Interactive Shell?

Allowing every user to log into a server increases security risks.

If an account is only required for running an application or service, there is no reason to allow terminal access.

Using a non-interactive shell:

- Prevents unauthorized login
- Reduces the attack surface
- Follows the Principle of Least Privilege
- Improves server security

---

## 🌍 Real-World Example

Imagine a backup software running on a production server.

The application requires a Linux user account to read files and perform backups.

However, no administrator or attacker should be able to log into that account.

Instead of assigning `/bin/bash`, the account is created with:

```text
/sbin/nologin
```

The application continues to work normally, but interactive login is blocked.

---

## ✅ Verification

Check whether the user exists:

```bash
grep jim /etc/passwd
```

Check the assigned shell:

```bash
getent passwd jim
```

Verify the user's ID:

```bash
id jim
```

---

## 🧠 Key Takeaways

- Every Linux user has a default shell.
- Interactive shells allow users to log in and execute commands.
- Non-interactive shells prevent login access.
- Service accounts should not have interactive login permissions.
- `/sbin/nologin` is commonly used to secure application accounts.
- This is a basic but important Linux security practice.

---

## 🚀 Skills Practiced

- Linux User Management
- Linux Commands
- User Creation
- Linux Security Basics
- System Administration
- Shell Configuration

---


## 📌 Resources

- Linux `useradd` command
- Linux `passwd` database (`/etc/passwd`)
- Linux shell documentation
- KodeKloud Linux Labs

---

### ⭐ Day 001 Complete!

This exercise strengthened my understanding of Linux user management and introduced an important security best practice used in real-world DevOps and System Administration environments.
