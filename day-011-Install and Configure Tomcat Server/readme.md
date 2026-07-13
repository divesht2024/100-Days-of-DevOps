# 🚀 Day 011 – Install and Configure Apache Tomcat Server

## 📖 Overview

Today, I learned how to install and configure **Apache Tomcat**, one of the most popular Java application servers used to deploy Java web applications.

In this hands-on exercise, I installed Tomcat, configured its service, modified server settings, and deployed a sample Java application. This task helped me understand Java application hosting and web server management in Linux environments.

---

## 🎯 Objective

* Install Apache Tomcat on a Linux server.
* Configure Tomcat service and ports.
* Deploy a Java web application.
* Verify application accessibility.
* Learn production deployment concepts.

---

## 🛠️ Environment

| Component          | Details                       |
| ------------------ | ----------------------------- |
| Operating System   | Linux                         |
| Application Server | Apache Tomcat                 |
| Runtime            | Java (JDK)                    |
| Deployment Type    | WAR File Deployment           |
| Category           | Application Server Management |

---

## 📌 Task

Install and configure Apache Tomcat server and deploy a Java web application.

---

## 💻 Steps Performed

### 1. Install Java

Verify Java installation:

```bash
java -version
```

If Java is not installed:

```bash
sudo yum install java-11-openjdk -y
```

---

### 2. Install Tomcat

```bash
sudo yum install tomcat -y
```

---

### 3. Start and Enable Tomcat Service

```bash
sudo systemctl start tomcat
sudo systemctl enable tomcat
```

Verify status:

```bash
systemctl status tomcat
```

---

### 4. Configure Tomcat Port

Edit configuration:

```bash
sudo vi /etc/tomcat/server.xml
```

Example:

```xml
<Connector port="8080" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />
```

Change the port if required.

---

### 5. Deploy Application

Copy the WAR file:

```bash
sudo cp ROOT.war /var/lib/tomcat/webapps/
```

Restart Tomcat:

```bash
sudo systemctl restart tomcat
```

---

### 6. Verify Deployment

Check deployed applications:

```bash
ls /var/lib/tomcat/webapps/
```

Verify service:

```bash
curl http://localhost:8080
```

---

## 📚 Concepts Learned

### What is Apache Tomcat?

Apache Tomcat is an open-source Java Servlet container that runs Java web applications.

It supports:

* Java Servlets
* JSP (Java Server Pages)
* Java Web Applications (.war files)

---

### What is a WAR File?

A WAR (Web Application Archive) file contains:

* Java classes
* JSP files
* Configuration files
* Static web resources

Tomcat automatically extracts and deploys WAR files placed in the `webapps` directory.

---

### Tomcat Directory Structure

| Directory  | Purpose                 |
| ---------- | ----------------------- |
| `bin/`     | Startup scripts         |
| `conf/`    | Configuration files     |
| `logs/`    | Server logs             |
| `webapps/` | Application deployments |
| `temp/`    | Temporary files         |

---

## 🌍 Real-World Use Case

A company develops an internal HR management application using Java Spring Boot.

The DevOps team:

* Installs Tomcat on production servers.
* Deploys the WAR file.
* Configures application ports.
* Monitors logs and service health.

This provides a reliable platform for hosting enterprise Java applications.

---

## 🔍 Verification

Verify Tomcat service:

```bash
systemctl status tomcat
```

Expected output:

```text
Active: active (running)
```

Verify listening port:

```bash
ss -tulpn | grep 8080
```

Expected output:

```text
LISTEN 0 128 *:8080 *:*
```

Test application:

```bash
curl http://localhost:8080
```

---

## 🔐 Best Practices

* Use a reverse proxy such as Nginx in production.
* Change default ports when necessary.
* Secure the Tomcat Manager application.
* Regularly update Java and Tomcat versions.
* Monitor logs for errors and performance issues.

---

## 🧠 Key Takeaways

* Learned how to install Apache Tomcat.
* Understood Java web application deployment.
* Configured Tomcat services and ports.
* Practiced Linux service management.
* Improved troubleshooting skills for application servers.

---

## 🚀 Skills Practiced

* Linux Administration
* Apache Tomcat
* Java Application Deployment
* Systemd Services
* Web Server Management
* Application Troubleshooting






---

## 💡 Interview Questions

### Q1. What is Apache Tomcat?

Apache Tomcat is an open-source Java application server used to run Java web applications.

---

### Q2. What is a WAR file?

A WAR file is a packaged Java web application archive used for deployment.

---

### Q3. Which directory contains deployed applications in Tomcat?

```text
/var/lib/tomcat/webapps/
```

---

### Q4. Which file contains Tomcat port configuration?

```text
server.xml
```

---

### Q5. Which command checks Tomcat service status?

```bash
systemctl status tomcat
```

---

## ⭐ Day 011 Summary

Today's challenge introduced me to Apache Tomcat installation and configuration. I learned how Java web applications are deployed using WAR files, how to manage Tomcat services, and how application servers fit into real-world production environments.
