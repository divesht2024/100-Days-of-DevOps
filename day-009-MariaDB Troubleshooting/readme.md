# 🚀 Day 009 – MariaDB Troubleshooting

## 📖 Overview

Today, I learned how to troubleshoot and resolve issues related to **MariaDB**, one of the most widely used open-source relational database management systems. Database troubleshooting is a critical skill for DevOps Engineers and System Administrators because application availability often depends on healthy database services.

In this hands-on exercise, I diagnosed common MariaDB issues such as service failures, port conflicts, configuration errors, authentication problems, and connectivity issues.

---

## 🎯 Objective

* Understand common MariaDB issues.
* Verify the MariaDB service status.
* Identify configuration problems.
* Troubleshoot startup failures.
* Validate database connectivity.
* Learn production troubleshooting practices.

---

## 🛠️ Environment

| Component        | Details         |
| ---------------- | --------------- |
| Operating System | Linux           |
| Database         | MariaDB         |
| Platform         | KodeKloud       |
| Category         | Troubleshooting |

---

## 📌 Task

Troubleshoot and resolve issues preventing MariaDB from functioning correctly.

Possible issues included:

* MariaDB service not running
* Configuration errors
* Incorrect permissions
* Port conflicts
* Authentication failures
* Database connectivity issues

---

## 💻 Commands Used

### Check MariaDB Service Status

```bash
systemctl status mariadb
```

---

### Start MariaDB Service

```bash
sudo systemctl start mariadb
```

---

### Enable MariaDB Service

```bash
sudo systemctl enable mariadb
```

---

### Restart MariaDB Service

```bash
sudo systemctl restart mariadb
```

---

### View Service Logs

```bash
journalctl -u mariadb -xe
```

---

### Check Listening Ports

```bash
ss -tulpn | grep 3306
```

---

### Verify Configuration File

```bash
cat /etc/my.cnf
```

---

### Test Database Connection

```bash
mysql -u root -p
```

---

## 📚 Concepts Learned

### What is MariaDB?

MariaDB is an open-source relational database management system derived from MySQL.

It is commonly used for:

* Web applications
* E-commerce platforms
* Content Management Systems
* Enterprise applications

---

### What is Port 3306?

MariaDB listens on port **3306** by default.

Applications connect to the database service through this port.

---

### Why Does MariaDB Fail to Start?

Common reasons include:

* Invalid configuration syntax
* Port already in use
* Corrupted database files
* Disk space issues
* Permission problems

---

### Importance of Logs

Logs are often the fastest way to identify database issues.

Useful log locations include:

```text
/var/log/mariadb/
/var/log/messages
journalctl -u mariadb
```

---

## 🌍 Real-World Use Case

Imagine an e-commerce website where customers suddenly cannot place orders.

The application team discovers that the backend database is unreachable.

The DevOps engineer:

* Checks the MariaDB service status.
* Reviews logs for errors.
* Restarts the service if necessary.
* Verifies connectivity from the application server.

Quick troubleshooting minimizes downtime and restores business operations.

---

## 🔍 Verification

Verify the service:

```bash
systemctl status mariadb
```

Expected output:

```text
Active: active (running)
```

Verify database connectivity:

```bash
mysql -u root -p
```

Verify listening port:

```bash
ss -tulpn | grep 3306
```

Expected output:

```text
LISTEN 0 80 *:3306 *:*
```

---

## 🔐 Best Practices

* Monitor database services continuously.
* Enable automatic startup on boot.
* Regularly review logs.
* Perform backups frequently.
* Restrict database access using firewalls and security groups.
* Keep MariaDB updated with security patches.

---

## 🧠 Key Takeaways

* Learned how to troubleshoot MariaDB issues.
* Understood the importance of service logs.
* Learned how to verify database connectivity.
* Practiced diagnosing startup failures.
* Improved Linux troubleshooting skills.

---

## 🚀 Skills Practiced

* Linux Administration
* Database Troubleshooting
* MariaDB
* Systemd Services
* Log Analysis
* Linux Networking
* DevOps Operations

---


## 💡 Interview Questions

### Q1. What is MariaDB?

MariaDB is an open-source relational database management system and a fork of MySQL.

---

### Q2. Which port does MariaDB use by default?

MariaDB uses port **3306** by default.

---

### Q3. How do you check if MariaDB is running?

```bash
systemctl status mariadb
```

---

### Q4. How do you view MariaDB logs?

```bash
journalctl -u mariadb -xe
```

---

### Q5. How do you verify that MariaDB is listening on port 3306?

```bash
ss -tulpn | grep 3306
```

---

## 📌 Resources

* MariaDB Documentation
* Linux Systemd Documentation
* Linux Networking Documentation
* KodeKloud Engineer Labs

---

## ⭐ Day 009 Summary

Today's hands-on exercise introduced me to **MariaDB troubleshooting**, an essential operational skill for DevOps Engineers and System Administrators. I learned how to diagnose service failures, analyze logs, verify network connectivity, and resolve common database issues to maintain application availability and reliability.
