
✅ Part 1: Exact KodeKloud Lab Guidelines (Exam-Safe Mode)
🔑 Step 0: Login to Application Server 2

From the jump host:

ssh steve@stapp02


Password:

Am3ric@

📂 Step 1: Copy the file into the container

```
docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src/
```

🔍 Step 2: Verify inside the container (MANDATORY)

```
docker exec ubuntu_latest ls -l /usr/src/
```

Expected result

File nautilus.txt.gpg is present in /usr/src/

File name and size match (no modification)

⚠️ Common Lab Mistakes to Avoid

❌ Copying from container to host (wrong direction)

❌ Wrong container name (ubuntu_latest must match exactly)

❌ Wrong destination path

❌ Using scp or rsync instead of docker cp



🧠 Part 2: Simple Step-by-Step Explanation (Beginner Friendly)
🪜 What are we doing?

The encrypted file already exists on the Docker host

We use Docker’s built-in copy command

Docker copies the file byte-for-byte (no changes)

🔍 Command Breakdown
docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src/


docker cp → copy files between host and container

/tmp/nautilus.txt.gpg → source file on host

ubuntu_latest: → target container

/usr/src/ → destination directory inside container

👉 This preserves the file exactly as-is.

🧠 Exam Memory Hook

docker cp = safe, direct, no modification

Always verify with:

docker exec <container> ls <path>

---
