
# 🚀 Day 014 – Linux Process Troubleshooting

## 📖 Overview

Today, I learned how to troubleshoot Linux processes by identifying, monitoring, and managing running services and applications. Process troubleshooting is a critical Linux administration skill that helps diagnose high CPU usage, excessive memory consumption, unresponsive applications, and failed services.

This hands-on exercise improved my understanding of Linux process management, system monitoring, and production troubleshooting techniques.

---

## 🎯 Objective

* Understand Linux process management.
* Monitor running processes.
* Identify resource-intensive processes.
* Start, stop, and restart services.
* Troubleshoot failed or unresponsive processes.
* Improve Linux system administration skills.

---

## 🛠️ Environment

| Component  | Details                                                                  |
| ---------- | ------------------------------------------------------------------------ |
| Platform   | Linux (CentOS/RHEL)                                                      |
| Category   | Process Management & Troubleshooting                                     |
| Tools Used | ps, top, htop, pidof, pgrep, kill, pkill, killall, systemctl, journalctl |

---

## 📌 Task

Investigate Linux processes, identify issues affecting system performance or service availability, and restore normal operation using standard Linux troubleshooting tools.

---

## 💻 Steps Performed

### 1️⃣ View Running Processes

Display all running processes:

```bash
ps -ef
```

Or:

```bash
ps aux
```

---

### 2️⃣ Monitor System Processes

Display real-time process information:

```bash
top
```

If installed:

```bash
htop
```

---

### 3️⃣ Find a Specific Process

Locate a process by name:

```bash
pgrep httpd
```

or

```bash
pidof httpd
```

---

### 4️⃣ Check Process Details

Display detailed information:

```bash
ps -fp <PID>
```

Example:

```bash
ps -fp 1234
```

---

### 5️⃣ Stop a Process

Terminate gracefully:

```bash
kill <PID>
```

Force terminate:

```bash
kill -9 <PID>
```

Terminate by process name:

```bash
pkill httpd
```

or

```bash
killall httpd
```

---

### 6️⃣ Manage Services

Check service status:

```bash
sudo systemctl status httpd
```

Start service:

```bash
sudo systemctl start httpd
```

Restart service:

```bash
sudo systemctl restart httpd
```

Stop service:

```bash
sudo systemctl stop httpd
```

Enable service on boot:

```bash
sudo systemctl enable httpd
```

---

### 7️⃣ Check Service Logs

View service logs:

```bash
sudo journalctl -u httpd
```

Latest logs:

```bash
sudo journalctl -u httpd -xe
```

---

### 8️⃣ Verify Resource Usage

Display memory usage:

```bash
free -h
```

Display disk usage:

```bash
df -h
```

Display CPU information:

```bash
lscpu
```

---

## 📚 Concepts Learned

### What is a Process?

A process is a running instance of a program. Every process is assigned a unique **Process ID (PID)** by the Linux kernel.

---

### Process States

Common Linux process states:

| State    | Meaning                              |
| -------- | ------------------------------------ |
| Running  | Currently executing                  |
| Sleeping | Waiting for an event                 |
| Stopped  | Paused                               |
| Zombie   | Process completed but not cleaned up |

---

### Process Management Commands

| Command   | Purpose                        |
| --------- | ------------------------------ |
| `ps`      | Display running processes      |
| `top`     | Monitor processes in real time |
| `htop`    | Interactive process viewer     |
| `pgrep`   | Find a process by name         |
| `pidof`   | Display a process ID           |
| `kill`    | Terminate a process            |
| `pkill`   | Kill processes by name         |
| `killall` | Stop all matching processes    |

---

## 🌍 Real-World Use Case

A production web application becomes unresponsive due to high CPU usage.

A DevOps engineer:

* Identifies the resource-intensive process using `top`.
* Finds the PID.
* Reviews service logs.
* Restarts the affected service.
* Verifies that the application is accessible again.

---

## 🔍 Verification

Verify that:

* Required services are running.
* Resource usage is within acceptable limits.
* Failed processes have been restarted.
* Application connectivity is restored.

---

## 🔐 Best Practices

* Investigate logs before killing a process.
* Use graceful termination (`kill`) before force termination (`kill -9`).
* Monitor CPU and memory usage regularly.
* Enable critical services to start automatically.
* Avoid killing system-critical processes unless necessary.

---

## 🧠 Key Takeaways

* Learned Linux process management fundamentals.
* Monitored CPU, memory, and process activity.
* Diagnosed service failures.
* Used Linux commands to troubleshoot production issues.
* Improved Linux administration and debugging skills.

---

## 🚀 Skills Practiced

* Linux Administration
* Process Management
* System Monitoring
* Service Management
* Performance Troubleshooting
* Production Support

---

## 💡 Interview Questions

### Q1. What is a PID?

A PID (Process ID) is a unique identifier assigned to every running process in Linux.

---

### Q2. What is the difference between `kill` and `kill -9`?

`kill` sends a SIGTERM signal, allowing a process to exit gracefully, while `kill -9` sends SIGKILL, forcing immediate termination.

---

### Q3. Which command shows running processes in real time?

The `top` command (or `htop` if installed) displays real-time process and resource usage.

---

### Q4. How do you find the PID of a running process?

Use:

```bash
pgrep <process-name>
```

or:

```bash
pidof <process-name>
```

---

### Q5. How do you check why a service failed?

Use:

```bash
sudo journalctl -u <service-name>
```

or:

```bash
sudo systemctl status <service-name>
```

---

## 📌 Resources

* Linux `ps` Manual
* Linux `top` Manual
* Linux `systemctl` Documentation
* Linux `journalctl` Documentation

---

## ⭐ Day 014 Summary

Today's hands-on exercise focused on **Linux Process Troubleshooting**. I learned how to inspect running processes, monitor CPU and memory usage, identify problematic services, analyze logs, and restore application availability using Linux process management and troubleshooting tools. These are essential skills for Linux Administrators, DevOps Engineers, SREs, and Cloud Engineers.
