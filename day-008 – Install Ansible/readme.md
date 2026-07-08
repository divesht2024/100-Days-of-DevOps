# 🚀 Day 008 – Install Ansible

## 📖 Overview

Today, I learned how to install **Ansible 4.9.0** on a Linux server using **pip3** instead of the operating system package manager. Ansible is one of the most popular **Configuration Management** and **Infrastructure Automation** tools used in DevOps.

In this lab, the requirement was to install **Ansible version 4.9.0** on the **Jump Host** and ensure that the Ansible binary was available globally so that all users on the system could execute Ansible commands.

---

## 🎯 Objective

* Install Ansible version **4.9.0**.
* Use **pip3 only** for installation.
* Ensure Ansible commands are globally accessible.
* Verify the installed version.
* Understand Ansible's role in DevOps automation.

---

## 🛠️ Environment

| Component           | Details                  |
| ------------------- | ------------------------ |
| Operating System    | Linux                    |
| Platform            | KodeKloud                |
| Tool                | Ansible                  |
| Installation Method | pip3                     |
| Ansible Version     | 4.9.0                    |
| Category            | Configuration Management |

---

## 📌 Task

Perform the following steps:

1. Install Ansible version **4.9.0** using `pip3`.
2. Ensure the Ansible executable is available globally.
3. Verify the installation.

---

## 💻 Commands Used

### Verify Python3 Installation

```bash
python3 --version
```

---

### Verify pip3 Installation

```bash
pip3 --version
```

---

### Install Ansible 4.9.0

```bash
sudo pip3 install ansible==4.9.0
```

---

### Verify Installation

```bash
ansible --version
```

Expected output:

```text
ansible [core 2.11.x]
ansible 4.9.0
```

---

### Verify Global Accessibility

Switch to another user and test:

```bash
su - someuser
ansible --version
```

The command should work successfully for all users.

---

## 📚 Concepts Learned

### What is Ansible?

Ansible is an open-source automation tool used for:

* Configuration Management
* Application Deployment
* Infrastructure Provisioning
* Server Orchestration
* Continuous Delivery

---

### Why is Ansible Popular?

Ansible is widely used because it is:

* Agentless
* Simple to learn
* YAML-based
* SSH-based
* Easy to scale

Unlike many other automation tools, Ansible does not require agents to be installed on managed nodes.

---

### What is pip3?

`pip3` is the package manager for Python 3.

It allows users to install Python packages directly from the Python Package Index (PyPI).

Example:

```bash
pip3 install package-name
```

---

### Why Use pip3 for Installing Ansible?

Advantages include:

* Access to specific versions
* Faster updates
* Independent of OS repositories
* Better compatibility for lab environments

---

### What Does "Globally Available" Mean?

A globally available command can be executed by any user on the system without specifying its full installation path.

Example:

```bash
ansible --version
```

instead of:

```bash
/usr/local/bin/ansible --version
```

---

## 🌍 Real-World Use Case

Imagine a DevOps team managing hundreds of Linux servers.

Instead of manually configuring each server, they use Ansible playbooks to:

* Install packages
* Create users
* Configure services
* Deploy applications
* Manage security settings

This dramatically reduces manual work and ensures consistency across environments.

---

## 🔍 Verification

Verify installation:

```bash
ansible --version
```

Verify executable path:

```bash
which ansible
```

Example output:

```text
/usr/local/bin/ansible
```

Verify package version:

```bash
pip3 show ansible
```

---

## 🔐 Best Practices

* Install only required versions.
* Use Python virtual environments for development environments.
* Keep Ansible updated for security fixes.
* Store playbooks in version control systems such as Git.
* Use SSH keys instead of passwords for automation.

---

## 🧠 Key Takeaways

* Learned how to install Ansible using `pip3`.
* Installed a specific Ansible version.
* Ensured global access to Ansible commands.
* Verified installation successfully.
* Understood Ansible's role in infrastructure automation.

---

## 🚀 Skills Practiced

* Linux Administration
* Python Package Management
* Ansible Installation
* Infrastructure Automation
* Configuration Management
* DevOps Fundamentals

---

## 💡 Interview Questions

### Q1. What is Ansible?

Ansible is an open-source automation tool used for configuration management, provisioning, and application deployment.

---

### Q2. Why is Ansible called agentless?

Because it communicates with managed nodes using SSH and does not require additional software agents to be installed.

---

### Q3. What is pip3?

`pip3` is the package manager used to install Python 3 packages.

---

### Q4. How do you verify the installed Ansible version?

```bash
ansible --version
```

---

### Q5. Why would you install Ansible using pip3 instead of yum or apt?

Because pip3 allows installation of specific versions and often provides newer releases than OS repositories.

---

## 📌 Resources

* Ansible Documentation
* Python pip Documentation
* Linux SSH Documentation
* KodeKloud Labs

---

## ⭐ Day 008 Summary

Today's hands-on exercise introduced me to installing **Ansible 4.9.0** using **pip3** and making it globally accessible across the system. I learned how Python package management works, how to verify software installations, and why Ansible is one of the most important tools in modern DevOps environments for automating infrastructure and configuration management.
