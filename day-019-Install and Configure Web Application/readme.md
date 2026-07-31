
# 🚀 Day 019 – Install and Configure Web Application

## 📖 Overview

Today, I learned how to install, deploy, and configure a **Java-based web application** on an **Apache Tomcat** server. Web applications are the core of many enterprise systems, and deploying them correctly is a fundamental DevOps responsibility.

This hands-on exercise improved my understanding of application deployment, Tomcat administration, service management, and application verification.

---

# 🎯 Objective

* Install Apache Tomcat.
* Configure the Tomcat service.
* Deploy a web application (`.war` file).
* Verify successful deployment.
* Understand the web application deployment lifecycle.

---

# 🛠️ Environment

| Component          | Details                    |
| ------------------ | -------------------------- |
| Platform           | Linux (CentOS/RHEL/Ubuntu) |
| Application Server | Apache Tomcat              |
| Application Type   | Java Web Application       |
| Package            | WAR File                   |
| Default Port       | 8080 (Configurable)        |
| Category           | Application Deployment     |

---

# 📌 Task

Install Apache Tomcat on a Linux server, deploy a Java web application (`ROOT.war` or any `.war` file), start the service, and verify that the application is accessible from a web browser.

---

# 💻 Steps Performed

## 1️⃣ Install Apache Tomcat

### CentOS / RHEL

```bash id="wa001"
sudo dnf install tomcat tomcat-webapps tomcat-admin-webapps -y
```

### Ubuntu

```bash id="wa002"
sudo apt update
sudo apt install tomcat9 -y
```

---

## 2️⃣ Start and Enable Tomcat

```bash id="wa003"
sudo systemctl enable tomcat
sudo systemctl start tomcat
```

Check service status:

```bash id="wa004"
sudo systemctl status tomcat
```

---

## 3️⃣ Verify Default Port

Tomcat listens on port **8080** by default.

Verify:

```bash id="wa005"
ss -tulnp | grep 8080
```

If required, edit:

```text id="wa006"
/etc/tomcat/server.xml
```

or

```text id="wa007"
/var/lib/tomcat/conf/server.xml
```

Change:

```xml id="wa008"
<Connector port="8080" protocol="HTTP/1.1" />
```

Restart Tomcat:

```bash id="wa009"
sudo systemctl restart tomcat
```

---

## 4️⃣ Deploy the Web Application

Copy the WAR file:

```bash id="wa010"
sudo cp ROOT.war /var/lib/tomcat/webapps/
```

or

```bash id="wa011"
sudo cp sample.war /var/lib/tomcat/webapps/
```

Tomcat automatically extracts the WAR file.

---

## 5️⃣ Verify Deployment

List deployed applications:

```bash id="wa012"
ls -l /var/lib/tomcat/webapps/
```

Example:

```text id="wa013"
ROOT/
ROOT.war
docs/
examples/
manager/
```

---

## 6️⃣ Access the Application

Using a browser:

```text id="wa014"
http://<SERVER-IP>:8080/
```

Or using curl:

```bash id="wa015"
curl http://localhost:8080
```

Expected output:

```html id="wa016"
Welcome to My Java Web Application
```

---

# 📚 Concepts Learned

## What is Apache Tomcat?

Apache Tomcat is an open-source Java Servlet container used to run Java web applications.

---

## What is a WAR File?

A **WAR (Web Application Archive)** file is a packaged Java web application that contains:

* HTML
* JSP
* Servlets
* Libraries
* Configuration files
* Static resources

---

## Web Application Deployment Flow

```text id="wa017"
        Developer
            |
       Build Application
            |
         WAR File
            |
     Apache Tomcat Server
            |
     Deploy Application
            |
        End Users
```

---

## Tomcat Directory Structure

| Directory               | Purpose                   |
| ----------------------- | ------------------------- |
| /var/lib/tomcat/webapps | Deployed applications     |
| /etc/tomcat             | Configuration files       |
| /var/log/tomcat         | Log files                 |
| server.xml              | Main server configuration |

---

# 🌍 Real-World Use Case

A development team builds a Java-based e-commerce application.

The DevOps engineer:

* Installs Apache Tomcat.
* Deploys the generated WAR file.
* Starts the application server.
* Verifies successful deployment.
* Monitors logs and application health.

Whenever a new version is released, the WAR file is updated and redeployed.

---

# 🔍 Verification

Verify:

✅ Tomcat installed successfully.
✅ Tomcat service is running.
✅ WAR file deployed.
✅ Application extracted automatically.
✅ Web application accessible.
✅ Correct port is listening.

Useful commands:

```bash id="wa018"
systemctl status tomcat
```

```bash id="wa019"
ss -tulnp | grep 8080
```

```bash id="wa020"
curl http://localhost:8080
```

---

# 🔐 Best Practices

* Use non-root users for application services.
* Keep Tomcat updated with security patches.
* Restrict access to Tomcat Manager in production.
* Remove unused sample applications.
* Configure HTTPS using SSL/TLS.
* Monitor Tomcat logs regularly.
* Deploy applications through CI/CD pipelines.

---

# 🧠 Key Takeaways

* Installed Apache Tomcat.
* Configured the application server.
* Deployed a Java web application.
* Verified application availability.
* Learned the Java web deployment lifecycle.

---

# 🚀 Skills Practiced

* Apache Tomcat
* Java Web Applications
* Linux Administration
* WAR Deployment
* Service Management
* Application Hosting
---

# 💡 Interview Questions

### Q1. What is Apache Tomcat?

Apache Tomcat is an open-source application server that runs Java Servlets and JavaServer Pages (JSP).

---

### Q2. What is a WAR file?

A WAR (Web Application Archive) file is a packaged Java web application that contains application code, libraries, and configuration files.

---

### Q3. Where should a WAR file be placed for deployment?

```text id="wa022"
/var/lib/tomcat/webapps/
```

Tomcat automatically deploys and extracts the WAR file placed in this directory.

---

### Q4. How do you check the status of the Tomcat service?

```bash id="wa023"
systemctl status tomcat
```

---

### Q5. How can you verify that the web application is running?

Use a web browser or:

```bash id="wa024"
curl http://localhost:8080
```

If configured on another port, replace `8080` with the appropriate port number.

---

# 📌 Resources

* Apache Tomcat Documentation
* Java Servlet Specification
* Linux System Administration Guide
* Oracle Java Documentation

---

# ⭐ Day 019 Summary

Today's hands-on exercise focused on **installing and configuring a Java web application using Apache Tomcat**. I learned how to install and manage Tomcat, deploy WAR files, configure the application server, verify successful deployment, and understand the complete Java web application deployment lifecycle. These skills are essential for DevOps engineers managing Java-based enterprise applications.
