
✅ Part 1: Exact KodeKloud Lab Guidelines (Exam-Safe Mode)
🔑 Step 0: Login to Application Server 1

From the jump host:
```
ssh tony@stapp01
# Password:
Ir0nM@n
```

📦 Step 1: Run nginx container (alpine tag)

```
docker run -d --name nginx_1 nginx:alpine
```

🔍 Step 2: Verify container state (MANDATORY)

```
docker ps
```

---

🧠 Part 2: Simple Step-by-Step Explanation (Beginner Friendly)
🪜 What are we doing?

We are:

Logging into Application Server 1

Creating a container

Making sure it keeps running

🔍 Command Breakdown
docker run -d --name nginx_1 nginx:alpine


docker run → create + start a container

-d → detached mode (runs in background)

--name nginx_1 → exact container name required by lab

nginx:alpine → nginx image, lightweight alpine version

If -d is missing → container may stop → lab fails.

🧠 Exam Memory Hook

Right server → Right name → Right image → Running

Always verify with:

docker ps

---
