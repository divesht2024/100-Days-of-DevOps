
# 🚀 Day 016 – Install and Configure Nginx as a Load Balancer

## 📖 Overview

Today, I learned how to install and configure **Nginx as a Load Balancer (LBR)** to distribute incoming client requests across multiple backend web servers. Load balancing improves application availability, scalability, and fault tolerance by preventing a single server from becoming overloaded.

This hands-on exercise enhanced my understanding of reverse proxies, load balancing algorithms, backend server pools, and high-availability web architectures.

---

# 🎯 Objective

* Install Nginx.
* Configure Nginx as a reverse proxy load balancer.
* Add multiple backend servers.
* Verify load balancing functionality.
* Understand real-world load balancing concepts.

---

# 🛠️ Environment

| Component  | Details                       |
| ---------- | ----------------------------- |
| Platform   | Linux (CentOS/RHEL/Ubuntu)    |
| Web Server | Nginx                         |
| Role       | Reverse Proxy & Load Balancer |
| Protocol   | HTTP                          |
| Category   | Web Server & Load Balancing   |

---

# 📌 Task

Install Nginx and configure it as a load balancer to distribute HTTP requests across multiple backend web servers.

---

# 💻 Steps Performed

## 1️⃣ Install Nginx

For CentOS/RHEL:

```bash
sudo dnf install nginx -y
```

For Ubuntu:

```bash
sudo apt update
sudo apt install nginx -y
```

Start and enable Nginx:

```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

Verify:

```bash
sudo systemctl status nginx
```

---

## 2️⃣ Configure Backend Servers

Assume two backend web servers:

| Server       | IP Address   |
| ------------ | ------------ |
| Web Server 1 | 192.168.1.10 |
| Web Server 2 | 192.168.1.11 |

Ensure both web servers are running and serving HTTP content.

---

## 3️⃣ Configure Nginx Load Balancer

Edit the configuration:

```bash
sudo vi /etc/nginx/nginx.conf
```

Example configuration:

```nginx
http {

    upstream backend_servers {
        server 192.168.1.10;
        server 192.168.1.11;
    }

    server {
        listen 80;

        location / {
            proxy_pass http://backend_servers;

            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
    }

}
```

---

## 4️⃣ Test Configuration

```bash
sudo nginx -t
```

Expected output:

```text
syntax is ok
test is successful
```

---

## 5️⃣ Restart Nginx

```bash
sudo systemctl restart nginx
```

---

## 6️⃣ Verify Load Balancing

Access the load balancer:

```text
http://<Load-Balancer-IP>
```

Or use:

```bash
curl http://<Load-Balancer-IP>
```

Multiple requests should be distributed across the configured backend servers.

---

# 📚 Concepts Learned

## What is a Load Balancer?

A Load Balancer distributes incoming client requests across multiple servers to improve availability, scalability, and performance.

---

## What is a Reverse Proxy?

A reverse proxy receives client requests and forwards them to one or more backend servers while hiding their internal details.

---

## Nginx Load Balancing Algorithms

| Algorithm         | Description                                                         |
| ----------------- | ------------------------------------------------------------------- |
| Round Robin       | Requests are distributed sequentially (default).                    |
| Least Connections | Sends requests to the server with the fewest active connections.    |
| IP Hash           | Routes requests from the same client IP to the same backend server. |

Example:

```nginx
upstream backend_servers {
    least_conn;

    server 192.168.1.10;
    server 192.168.1.11;
}
```

---

## Nginx Load Balancing Architecture

```text
               Client
                  |
                  |
            Nginx Load Balancer
                  |
        -------------------------
        |                       |
        |                       |
   Web Server 1           Web Server 2
   192.168.1.10           192.168.1.11
```

---

# 🌍 Real-World Use Case

An e-commerce website experiences high traffic during seasonal sales.

Instead of relying on a single web server:

* Nginx receives all incoming requests.
* Requests are distributed across multiple backend servers.
* If one backend server fails, traffic continues to be served by the remaining healthy servers.
* Users experience improved performance and reduced downtime.

---

# 🔍 Verification

Verify that:

* Nginx service is running.
* Configuration syntax is valid.
* Backend servers are reachable.
* Client requests are successfully forwarded.
* Traffic is distributed across backend servers.

---

# 🔐 Best Practices

* Use health checks to detect unavailable backend servers.
* Deploy backend servers behind a private network.
* Enable HTTPS for secure client communication.
* Monitor traffic and server health.
* Combine Nginx with Keepalived or cloud load balancers for high availability.

---

# 🧠 Key Takeaways

* Learned how to install and configure Nginx.
* Configured Nginx as a reverse proxy.
* Implemented load balancing across multiple backend servers.
* Understood load balancing algorithms.
* Improved Linux web server administration skills.

---

# 🚀 Skills Practiced

* Linux Administration
* Nginx
* Reverse Proxy
* Load Balancing
* HTTP
* High Availability

---

# 💡 Interview Questions

### Q1. What is the role of Nginx as a Load Balancer?

Nginx distributes incoming client requests across multiple backend servers to improve performance, scalability, and availability.

---

### Q2. What is the default load balancing algorithm used by Nginx?

The default algorithm is **Round Robin**, where requests are distributed sequentially across backend servers.

---

### Q3. What is an `upstream` block in Nginx?

An `upstream` block defines a group of backend servers that Nginx uses to forward client requests.

---

### Q4. What is the difference between a reverse proxy and a load balancer?

A reverse proxy forwards client requests to backend servers, while a load balancer distributes those requests across multiple backend servers for scalability and fault tolerance.

---

### Q5. Why are health checks important in load balancing?

Health checks detect unhealthy backend servers and prevent them from receiving client requests until they recover.

---

# 📌 Resources

* Nginx Documentation
* Nginx Load Balancing Guide
* Linux System Administration Guide
* High Availability Concepts

---

# ⭐ Day 016 Summary

Today's hands-on exercise focused on configuring **Nginx as a Load Balancer**. I learned how to install Nginx, configure upstream backend servers, distribute traffic using load balancing algorithms, and verify request routing. These skills are fundamental for building scalable, highly available, and production-ready web applications.
