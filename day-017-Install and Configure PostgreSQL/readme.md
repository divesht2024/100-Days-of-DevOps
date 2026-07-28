
# 🚀 Day 017 – Install and Configure PostgreSQL

## 📖 Overview

Today, I learned how to install and configure **PostgreSQL**, an open-source relational database management system widely used in modern applications. PostgreSQL provides reliable data storage, powerful SQL capabilities, and advanced features required for production workloads.

This hands-on exercise improved my understanding of database installation, user management, security configuration, and application database connectivity.

---

# 🎯 Objective

* Install PostgreSQL database server.
* Configure PostgreSQL service.
* Create databases and users.
* Manage database permissions.
* Verify database connectivity.
* Understand PostgreSQL administration basics.

---

# 🛠️ Environment

| Component    | Details                    |
| ------------ | -------------------------- |
| Platform     | Linux (CentOS/RHEL/Ubuntu) |
| Database     | PostgreSQL                 |
| Service      | PostgreSQL Server          |
| Default Port | 5432                       |
| Category     | Database Administration    |

---

# 📌 Task

Install and configure PostgreSQL on a Linux server and prepare it for application usage.

---

# 💻 Steps Performed

## 1️⃣ Install PostgreSQL

### CentOS/RHEL:

Install PostgreSQL packages:

```bash id="8z1d2x"
sudo dnf install postgresql-server postgresql-contrib -y
```

Initialize database:

```bash id="9q3x4p"
sudo postgresql-setup --initdb
```

---

### Ubuntu:

```bash id="0f4d7m"
sudo apt update
sudo apt install postgresql postgresql-contrib -y
```

---

# 2️⃣ Start PostgreSQL Service

Enable PostgreSQL at boot:

```bash id="5d8h2k"
sudo systemctl enable postgresql
```

Start service:

```bash id="q7m3vz"
sudo systemctl start postgresql
```

Check status:

```bash id="j9w2pc"
sudo systemctl status postgresql
```

---

# 3️⃣ Access PostgreSQL Database

Switch to PostgreSQL user:

```bash id="r6x8nk"
sudo -i -u postgres
```

Open PostgreSQL shell:

```bash id="t4m8ws"
psql
```

---

# 4️⃣ Create Database

Create a database:

```sql id="x2c7mv"
CREATE DATABASE devops_db;
```

Verify databases:

```sql id="k8p1ds"
\l
```

---

# 5️⃣ Create Database User

Create user:

```sql id="v3m9qy"
CREATE USER devops_user WITH PASSWORD 'password';
```

---

# 6️⃣ Grant Permissions

Assign database ownership:

```sql id="p6n2bx"
ALTER DATABASE devops_db OWNER TO devops_user;
```

Grant privileges:

```sql id="z7h4cw"
GRANT ALL PRIVILEGES ON DATABASE devops_db TO devops_user;
```

---

# 7️⃣ Configure Remote Access

Edit PostgreSQL configuration:

```bash id="m4q8ys"
sudo vi /var/lib/pgsql/data/postgresql.conf
```

Change:

```conf
listen_addresses = '*'
```

---

Edit client authentication:

```bash id="r2k9vw"
sudo vi /var/lib/pgsql/data/pg_hba.conf
```

Add:

```conf
host    all    all    0.0.0.0/0    md5
```

---

Restart PostgreSQL:

```bash id="h6c3dz"
sudo systemctl restart postgresql
```

---

# 8️⃣ Verify PostgreSQL Connection

Connect locally:

```bash id="n7x5qp"
psql -U devops_user -d devops_db
```

Check PostgreSQL version:

```sql id="b4m8kj"
SELECT version();
```

---

# 📚 Concepts Learned

## What is PostgreSQL?

PostgreSQL is an open-source object-relational database management system used for storing and managing structured data.

---

## PostgreSQL Architecture

```text id="g4w9hx"
                Client Application
                       |
                       |
                  PostgreSQL
                       |
              -----------------
              |               |
          Query Parser     Storage Engine
              |
          Database Files
```

---

# PostgreSQL Components

| Component | Purpose                    |
| --------- | -------------------------- |
| Database  | Collection of related data |
| Table     | Stores structured records  |
| Schema    | Logical database structure |
| User      | Database access identity   |
| Role      | Permission management      |
| Query     | SQL operation              |

---

# Common PostgreSQL Commands

Connect to database:

```bash id="w3q8nm"
psql -U username -d database_name
```

List databases:

```sql id="c5k2zr"
\l
```

List tables:

```sql id="x9v6qp"
\dt
```

Show current user:

```sql id="m8f3kx"
SELECT current_user;
```

Exit PostgreSQL:

```sql id="e2n7vz"
\q
```

---

# 🌍 Real-World Use Case

A web application requires a reliable database backend.

A DevOps engineer:

* Installs PostgreSQL on a database server.
* Creates application-specific users.
* Configures secure authentication.
* Provides database access to application teams.
* Monitors database availability.

PostgreSQL is commonly used with applications built using Java, Python, Node.js, and .NET.

---

# 🔍 Verification

Verify:

✅ PostgreSQL package installed
✅ PostgreSQL service is running
✅ Database created successfully
✅ User permissions configured
✅ Application user can connect
✅ Port 5432 is listening

Check port:

```bash id="y6t2qp"
ss -tulnp | grep 5432
```

---

# 🔐 Best Practices

* Do not use the default `postgres` user for applications.
* Use strong database passwords.
* Restrict remote access using firewall rules.
* Enable SSL connections for production.
* Take regular database backups.
* Apply least privilege access.
* Monitor database performance.

---

# 🧠 Key Takeaways

* Installed and configured PostgreSQL.
* Learned database and user management.
* Configured authentication settings.
* Understood PostgreSQL administration basics.
* Improved database management skills required for DevOps roles.

---

# 🚀 Skills Practiced

* PostgreSQL
* Linux Administration
* Database Management
* User & Permission Management
* SQL Basics
* Application Database Configuration

---

# 💡 Interview Questions

### Q1. What is PostgreSQL?

PostgreSQL is an open-source relational database management system used for storing and managing structured data.

---

### Q2. What is the default PostgreSQL port?

```text
5432
```

---

### Q3. How do you check PostgreSQL service status?

```bash
systemctl status postgresql
```

---

### Q4. Difference between PostgreSQL and MySQL?

| PostgreSQL                 | MySQL                            |
| -------------------------- | -------------------------------- |
| Object-relational database | Relational database              |
| Advanced SQL features      | Simple and fast                  |
| Strong ACID compliance     | Widely used for web applications |
| Supports complex queries   | Easier administration            |

---

### Q5. How do you allow remote PostgreSQL connections?

Modify:

```text
postgresql.conf
```

and:

```text
pg_hba.conf
```

Then restart PostgreSQL service.

---

# 📌 Resources

* PostgreSQL Documentation
* Linux Database Administration Guide
* SQL Reference Documentation

---

# ⭐ Day 017 Summary

Today's hands-on exercise focused on **installing and configuring PostgreSQL**. I learned how to deploy a PostgreSQL database server, create databases and users, manage permissions, configure connectivity, and apply security practices. These skills are valuable for DevOps engineers managing application infrastructure and database environments.
