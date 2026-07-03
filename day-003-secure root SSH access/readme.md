# 🚀 Day 003 – Secure Root SSH Access

## 📖 Overview

Today, I learned how to **secure SSH access for the root user** in Linux. Since the **root account has unrestricted privileges**, allowing direct SSH login can expose a server to significant security risks. As a best practice, system administrators either **disable root SSH login completely** or **restrict it** based on organizational security policies.

This lab helped me understand SSH configuration, root login security, and best practices for protecting Linux servers from unauthorized access.

---

## 🎯 Objective

- Understand why root SSH access is considered a security risk.
- Configure SSH settings to secure root login.
- Learn how to modify the SSH daemon configuration.
- Verify the SSH configuration.
- Understand best practices for secure remote administration.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Operating System | Linux |
| Service | OpenSSH Server |
| Platform | KodeKloud |
| Category | Linux Security |

---

## 📌 Task

Configure the SSH server to **secure root SSH access** by modifying the SSH daemon configuration according to the required security policy.

---

## 💻 Commands Used

### Open the SSH configuration file

```bash
sudo vi /etc/ssh/sshd_config
```

or

```bash
sudo nano /etc/ssh/sshd_config
```

---

### Configure Root Login

Allow root login

```text
PermitRootLogin yes
```

Disable root login

```text
PermitRootLogin no
```

Allow only SSH key authentication

```text
PermitRootLogin prohibit-password
```

---

### Restart SSH Service

Ubuntu/Debian

```bash
sudo systemctl restart ssh
```

RHEL/CentOS

```bash
sudo systemctl restart sshd
```

---

### Verify SSH Service

```bash
sudo systemctl status ssh
```

or

```bash
sudo systemctl status sshd
```

---

### Verify Configuration

```bash
grep PermitRootLogin /etc/ssh/sshd_config
```

---

## 📚 Concepts Learned

### What is SSH?

SSH (Secure Shell) is a secure network protocol used to remotely access and manage Linux servers over an encrypted connection.

Unlike Telnet, SSH encrypts all communication, protecting credentials and data from interception.

---

### Who is the Root User?

The **root** user is the superuser in Linux.

It has unrestricted access to:

- System files
- User accounts
- Services
- Packages
- Network configuration
- Security settings

Because of these privileges, protecting root access is critical.

---

### What is `PermitRootLogin`?

`PermitRootLogin` is a configuration directive in the SSH server configuration file that controls whether the root user can log in through SSH.

Common options include:

| Value | Description |
|-------|-------------|
| `yes` | Allows direct root login |
| `no` | Completely disables root login |
| `prohibit-password` | Allows only SSH key authentication for root |
| `forced-commands-only` | Allows login only for forced commands with SSH keys |

---

### Why Secure Root SSH Access?

Allowing direct root login can expose the server to:

- Brute-force attacks
- Credential theft
- Unauthorized administrative access
- Increased security risks

Disabling or restricting root login significantly improves server security.

---

## 🌍 Real-World Use Case

Imagine an organization hosting production applications on Linux servers.

Instead of allowing administrators to log in directly as **root**, each administrator logs in using their own user account with SSH keys. When administrative privileges are required, they use:

```bash
sudo
```

This approach provides:

- Better security
- User accountability
- Audit trails
- Reduced risk of unauthorized root access

---

## 🔍 Verification

Check the SSH configuration:

```bash
grep PermitRootLogin /etc/ssh/sshd_config
```

Check SSH service status:

```bash
sudo systemctl status ssh
```

or

```bash
sudo systemctl status sshd
```

Verify the SSH daemon is running after applying the configuration changes.

---

## 🔐 Security Best Practices

- Disable direct root login whenever possible.
- Use SSH key authentication instead of passwords.
- Disable password authentication if SSH keys are used.
- Grant administrative privileges through `sudo`.
- Keep OpenSSH updated.
- Restrict SSH access using firewalls or security groups.
- Monitor SSH login attempts regularly.

---

## 🧠 Key Takeaways

- Learned how SSH enables secure remote access to Linux servers.
- Understood why direct root login is a security concern.
- Learned how to configure `PermitRootLogin` in the SSH configuration.
- Learned how to restart and verify the SSH service.
- Understood best practices for securing Linux servers.

---

## 🚀 Skills Practiced

- Linux Administration
- OpenSSH Configuration
- SSH Security
- Linux User Management
- System Hardening
- Server Security
- Command-Line Operations

---


## 📖 Commands Reference

| Command | Purpose |
|----------|---------|
| `vi /etc/ssh/sshd_config` | Edit SSH configuration |
| `systemctl restart ssh` | Restart SSH service (Ubuntu/Debian) |
| `systemctl restart sshd` | Restart SSH service (RHEL/CentOS) |
| `systemctl status ssh` | Check SSH service status |
| `grep PermitRootLogin /etc/ssh/sshd_config` | Verify root login configuration |

---

## 💡 Interview Questions

### Q1. What is SSH?

SSH (Secure Shell) is a secure protocol used to remotely access and manage Linux systems over an encrypted connection.

---

### Q2. Why is direct root SSH login discouraged?

Because the root account has full administrative privileges, allowing direct login increases the risk of brute-force attacks and unauthorized access.

---

### Q3. What does `PermitRootLogin no` do?

It completely disables SSH login for the root user.

---

### Q4. What is the recommended way to perform administrative tasks?

Log in with a regular user account and use the `sudo` command when elevated privileges are required.

---

### Q5. Where is the SSH server configuration file located?

```text
/etc/ssh/sshd_config
```

---

## 📌 Resources

- OpenSSH Documentation
- Linux `sshd_config` Manual
- KodeKloud Linux Labs
- Linux Security Best Practices

---

## ⭐ Day 003 Summary

Today's hands-on exercise helped me understand the importance of securing **root SSH access** on Linux servers. I learned how to configure the SSH daemon, control root login using the `PermitRootLogin` directive, and apply security best practices such as using SSH keys and `sudo` instead of direct root access. These practices are essential for hardening Linux servers in production environments.
