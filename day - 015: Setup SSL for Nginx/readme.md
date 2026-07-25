
# 🚀 Day 015 – Setup SSL for Nginx

## 📖 Overview

Today, I learned how to secure an **Nginx web server** by configuring **SSL/TLS encryption**. SSL certificates encrypt communication between clients and servers, ensuring secure data transmission and protecting sensitive information from interception.

This hands-on exercise improved my understanding of HTTPS, SSL certificates, Nginx configuration, and Linux web server security.

---

# 🎯 Objective

* Install and configure Nginx.
* Generate or use an SSL certificate.
* Configure HTTPS on Nginx.
* Redirect HTTP traffic to HTTPS.
* Verify secure communication.

---

# 🛠️ Environment

| Component  | Details                                    |
| ---------- | ------------------------------------------ |
| Platform   | Linux (CentOS/RHEL/Ubuntu)                 |
| Web Server | Nginx                                      |
| Protocol   | HTTPS                                      |
| SSL/TLS    | OpenSSL                                    |
| Category   | Linux Security & Web Server Administration |

---

# 📌 Task

Configure SSL/TLS on an Nginx web server so that users can securely access the website over HTTPS.

---

# 💻 Steps Performed

## 1️⃣ Install Nginx

For CentOS/RHEL:

```bash id="mfh3d2"
sudo dnf install nginx -y
```

For Ubuntu:

```bash id="2fszzq"
sudo apt install nginx -y
```

Start and enable Nginx:

```bash id="9z5mxm"
sudo systemctl enable nginx
sudo systemctl start nginx
```

---

## 2️⃣ Generate a Self-Signed SSL Certificate

Create a certificate and private key:

```bash id="74r9j6"
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /etc/nginx/server.key \
-out /etc/nginx/server.crt
```

Provide the requested certificate details when prompted.

---

## 3️⃣ Configure Nginx for HTTPS

Edit the Nginx configuration file:

```bash id="bmgjxu"
sudo vi /etc/nginx/nginx.conf
```

or create a server block under:

```text id="r4zc2h"
/etc/nginx/conf.d/default.conf
```

Example configuration:

```nginx id="s0uwqh"
server {
    listen 443 ssl;
    server_name localhost;

    ssl_certificate /etc/nginx/server.crt;
    ssl_certificate_key /etc/nginx/server.key;

    location / {
        root /usr/share/nginx/html;
        index index.html;
    }
}
```

---

## 4️⃣ Redirect HTTP to HTTPS

Add another server block:

```nginx id="kt3tv4"
server {
    listen 80;
    server_name localhost;
    return 301 https://$host$request_uri;
}
```

---

## 5️⃣ Test the Configuration

Verify Nginx syntax:

```bash id="twitmb"
sudo nginx -t
```

If successful:

```text id="e8mhyq"
syntax is ok
test is successful
```

---

## 6️⃣ Restart Nginx

```bash id="cjlwmz"
sudo systemctl restart nginx
```

---

## 7️⃣ Verify HTTPS

Using a browser:

```text id="s1rkca"
https://<server-ip>
```

Or using curl:

```bash id="9vzj9w"
curl -k https://localhost
```

The `-k` option ignores certificate validation for self-signed certificates.

---

# 📚 Concepts Learned

## What is SSL/TLS?

SSL (Secure Sockets Layer) and its successor TLS (Transport Layer Security) encrypt communication between a client and a server, ensuring confidentiality and integrity.

---

## What is HTTPS?

HTTPS (Hypertext Transfer Protocol Secure) is HTTP running over SSL/TLS encryption, protecting data exchanged between users and web servers.

---

## SSL Handshake

```text id="v5e5t8"
Client
   |
   | HTTPS Request
   ↓
Nginx Server
   |
   | Sends SSL Certificate
   ↓
Certificate Validation
   |
   ↓
Encrypted Connection Established
```

---

## Self-Signed vs CA-Signed Certificates

| Self-Signed Certificate | CA-Signed Certificate                     |
| ----------------------- | ----------------------------------------- |
| Generated locally       | Issued by a trusted Certificate Authority |
| Suitable for testing    | Recommended for production                |
| Browser shows a warning | Trusted by browsers                       |

---

# 🌍 Real-World Use Case

A company hosts its web application on an Nginx server.

To secure user login credentials and sensitive data:

* SSL certificates are installed.
* HTTP traffic is redirected to HTTPS.
* All communication is encrypted.

This ensures secure access and builds user trust.

---

# 🔍 Verification

Verify that:

* Nginx service is running.
* SSL certificate is configured.
* HTTPS is accessible.
* HTTP requests redirect to HTTPS.
* Nginx configuration passes validation.

---

# 🔐 Best Practices

* Use CA-signed certificates in production.
* Redirect all HTTP traffic to HTTPS.
* Disable outdated SSL/TLS versions.
* Renew certificates before expiration.
* Protect private key files with appropriate permissions.

---

# 🧠 Key Takeaways

* Learned SSL/TLS fundamentals.
* Configured HTTPS on Nginx.
* Generated and used SSL certificates.
* Redirected HTTP traffic securely.
* Improved Linux web server security skills.

---

# 🚀 Skills Practiced

* Linux Administration
* Nginx
* SSL/TLS
* HTTPS
* OpenSSL
* Web Server Security

---

# 💡 Interview Questions

### Q1. What is the purpose of SSL/TLS?

SSL/TLS encrypts communication between clients and servers, ensuring secure data transmission.

---

### Q2. What is the default port for HTTPS?

```text id="tzr5r4"
443
```

---

### Q3. What command verifies the Nginx configuration?

```bash id="cr1dfq"
sudo nginx -t
```

---

### Q4. What is the difference between HTTP and HTTPS?

| HTTP        | HTTPS                   |
| ----------- | ----------------------- |
| Unencrypted | Encrypted using SSL/TLS |
| Port 80     | Port 443                |
| Less secure | Secure communication    |

---

### Q5. Why are CA-signed certificates preferred in production?

Because they are trusted by browsers and provide verified identity, eliminating browser security warnings.

---

# 📌 Resources

* Nginx Documentation
* OpenSSL Documentation
* Let's Encrypt Documentation
* Linux System Administration Guide

---

# ⭐ Day 015 Summary

Today's hands-on exercise focused on configuring **SSL/TLS for Nginx**. I learned how to generate SSL certificates, configure HTTPS, redirect HTTP traffic securely, and validate Nginx configurations. These are essential skills for deploying secure web applications and managing production web servers.
