# 🚀 Day 004 – Script Execution Permissions

## 📖 Overview

Today, I learned how to manage **file permissions** in Linux by making a shell script executable using the `chmod` command. File permissions are a fundamental part of Linux security, controlling who can read, write, and execute files.

In this lab, I granted execute permissions to a script so that all users on the system could run it.

---

## 🎯 Objective

- Understand Linux file permissions.
- Learn how to use the `chmod` command.
- Grant execute permission to a shell script.
- Verify the updated file permissions.
- Understand the importance of executable permissions in Linux.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Operating System | Linux |
| Platform | KodeKloud |
| Category | Linux File Permissions |

---

## 📌 Task

Grant executable permissions to the script located at:

```text
/tmp/xfusioncorp.sh
```

Ensure that **all users** have permission to execute the script.

---

## 💻 Commands Used

### Check Current Permissions

```bash
ls -l /tmp/xfusioncorp.sh
```

---

### Grant Execute Permission

```bash
chmod 755 /tmp/xfusioncorp.sh
```

---

### Verify Permissions

```bash
ls -l /tmp/xfusioncorp.sh
```

Example Output

```text
-rwxr-xr-x 1 root root 120 Jul 4 10:30 /tmp/xfusioncorp.sh
```

---

## 📚 Concepts Learned

### What is `chmod`?

The `chmod` (Change Mode) command is used to modify file and directory permissions in Linux.

It controls who can:

- Read (`r`)
- Write (`w`)
- Execute (`x`)

---

### Understanding Linux File Permissions

Each file has permissions for three categories of users:

| User Type | Description |
|-----------|-------------|
| Owner (u) | The user who owns the file |
| Group (g) | Members of the file's group |
| Others (o) | Everyone else |

Permission symbols:

| Permission | Symbol | Value |
|------------|--------|------:|
| Read | `r` | 4 |
| Write | `w` | 2 |
| Execute | `x` | 1 |

---

### Understanding `chmod 755`

The numeric mode `755` is calculated as follows:

| User | Calculation | Permission |
|------|-------------|------------|
| Owner | 4 + 2 + 1 = 7 | Read, Write, Execute (`rwx`) |
| Group | 4 + 1 = 5 | Read, Execute (`r-x`) |
| Others | 4 + 1 = 5 | Read, Execute (`r-x`) |

Result:

```text
rwxr-xr-x
```

Meaning:

- Owner can read, write, and execute.
- Group can read and execute.
- Others can read and execute.

---

### Why Execute Permission is Important

Without execute permission:

- A shell script cannot be run directly.
- Users receive a **Permission denied** error.

With execute permission:

```bash
./xfusioncorp.sh
```

The operating system recognizes the file as an executable script.

---

## 🌍 Real-World Use Case

Imagine a DevOps team creates a deployment script that automates application deployment across multiple servers.

To allow all team members to run the script while preventing unauthorized modifications, the administrator assigns:

```bash
chmod 755 deploy.sh
```

This allows everyone to execute the script, while only the owner can modify it.

---

## 🔍 Verification

Check file permissions:

```bash
ls -l /tmp/xfusioncorp.sh
```

Execute the script:

```bash
/tmp/xfusioncorp.sh
```

Verify that all users have execute permission.

---

## 🔐 Security Best Practices

- Grant only the permissions that are necessary.
- Avoid using `chmod 777`, as it gives full access to everyone.
- Use `755` for scripts that need to be executable by multiple users.
- Restrict write permissions to the file owner whenever possible.
- Regularly review file permissions on production servers.

---

## 🧠 Key Takeaways

- Learned how Linux file permissions work.
- Understood the purpose of the `chmod` command.
- Learned how to grant execute permissions using `chmod 755`.
- Understood the difference between read, write, and execute permissions.
- Learned why executable permissions are essential for shell scripts.
- Improved understanding of Linux security and access control.

---

## 🚀 Skills Practiced

- Linux Administration
- File Permissions
- Linux Security
- Shell Scripting
- Command-Line Operations
- System Administration

---

## 📂 Project Structure

```text
day-004-script-execution-permissions/
│── README.md
```

## 📖 Commands Reference

| Command | Purpose |
|----------|---------|
| `ls -l` | View file permissions |
| `chmod 755 file` | Grant execute permission while keeping write access only for the owner |
| `./script.sh` | Execute the script |
| `stat file` | Display detailed file information |

---

## 💡 Interview Questions

### Q1. What does `chmod` do?

`chmod` changes the permissions of files and directories in Linux.

---

### Q2. What does `chmod 755` mean?

It gives the owner read, write, and execute permissions, while the group and others receive read and execute permissions.

---

### Q3. What do the numbers 7, 5, and 5 represent?

- **7 = 4 + 2 + 1** → Read, Write, Execute
- **5 = 4 + 1** → Read, Execute
- **5 = 4 + 1** → Read, Execute

---

### Q4. Why is execute permission required?

Without execute permission, a script or executable file cannot be run directly by the operating system.

---

### Q5. Why is `chmod 777` generally discouraged?

Because it grants read, write, and execute permissions to everyone, increasing the risk of accidental changes or unauthorized access.

---

## 📌 Resources

- Linux `chmod` Manual (`man chmod`)
- Linux File Permissions Documentation
- KodeKloud Linux Labs
- GNU Core Utilities Documentation

---

## ⭐ Day 004 Summary

Today's hands-on exercise helped me understand how Linux manages **file permissions** and why they are crucial for system security. I learned how to use the `chmod` command to grant execute permissions, interpret numeric permission values like `755`, and verify permission changes. These concepts are fundamental for Linux administration, shell scripting, and DevOps automation.
