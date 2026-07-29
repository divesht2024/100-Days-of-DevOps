
# 🚀 Day 018 – Install and Configure Database Server

## 📖 Overview

Today, I learned how to install and configure a **Database Server** on Linux. A database server stores, manages, and retrieves application data efficiently and securely. In this hands-on exercise, I installed a database server, started the service, configured it for local and remote access, and verified database connectivity.

This task strengthened my understanding of database administration, Linux service management, networking, and security best practices.

---

# 🎯 Objective

* Install a database server.
* Start and enable the database service.
* Secure the database installation.
* Create a database and user.
* Configure remote access (if required).
* Verify database connectivity.

---

# 🛠️ Environment

| Component       | Details                    |
| --------------- | -------------------------- |
| Platform        | Linux (CentOS/RHEL/Ubuntu) |
| Database Server | MariaDB / MySQL            |
| Service         | mariadb                    |
| Default Port    | 3306                       |
| Category        | Database Administration    |

---

# 📌 Task

Install and configure a database server on Linux, create a sample database and user, and verify that the service is running correctly.

---

# 💻 Steps Performed

## 1️⃣ Install Database Server

### CentOS / RHEL

```bash id="k2f7md"
sudo dnf install mariadb-server -y
```

### Ubuntu

```bash id="q9x3wh"
sudo apt update
sudo apt install mariadb-server -y
```

---

## 2️⃣ Start and Enable the Service

```bash id="n4y8pk"
sudo systemctl enable mariadb
sudo systemctl start mariadb
```

Check status:

```bash id="w5r1qt"
sudo systemctl status mariadb
```

---

## 3️⃣ Secure the Installation

Run the security script:

```bash id="v2m8hs"
sudo mysql_secure_installation
```

Typical configuration:

* Set root password
* Remove anonymous users
* Disallow remote root login
* Remove test database
* Reload privilege tables

---

## 4️⃣ Login to the Database

```bash id="h3t9jk"
sudo mysql
```

or

```bash id="p6m4zc"
mysql -u root -p
```

---

## 5️⃣ Create a Database

```sql id="g8q5xr"
CREATE DATABASE devops_db;
```

Verify:

```sql id="d7w2la"
SHOW DATABASES;
```

---

## 6️⃣ Create a Database User

```sql id="r1n6by"
CREATE USER 'devops_user'@'localhost' IDENTIFIED BY 'StrongPassword';
```

Grant privileges:

```sql id="c4v9up"
GRANT ALL PRIVILEGES ON devops_db.* TO 'devops_user'@'localhost';
FLUSH PRIVILEGES;
```

---

## 7️⃣ Configure Remote Access (Optional)

Edit the configuration file:

```bash id="x8k1jq"
sudo vi /etc/my.cnf
```

or

```bash id="u2d7ml"
sudo vi /etc/mysql/mariadb.conf.d/50-server.cnf
```

Update:

```conf id="s3y5hn"
bind-address = 0.0.0.0
```

Restart the service:

```bash id="b9r6we"
sudo systemctl restart mariadb
```

---

## 8️⃣ Verify the Service

Check the listening port:

```bash id="m7z2xt"
ss -tulnp | grep 3306
```

Test login:

```bash id="j5n4kb"
mysql -u devops_user -p devops_db
```

---

# 📚 Concepts Learned

## What is a Database Server?

A database server is software that stores, organizes, and manages structured data for applications.

---

## What is MariaDB?

MariaDB is an open-source relational database management system (RDBMS) and a drop-in replacement for MySQL.

---

## Database Server Architecture

```text id="f6x3qn"
             Client Application
                    |
                    |
             Database Server
                    |
          --------------------
          |                  |
      Databases          User Accounts
                    |
                Data Storage
```

---

## Common Database Commands

Show databases:

```sql id="a8t4pr"
SHOW DATABASES;
```

Select a database:

```sql id="e1m7ws"
USE devops_db;
```

Show users:

```sql id="z9h2cv"
SELECT User, Host FROM mysql.user;
```

Exit:

```sql id="q7k5md"
EXIT;
```

---

# 🌍 Real-World Use Case

A web application requires a backend database to store user information, orders, and application data.

A DevOps engineer:

* Installs a database server.
* Creates application databases.
* Configures user permissions.
* Secures database access.
* Monitors service availability.

The application then connects securely to the database for all read and write operations.

---

# 🔍 Verification

Verify that:

✅ Database server is installed.
✅ Service is running.
✅ Port **3306** is listening.
✅ Database is created.
✅ User authentication works.
✅ Required privileges are granted.

Useful commands:

```bash id="t4v8px"
systemctl status mariadb
```

```bash id="l6j2rq"
ss -tulnp | grep 3306
```

```bash id="w8c5nt"
mysql -u root -p
```

---

# 🔐 Best Practices

* Use strong passwords for database users.
* Disable remote root login.
* Grant only necessary privileges.
* Restrict database access using firewall rules.
* Perform regular backups.
* Keep the database server updated.
* Monitor database logs and performance.

---

# 🧠 Key Takeaways

* Installed and configured a database server.
* Managed database services using systemd.
* Created databases and users.
* Configured authentication and permissions.
* Learned essential database administration tasks.

---

# 🚀 Skills Practiced

* Linux Administration
* MariaDB
* MySQL
* Database Management
* User & Permission Management
* Service Administration
---

# 💡 Interview Questions

### Q1. What is the default port used by MariaDB/MySQL?

**3306**

---

### Q2. How do you check if the MariaDB service is running?

```bash id="d3n8mw"
systemctl status mariadb
```

---

### Q3. What is the purpose of `mysql_secure_installation`?

It secures a new MariaDB/MySQL installation by setting a root password, removing anonymous users, disabling remote root login, removing the test database, and reloading privilege tables.

---

### Q4. How do you create a new database?

```sql id="v1r5qb"
CREATE DATABASE database_name;
```

---

### Q5. Why should applications avoid using the root database account?

Using dedicated application users with limited privileges improves security and follows the principle of least privilege.

---

# 📌 Resources

* MariaDB Documentation
* MySQL Documentation
* Linux System Administration Guide
* SQL Reference Documentation

---

# ⭐ Day 018 Summary

Today's hands-on exercise focused on **installing and configuring a database server** on Linux. I learned how to install MariaDB, manage the database service, secure the installation, create databases and users, configure permissions, and verify connectivity. These are essential skills for DevOps engineers responsible for deploying and maintaining application database infrastructure.
