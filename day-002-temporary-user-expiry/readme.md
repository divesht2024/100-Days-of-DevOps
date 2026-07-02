# 🚀 Day 002 – Temporary User Account with Expiry Date

## 📖 Overview

In today's lab, I learned how to create a **temporary Linux user account** with an **expiration date**. Account expiration is an important security feature that automatically disables a user account after a specified date, eliminating the need for manual account removal.

This practice is commonly used in enterprise environments for contractors, interns, consultants, vendors, and temporary employees who require system access only for a limited period.

---

## 🎯 Objective

- Create a temporary Linux user.
- Assign an account expiration date.
- Verify the account expiry configuration.
- Understand the importance of temporary accounts in Linux system administration.

---

## 🛠️ Environment

| Component | Details |
|-----------|---------|
| Operating System | Linux |
| Platform | KodeKloud |
| Category | Linux User Management |

---

## 📌 Task

Create a temporary user account with an expiration date so that the account is automatically disabled after the specified date.

---

## 💻 Commands Used

### Create a user with an expiry date

```bash
sudo useradd -e YYYY-MM-DD username
```

**Example**

```bash
sudo useradd -e 2026-12-31 john
```

---

### Verify account expiry

```bash
sudo chage -l john
```

Example Output

```text
Last password change                                    : Jul 02, 2026
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : Dec 31, 2026
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
```

---

### Display user information

```bash
id john
```

---

### View user entry

```bash
grep john /etc/passwd
```

---

## 📚 Concepts Learned

### What is a Temporary User?

A temporary user is a Linux account created for a limited period. Once the expiration date is reached, the operating system automatically disables the account, preventing the user from logging in.

---

### What is Account Expiry?

Account expiry is a security feature that disables a user account after a specified date.

Unlike deleting a user, the account still exists in the system but cannot be used for authentication.

---

### Password Expiry vs Account Expiry

| Password Expiry | Account Expiry |
|-----------------|----------------|
| Forces the user to change their password | Completely disables the user account |
| User can continue using the account after changing the password | User cannot log in after the expiry date |
| Configured using `chage` | Configured using `useradd -e` or `usermod -e` |

---

### Why Use Temporary Accounts?

Temporary accounts are commonly created for:

- Contractors
- Interns
- Consultants
- Third-party vendors
- Auditors
- Temporary project members
- Guest users

---

## 🌍 Real-World Use Case

Imagine a company hires a cybersecurity consultant for a **45-day security audit**.

The consultant requires access to Linux servers during the project.

Instead of manually remembering to disable the account after the engagement ends, the system administrator creates the account with an expiration date.

Once the project is complete, Linux automatically disables the account, ensuring the consultant no longer has access to the infrastructure. This reduces security risks and prevents unused accounts from remaining active.

---

## 🔍 Verification

Check account expiry information:

```bash
sudo chage -l john
```

Check user details:

```bash
id john
```

Verify user exists:

```bash
grep john /etc/passwd
```

---

## 🔐 Security Benefits

- Automatically disables unused accounts.
- Prevents forgotten user accounts from remaining active.
- Reduces the attack surface.
- Supports the Principle of Least Privilege (PoLP).
- Helps organizations meet security and compliance requirements.
- Eliminates manual account cleanup.

---

## 🧠 Key Takeaways

- Learned how to create temporary Linux users.
- Understood how account expiration works.
- Learned to verify account expiry using the `chage` command.
- Understood the difference between password expiry and account expiry.
- Learned why temporary accounts are widely used in enterprise environments.
- Improved understanding of Linux user administration and security best practices.

---

## 🚀 Skills Practiced

- Linux User Management
- Linux Administration
- User Account Creation
- Account Expiration Management
- Linux Security
- System Administration

---

## 📂 Project Structure

```text
day-002-temporary-user-expiry/
│── README.md
```


## 📖 Commands Reference

| Command | Purpose |
|----------|---------|
| `useradd -e` | Create a user with an account expiry date |
| `usermod -e` | Modify an existing user's expiry date |
| `chage -l` | Display password and account aging information |
| `id` | Display user and group information |
| `grep /etc/passwd` | Verify that the user exists |

---

## 📌 Resources

- Linux `useradd` Command
- Linux `usermod` Command
- Linux `chage` Command
- `/etc/passwd`
- `/etc/shadow`
- KodeKloud Linux Labs

---

## ⭐ Day 002 Summary

Today's exercise introduced me to **account expiration management in Linux**, an essential system administration and security practice. I learned how to create temporary user accounts, configure automatic account expiration, and verify the settings using Linux administration commands.

Using account expiry helps organizations automatically revoke access for temporary users such as contractors, interns, consultants, and vendors, reducing security risks and ensuring better access control in production environments.
