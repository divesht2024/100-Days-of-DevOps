# 🚀 Day 005 – SELinux Installation and Configuration



## 📖 Overview



Today, I learned about **Security-Enhanced Linux (SELinux)**, a Linux security module that provides **Mandatory Access Control (MAC)** to enhance system security. Unlike traditional Linux permissions, SELinux enforces security policies that control how users, processes, and applications interact with files and system resources.



In this lab, I learned how to install, configure, enable, disable, and verify SELinux, as well as understand its operating modes and practical use cases in production environments.



---



## 🎯 Objective



- Understand what SELinux is.

- Install SELinux packages (if required).

- Configure SELinux on a Linux system.

- Learn the different SELinux modes.

- Verify SELinux status.

- Understand real-world use cases and security benefits.



---



## 🛠️ Environment



| Component | Details |

|-----------|---------|

| Operating System | Linux (RHEL/CentOS/Rocky/AlmaLinux) |

| Security Module | SELinux |

| Platform | KodeKloud |

| Category | Linux Security |



---



## 📌 Task



Install and configure SELinux on the Linux server, verify its status, and understand how it enhances system security using Mandatory Access Control (MAC).



---



## 💻 Commands Used



### Check SELinux Status



```bash

sestatus

```



---



### Verify SELinux Configuration



```bash

cat /etc/selinux/config

```



---



### Edit SELinux Configuration



```bash

sudo vi /etc/selinux/config

```



---



### Example Configuration



```text

SELINUX=enforcing

SELINUXTYPE=targeted

```



Available modes:



```text

SELINUX=enforcing

SELINUX=permissive

SELINUX=disabled

```



---



### Change SELinux Mode Temporarily



Enable Enforcing Mode



```bash

sudo setenforce 1

```



Enable Permissive Mode



```bash

sudo setenforce 0

```



---



### Verify Current Mode



```bash

getenforce

```



---



## 📚 Concepts Learned



### What is SELinux?



SELinux (Security-Enhanced Linux) is a Linux kernel security feature that implements **Mandatory Access Control (MAC)**.



It restricts what users, applications, and services can access—even if they have root privileges.



This greatly reduces the impact of compromised applications and unauthorized access.



---



### What is Mandatory Access Control (MAC)?



Mandatory Access Control is a security model where access decisions are enforced by system-defined security policies.



Unlike traditional Linux permissions (Discretionary Access Control), users cannot override SELinux policies.



---



### SELinux Modes



#### Enforcing Mode



- Security policies are actively enforced.

- Unauthorized actions are blocked.

- Security violations are logged.



---



#### Permissive Mode



- Security policies are **not enforced**.

- Violations are logged but not blocked.

- Useful for troubleshooting and testing.



---



#### Disabled Mode



- SELinux is completely turned off.

- No security policies are applied.

- Not recommended for production systems.



---



### SELinux Policy Types



#### Targeted Policy



- Protects selected services.

- Default policy on most Linux distributions.

- Commonly used in production.



#### MLS (Multi-Level Security)



- Provides advanced security classifications.

- Used in military and government environments.



---



## 🌍 Real-World Use Case



Imagine a web server running Apache.



An attacker exploits a vulnerability in the web application and gains access to the Apache process.



Without SELinux:



- The attacker may access sensitive files across the system.



With SELinux:



- Apache is restricted by SELinux policies.

- It can access only the files and directories explicitly permitted.

- Even if compromised, the attacker's actions are limited, reducing the overall impact.



---



## 🔍 Verification



Check SELinux status:



```bash

sestatus

```



Expected Output



```text

SELinux status:                 enabled

Current mode:                   enforcing

Policy from config file:        targeted

```



Verify the current mode:



```bash

getenforce

```



Possible outputs:



```text

Enforcing

```



```text

Permissive

```



```text

Disabled

```



---



## 🔐 Security Benefits



- Provides Mandatory Access Control (MAC).

- Limits the damage caused by compromised applications.

- Prevents unauthorized access to sensitive files.

- Enforces security policies across the system.

- Improves compliance with enterprise security standards.

- Enhances overall Linux system security.



---



## 🧠 Key Takeaways



- Learned what SELinux is and why it is important.

- Understood the difference between MAC and traditional Linux permissions.

- Learned the three SELinux operating modes.

- Learned how to configure SELinux using `/etc/selinux/config`.

- Learned how to verify SELinux status using `sestatus` and `getenforce`.

- Understood why SELinux is widely used in enterprise Linux environments.



---



## 🚀 Skills Practiced



- Linux Administration

- Linux Security

- SELinux

- Mandatory Access Control (MAC)

- System Hardening

- Command-Line Operations

- Security Configuration



---





## 📖 Commands Reference



| Command | Purpose |

|----------|---------|

| `sestatus` | Display SELinux status |

| `getenforce` | Show the current SELinux mode |

| `setenforce 1` | Switch to Enforcing mode temporarily |

| `setenforce 0` | Switch to Permissive mode temporarily |

| `cat /etc/selinux/config` | View SELinux configuration |

| `vi /etc/selinux/config` | Edit SELinux configuration |



---



## 💡 Interview Questions



### Q1. What is SELinux?



SELinux (Security-Enhanced Linux) is a Linux security module that implements Mandatory Access Control (MAC) to restrict access to system resources based on security policies.



---



### Q2. What are the three SELinux modes?



- Enforcing

- Permissive

- Disabled



---



### Q3. What is the difference between Enforcing and Permissive mode?



**Enforcing** blocks actions that violate SELinux policies, while **Permissive** allows the actions but logs the violations for analysis.



---



### Q4. What is the difference between DAC and MAC?



- **DAC (Discretionary Access Control):** Access is controlled by file owners using traditional Linux permissions.

- **MAC (Mandatory Access Control):** Access is controlled by system-wide security policies that users cannot override.



---



### Q5. How do you check whether SELinux is enabled?



Use either:



```bash

sestatus

```



or



```bash

getenforce

```



---



## 📌 Resources



- Red Hat SELinux Documentation

- SELinux Project Documentation

- Linux `sestatus` Manual

- KodeKloud Linux Labs



---



## ⭐ Day 005 Summary

Today's hands-on exercise introduced me to **SELinux**, one of the most important security features in enterprise Linux systems. I learned how to install and configure SELinux, understand its operating modes, verify its status, and appreciate how Mandatory Access Control (MAC) strengthens system security. This knowledge is essential for securing production Linux servers and is a valuable skill for DevOps Engineers and Linux System Administrators.
