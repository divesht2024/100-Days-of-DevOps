# 🚀 Day 013 – IPtables Installation and Configuration

## 📖 Overview

Today, I learned about **Linux firewall management using IPtables**. I practiced installing IPtables, creating firewall rules, controlling network traffic, and understanding how Linux systems protect services by filtering incoming and outgoing connections.

This hands-on exercise improved my knowledge of Linux security, networking, and server hardening techniques used in DevOps environments.

---

## 🎯 Objective

* Understand Linux firewall concepts.
* Install and configure IPtables.
* Create firewall rules.
* Allow and block network traffic.
* Verify firewall configurations.
* Learn basic server security practices.

---

## 🛠️ Environment

| Component       | Details                       |
| --------------- | ----------------------------- |
| Platform        | Linux (CentOS/RHEL)           |
| Firewall Tool   | IPtables                      |
| Service Manager | systemd                       |
| Category        | Linux Security & Networking   |
| Tools Used      | iptables, systemctl, curl, ss |

---

# 📌 Task

Install IPtables on the Linux server and configure firewall rules to control network access.

---

# 💻 Steps Performed

## 1️⃣ Check Existing Firewall Rules

First, check current IPtables rules:

```bash
sudo iptables -L -n -v
```

Explanation:

* `-L` → List rules
* `-n` → Show IP addresses and ports numerically
* `-v` → Show detailed information

---

## 2️⃣ Install IPtables Package

### CentOS / RHEL

```bash
sudo yum install iptables-services -y
```

or:

```bash
sudo dnf install iptables-services -y
```

---

## 3️⃣ Enable IPtables Service

Start the service:

```bash
sudo systemctl start iptables
```

Enable at boot:

```bash
sudo systemctl enable iptables
```

Check status:

```bash
sudo systemctl status iptables
```

---

# 🔥 4️⃣ Understanding IPtables Chains

IPtables contains three default chains:

| Chain   | Purpose                   |
| ------- | ------------------------- |
| INPUT   | Controls incoming traffic |
| OUTPUT  | Controls outgoing traffic |
| FORWARD | Controls routed traffic   |

---

# 🔐 5️⃣ Allow SSH Access

Before adding firewall rules, allow SSH to avoid locking yourself out.

```bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

---

# 🌐 6️⃣ Allow HTTP Traffic

Allow web traffic:

```bash
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```

---

# 🚫 7️⃣ Block a Specific Port

Example: Block port 8080

```bash
sudo iptables -A INPUT -p tcp --dport 8080 -j DROP
```

---

# 8️⃣ Allow Established Connections

Allow existing connections:

```bash
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

# 9️⃣ Set Default Firewall Policy

Example: Drop all incoming traffic by default:

```bash
sudo iptables -P INPUT DROP
```

Allow outgoing traffic:

```bash
sudo iptables -P OUTPUT ACCEPT
```

---

# 🔎 10️⃣ Verify Rules

List configured rules:

```bash
sudo iptables -L -n --line-numbers
```

Example output:

```text
Chain INPUT (policy DROP)

num target     prot opt source destination
1   ACCEPT     tcp  --  0.0.0.0/0  tcp dpt:22
2   ACCEPT     tcp  --  0.0.0.0/0  tcp dpt:80
```

---

# 💾 11️⃣ Save IPtables Rules

Save current rules:

```bash
sudo service iptables save
```

or:

```bash
sudo iptables-save > /etc/sysconfig/iptables
```

---

# 📚 Concepts Learned

## What is IPtables?

IPtables is a Linux firewall utility used to configure packet filtering rules.

It controls:

* Incoming traffic
* Outgoing traffic
* Network forwarding

---

## How IPtables Works

When a packet reaches a Linux server:

```
Incoming Packet
        |
        ↓
     IPtables
        |
        ↓
Rule Matching
        |
        ↓
 ACCEPT / DROP / REJECT
```

---

## Difference Between DROP and REJECT

| DROP                           | REJECT                     |
| ------------------------------ | -------------------------- |
| Silently discards packets      | Sends error response       |
| More secure                    | Provides feedback          |
| Common in production firewalls | Useful for troubleshooting |

---

# 🌍 Real-World Use Case

A production Linux server hosts a web application.

A DevOps engineer configures IPtables to:

* Allow SSH access for administrators.
* Allow HTTP/HTTPS traffic for users.
* Block unnecessary ports.
* Reduce attack surface.

---

# 🔍 Verification

Verify:

✅ IPtables installed
✅ Firewall service running
✅ Required ports allowed
✅ Unnecessary ports blocked
✅ Rules saved permanently

---

# 🔐 Best Practices

* Always allow SSH before applying DROP policies.
* Avoid opening unnecessary ports.
* Review firewall rules regularly.
* Document firewall changes.
* Use security groups along with host firewalls in cloud environments.

---

# 🧠 Key Takeaways

* Learned Linux firewall fundamentals.
* Installed and configured IPtables.
* Created traffic filtering rules.
* Understood firewall chains and policies.
* Improved Linux server security knowledge.

---

# 🚀 Skills Practiced

* Linux Administration
* IPtables Firewall
* Network Security
* Port Management
* Server Hardening
* Troubleshooting

---

# 💡 Interview Questions

### Q1. What is IPtables?

IPtables is a Linux firewall utility used to define rules for filtering network traffic.

---

### Q2. What are IPtables chains?

The three default chains are:

* INPUT
* OUTPUT
* FORWARD

---

### Q3. Difference between IPtables and Security Groups?

| IPtables            | Security Groups                  |
| ------------------- | -------------------------------- |
| Host-based firewall | Cloud network firewall           |
| Runs inside OS      | Managed by cloud provider        |
| Controls OS traffic | Controls instance network access |

---

### Q4. How do you view IPtables rules?

```bash
iptables -L -n -v
```

---

### Q5. Why should SSH be allowed before setting INPUT policy to DROP?

Because blocking SSH first can lock administrators out of the server.

---

# ⭐ Day 013 Summary

Today I learned how to install and configure **IPtables firewall on Linux**. I practiced creating firewall rules, controlling network traffic, securing server access, and understanding how firewalls protect production systems. These concepts are essential for Linux administration, Cloud Security, and DevOps operations.
