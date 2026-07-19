# 🚀 Day 012 – Linux Network Services Troubleshooting

## 📖 Overview

Today, I worked on troubleshooting a Linux web server where the **Apache (httpd) service was not reachable on a custom port**. The task involved identifying the root cause using Linux networking tools and restoring service availability without compromising system security.

This hands-on exercise strengthened my understanding of Linux service management, networking, and web server troubleshooting.

---

## 🎯 Objective

* Troubleshoot an Apache web server connectivity issue.
* Verify service availability using networking tools.
* Ensure Apache is listening on the required port.
* Restore access without modifying application files.
* Validate connectivity from a remote server.

---

## 🛠️ Environment

| Component       | Details                            |
| --------------- | ---------------------------------- |
| Platform        | Linux (CentOS/RHEL)                |
| Web Server      | Apache (httpd)                     |
| Service Manager | systemd                            |
| Tools Used      | curl, ss, netstat, systemctl, grep |
| Category        | Linux Networking & Troubleshooting |

---

## 📌 Task

Identify why the Apache web server was not reachable on a custom port and restore connectivity while maintaining existing security settings.

---

## 💻 Steps Performed

### 1️⃣ Verify Connectivity

From the jump host, test the web service:

```bash
curl http://stapp03:6300
```

If the request fails, continue troubleshooting on the target server.

---

### 2️⃣ Check Apache Service Status

Verify whether the Apache service is running:

```bash
sudo systemctl status httpd
```

If stopped:

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

### 3️⃣ Verify Listening Port

Check whether Apache is listening on the expected port:

```bash
sudo ss -tulpn | grep httpd
```

or

```bash
sudo netstat -tulpn | grep httpd
```

---

### 4️⃣ Verify Apache Configuration

Check the configured listening port:

```bash
sudo grep -R "Listen" /etc/httpd/
```

Example:

```text
Listen 6300
```

---

### 5️⃣ Restart Apache (If Required)

After configuration changes:

```bash
sudo systemctl restart httpd
```

---

### 6️⃣ Test Locally

Verify the service locally:

```bash
curl http://localhost:6300
```

---

### 7️⃣ Test Remotely

Return to the jump host and verify:

```bash
curl http://stapp03:6300
```

Successful HTML output confirms the issue has been resolved.

---

## 📚 Concepts Learned

### Apache (httpd)

Apache HTTP Server is one of the most widely used open-source web servers for hosting websites and web applications.

---

### systemctl

`systemctl` is used to manage services on Linux systems.

Common commands:

```bash
sudo systemctl start httpd
sudo systemctl stop httpd
sudo systemctl restart httpd
sudo systemctl status httpd
```

---

### ss

The `ss` command displays network sockets and listening ports.

Example:

```bash
sudo ss -tulpn
```

---

### netstat

`netstat` is another utility for viewing active network connections and listening ports.

Example:

```bash
sudo netstat -tulpn
```

---

### curl

`curl` is used to test web server connectivity and retrieve HTTP responses.

Example:

```bash
curl http://localhost:6300
```

---

## 🌍 Real-World Use Case

A production monitoring system reports that a company's web application is unreachable.

A DevOps engineer investigates by:

* Checking the Apache service.
* Verifying listening ports.
* Reviewing configuration files.
* Testing connectivity locally and remotely.
* Restoring the service with minimal downtime.

---

## 🔍 Verification

Verify that:

* Apache service is running.
* Apache is listening on the required port.
* The application responds locally.
* The application is reachable from the jump host.

---

## 🔐 Best Practices

* Monitor critical services continuously.
* Use custom ports only when required.
* Verify configurations before restarting services.
* Avoid modifying application files during troubleshooting.
* Follow the least-change principle in production environments.

---

## 🧠 Key Takeaways

* Learned systematic Linux troubleshooting.
* Practiced Apache service management.
* Verified network connectivity using Linux tools.
* Understood how to identify listening ports.
* Improved troubleshooting and debugging skills.

---

## 🚀 Skills Practiced

* Linux Administration
* Apache HTTP Server
* Linux Networking
* Service Management
* Troubleshooting
* System Monitoring

---



## 💡 Interview Questions

### Q1. What is the purpose of the `ss` command?

The `ss` command displays network socket information and helps verify which ports services are listening on.

---

### Q2. How do you check whether Apache is running?

```bash
sudo systemctl status httpd
```

---

### Q3. How do you verify that Apache is listening on the correct port?

```bash
sudo ss -tulpn | grep httpd
```

---

### Q4. What is the purpose of the `Listen` directive in Apache?

The `Listen` directive specifies the port on which Apache accepts incoming HTTP requests.

---

### Q5. Why is `curl` useful during troubleshooting?

`curl` allows administrators to test HTTP connectivity and verify whether a web server is responding correctly.

---

## 📌 Resources

* Apache HTTP Server Documentation
* Linux `systemctl` Manual
* Linux `ss` Command Documentation
* Linux Networking Guide

---

## ⭐ Day 012 Summary

Today's hands-on exercise focused on troubleshooting **Linux network services** by restoring Apache connectivity on a custom port. I learned how to diagnose service availability, verify listening ports, inspect Apache configuration, and validate network connectivity using standard Linux administration tools. This task closely reflects real-world DevOps and system administration troubleshooting scenarios.
