
# 🚀 Day 020 – Configure Nginx + PHP-FPM Using Unix Socket

## 📖 Overview

Today, I learned how to configure **Nginx** to serve **PHP applications** using **PHP-FPM (FastCGI Process Manager)** over a **Unix Socket** instead of a TCP port. This is a common production setup because Unix sockets provide faster local communication and improved security when Nginx and PHP-FPM run on the same server.

This hands-on exercise strengthened my understanding of web servers, PHP-FPM, FastCGI, Unix sockets, and Linux service configuration.

---

# 🎯 Objective

* Install Nginx and PHP-FPM.
* Configure PHP-FPM to use a Unix socket.
* Configure Nginx to communicate with PHP-FPM.
* Deploy a sample PHP application.
* Verify PHP processing through Nginx.

---

# 🛠️ Environment

| Component         | Details                    |
| ----------------- | -------------------------- |
| Platform          | Linux (CentOS/RHEL/Ubuntu) |
| Web Server        | Nginx                      |
| PHP Processor     | PHP-FPM                    |
| Communication     | Unix Socket                |
| Default HTTP Port | 80                         |
| Category          | Web Server Configuration   |

---

# 📌 Task

Install Nginx and PHP-FPM, configure PHP-FPM to listen on a Unix socket, update the Nginx server configuration to use the socket, and verify that PHP pages are served correctly.

---

# 💻 Steps Performed

## 1️⃣ Install Nginx and PHP-FPM

### CentOS / RHEL

```bash id="ng001"
sudo dnf install nginx php-fpm php-cli -y
```

### Ubuntu

```bash id="ng002"
sudo apt update
sudo apt install nginx php-fpm php-cli -y
```

---

## 2️⃣ Start and Enable Services

```bash id="ng003"
sudo systemctl enable nginx
sudo systemctl enable php-fpm

sudo systemctl start nginx
sudo systemctl start php-fpm
```

Verify:

```bash id="ng004"
sudo systemctl status nginx
sudo systemctl status php-fpm
```

---

## 3️⃣ Configure PHP-FPM

Edit the PHP-FPM pool configuration.

### CentOS / RHEL

```text id="ng005"
/etc/php-fpm.d/www.conf
```

### Ubuntu

```text id="ng006"
/etc/php/8.x/fpm/pool.d/www.conf
```

Update the **listen** directive:

```ini id="ng007"
listen = /run/php-fpm/www.sock
```

Ensure the socket permissions are configured:

```ini id="ng008"
listen.owner = nginx
listen.group = nginx
listen.mode = 0660
```

> On Ubuntu, replace `nginx` with `www-data` if required.

Restart PHP-FPM:

```bash id="ng009"
sudo systemctl restart php-fpm
```

---

## 4️⃣ Configure Nginx

Edit the server configuration.

Example:

```text id="ng010"
/etc/nginx/conf.d/default.conf
```

or

```text id="ng011"
/etc/nginx/sites-available/default
```

Inside the PHP location block:

```nginx id="ng012"
location ~ \.php$ {
    include fastcgi_params;
    fastcgi_pass unix:/run/php-fpm/www.sock;
    fastcgi_index index.php;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
}
```

Test configuration:

```bash id="ng013"
sudo nginx -t
```

Restart Nginx:

```bash id="ng014"
sudo systemctl restart nginx
```

---

## 5️⃣ Deploy a Sample PHP Application

Create a PHP file:

```bash id="ng015"
sudo tee /usr/share/nginx/html/info.php
```

Content:

```php id="ng016"
<?php
phpinfo();
?>
```

---

## 6️⃣ Verify the Configuration

Open:

```text id="ng017"
http://<SERVER-IP>/info.php
```

Or use:

```bash id="ng018"
curl http://localhost/info.php
```

If the PHP information page is displayed, the configuration is successful.

---

# 📚 Concepts Learned

## What is PHP-FPM?

