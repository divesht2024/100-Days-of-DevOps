# 🚀 Day 007 – Linux SSH Authentication (Password-less SSH)

## 📖 Overview

Today, I learned how to configure **password-less SSH authentication** between Linux servers using **SSH key-based authentication**. Instead of entering a password every time a remote connection is established, SSH keys provide a secure and convenient authentication mechanism.

This is a fundamental DevOps practice used for automation tools like **Ansible**, **Jenkins**, shell scripts, and CI/CD pipelines, enabling secure communication between servers without manual intervention.

---

## 🎯 Objective

- Understand SSH key-based authentication.
- Generate an SSH key pair.
- Copy the public key to remote servers.
- Configure password-less SSH login.
- Verify secure remote access.
- Learn real-world use cases and security best practices.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Operating System | Linux |
| Service | OpenSSH |
| Platform | KodeKloud |
| Category | Linux Networking & Security |

---

## 📌 Task

Configure **password-less SSH authentication** from the **jump host** (`thor` user) to all application servers using their respective users.

Example:

| Source | Destination |
|---------|-------------|
| thor | tony@stapp01 |
| thor | steve@stapp02 |
| thor | banner@stapp03 |

---

## 💻 Commands Used

### Generate an SSH Key Pair

```bash
ssh-keygen -t rsa
```

This creates:

```text
~/.ssh/id_rsa
~/.ssh/id_rsa.pub
```

---

### Copy the Public Key to a Remote Server

```bash
ssh-copy-id tony@stapp01
```

Similarly:

```bash
ssh-copy-id steve@stapp02
```

```bash
ssh-copy-id banner@stapp03
```

---

### Verify Password-less Login

```bash
ssh tony@stapp01
```

or

```bash
ssh steve@stapp02
```

or

```bash
ssh banner@stapp03
```

The connection should be established **without prompting for a password**.

---

## 📚 Concepts Learned

### What is SSH?

SSH (Secure Shell) is a secure network protocol used to remotely access and manage Linux servers over an encrypted connection.

It replaces insecure protocols like Telnet by encrypting all communication.

---

### What is SSH Key-Based Authentication?

SSH key-based authentication uses a pair of cryptographic keys:

- **Private Key** (stored securely on the client)
- **Public Key** (copied to the remote server)

When connecting, the server verifies the client's private key against the stored public key, allowing secure authentication without passwords.

---

### SSH Key Pair

```text
Client Machine

Private Key
id_rsa
      │
      │
      ▼
Remote Server

Public Key
authorized_keys
```

The private key should **never** be shared.

---

### What is `ssh-copy-id`?

The `ssh-copy-id` command copies the local public key to the remote server's:

```text
~/.ssh/authorized_keys
```

This enables password-less authentication for future SSH sessions.

---

### Why Use Password-less SSH?

Benefits include:

- Faster server access
- Secure authentication
- No repeated password prompts
- Essential for automation
- Required by many DevOps tools

---

## 🌍 Real-World Use Case

Imagine an **Ansible Control Node** managing hundreds of Linux servers.

Instead of entering passwords for every server, SSH keys are configured once.

When Ansible executes commands, it connects to all managed nodes automatically using SSH key authentication, making large-scale automation secure and efficient.

---

## 🔍 Verification

Verify SSH connectivity:

```bash
ssh tony@stapp01
```

Expected behavior:

- No password prompt.
- Successful login to the remote server.

Check the public key on the remote server:

```bash
cat ~/.ssh/authorized_keys
```

---

## 🔐 Best Practices

- Protect the private key with appropriate file permissions.
- Never share the private key.
- Use SSH keys instead of passwords whenever possible.
- Disable password authentication for production servers after verifying key-based access.
- Rotate SSH keys periodically.
- Restrict SSH access using firewalls or security groups.

---

## 🧠 Key Takeaways

- Learned how SSH key-based authentication works.
- Generated an RSA SSH key pair.
- Configured password-less SSH access.
- Learned the purpose of `ssh-copy-id`.
- Understood how SSH keys improve security and automation.
- Gained practical experience with secure remote server access.

---

## 🚀 Skills Practiced

- Linux Administration
- OpenSSH
- SSH Key Authentication
- Linux Security
- Remote Server Management
- Command-Line Operations
- DevOps Fundamentals

---

## 📖 Commands Reference

| Command | Purpose |
|----------|---------|
| `ssh-keygen -t rsa` | Generate an RSA SSH key pair |
| `ssh-copy-id user@host` | Copy the public key to a remote server |
| `ssh user@host` | Connect to a remote server |
| `cat ~/.ssh/authorized_keys` | View authorized public keys on the server |
| `ls -la ~/.ssh` | List SSH configuration files |

---

## 💡 Interview Questions

### Q1. What is SSH?

SSH (Secure Shell) is a secure protocol used to remotely access and manage Linux systems over an encrypted connection.

---

### Q2. What is the difference between a public key and a private key?

- **Public Key:** Stored on the remote server and shared openly.
- **Private Key:** Stored securely on the client and must never be shared.

---

### Q3. What is the purpose of the `authorized_keys` file?

The `authorized_keys` file stores public SSH keys that are permitted to authenticate users on the server.

---

### Q4. What does `ssh-copy-id` do?

It copies the client's public SSH key into the remote user's `~/.ssh/authorized_keys` file, enabling password-less SSH login.

---

### Q5. Why is password-less SSH important in DevOps?

It enables secure, automated communication between systems and is widely used by tools such as Ansible, Jenkins, Terraform, and CI/CD pipelines.

---

## 📌 Resources

- OpenSSH Documentation
- Linux `ssh` Manual (`man ssh`)
- Linux `ssh-keygen` Manual (`man ssh-keygen`)
- KodeKloud Linux Labs

---

## ⭐ Day 007 Summary

Today's hands-on exercise introduced me to **SSH key-based authentication**, one of the most important concepts in Linux administration and DevOps. I learned how to generate SSH keys, configure password-less authentication, and securely connect to remote servers without using passwords. This knowledge is essential for infrastructure automation, configuration management, and secure server administration in production environments.