PHP-FPM (FastCGI Process Manager) is a PHP process manager that efficiently executes PHP scripts and communicates with web servers such as Nginx.

---

## What is FastCGI?

FastCGI is a protocol that enables communication between a web server and an application server, allowing dynamic content (such as PHP) to be processed efficiently.

---

## What is a Unix Socket?

A Unix socket is a special file used for communication between processes on the same machine. It avoids TCP/IP overhead and is commonly used for Nginx–PHP-FPM communication.

---

## Nginx + PHP-FPM Architecture

```text id="ng019"
          Client Browser
                 |
             HTTP Request
                 |
              Nginx Server
                 |
      Unix Socket (/run/php-fpm/www.sock)
                 |
             PHP-FPM Service
                 |
            PHP Application
```

---

# 🌍 Real-World Use Case

Many production environments host PHP applications such as WordPress, Laravel, Magento, and Drupal.

Instead of using TCP communication between Nginx and PHP-FPM, administrators configure a Unix socket because:

* It is faster for local communication.
* It reduces network overhead.
* It limits access to local processes only.
* It improves overall performance.

---

# 🔍 Verification

Verify:

✅ Nginx service is running.
✅ PHP-FPM service is running.
✅ Unix socket exists.
✅ Nginx configuration passes validation.
✅ PHP page loads successfully.

Useful commands:

```bash id="ng020"
systemctl status nginx
```

```bash id="ng021"
systemctl status php-fpm
```

```bash id="ng022"
ls -l /run/php-fpm/
```

```bash id="ng023"
nginx -t
```

---

# 🔐 Best Practices

* Use Unix sockets when Nginx and PHP-FPM run on the same server.
* Restrict socket permissions using appropriate ownership and mode.
* Disable unnecessary PHP functions in production.
* Keep Nginx and PHP packages updated.
* Enable HTTPS using SSL/TLS.
* Monitor Nginx and PHP-FPM logs for errors and performance.

---

# 🧠 Key Takeaways

* Installed and configured Nginx.
* Installed and configured PHP-FPM.
* Connected Nginx and PHP-FPM using a Unix socket.
* Deployed a PHP application.
* Verified dynamic PHP content delivery.

---

# 🚀 Skills Practiced

* Nginx Administration
* PHP-FPM Configuration
* FastCGI
* Unix Socket Configuration
* Linux Service Management
* Web Application Hosting

---

# 💡 Interview Questions

### Q1. What is PHP-FPM?

PHP-FPM (FastCGI Process Manager) is an implementation of FastCGI for PHP that manages PHP worker processes efficiently and improves application performance.

---

### Q2. Why use a Unix socket instead of TCP for PHP-FPM?

Unix sockets provide faster communication between Nginx and PHP-FPM on the same server because they avoid TCP/IP networking overhead. They also improve security by limiting communication to local processes.

---

### Q3. Where is the PHP-FPM socket typically located?

Common locations include:

```text id="ng025"
/run/php-fpm/www.sock
```

or

```text id="ng026"
/run/php/php8.x-fpm.sock
```

depending on the Linux distribution and PHP version.

---

### Q4. Which Nginx directive connects to PHP-FPM?

```nginx id="ng027"
fastcgi_pass unix:/run/php-fpm/www.sock;
```

---

### Q5. How do you test the Nginx configuration before restarting the service?

```bash id="ng028"
sudo nginx -t
```

This validates the configuration syntax and helps prevent service disruptions.

---

# 📌 Resources

* Nginx Documentation
* PHP-FPM Documentation
* FastCGI Specification
* Linux System Administration Guide

---

# ⭐ Day 020 Summary

Today's hands-on exercise focused on **configuring Nginx and PHP-FPM using a Unix socket**. I installed and configured both services, connected them using FastCGI over a Unix socket, deployed a sample PHP application, and verified successful execution. This setup is widely used in production environments because it offers improved performance, better security, and efficient local communication between the web server and the PHP application server.
