# 🚀 Day 024 – Git: Create Branches

## 📖 Overview

Today, I learned how to **create and manage branches in Git**. Branching is one of Git's most powerful features, allowing developers to work on new features, bug fixes, or experiments without affecting the main codebase.

This hands-on exercise strengthened my understanding of Git branching strategies, branch management, and collaborative development workflows used in modern DevOps environments.

---

# 🎯 Objective

* Create new Git branches.
* Switch between branches.
* Verify the current branch.
* Understand branch isolation.
* Learn common Git branching workflows.

---

# 🛠️ Environment

| Component       | Details               |
| --------------- | --------------------- |
| Platform        | Linux / Windows       |
| Version Control | Git                   |
| Repository Type | Local Git Repository  |
| Category        | Git & Version Control |

---

# 📌 Task

Create one or more Git branches, switch between them, and verify that each branch provides an isolated workspace for development.

---

# 💻 Steps Performed

## 1️⃣ Navigate to the Repository

```bash id="git001"
cd my-project
```

Verify it is a Git repository:

```bash id="git002"
git status
```

---

## 2️⃣ Check Existing Branches

Display all local branches:

```bash id="git003"
git branch
```

Example output:

```text id="git004"
* main
```

---

## 3️⃣ Create a New Branch

Create a feature branch:

```bash id="git005"
git branch feature-login
```

Verify:

```bash id="git006"
git branch
```

Output:

```text id="git007"
* main
  feature-login
```

---

## 4️⃣ Switch to the New Branch

```bash id="git008"
git checkout feature-login
```

Or using the newer command:

```bash id="git009"
git switch feature-login
```

Verify:

```bash id="git010"
git branch
```

Output:

```text id="git011"
  main
* feature-login
```

---

## 5️⃣ Create and Switch in One Command

```bash id="git012"
git checkout -b feature-dashboard
```

Or:

```bash id="git013"
git switch -c feature-dashboard
```

This command creates the branch and immediately switches to it.

---

## 6️⃣ View All Branches

```bash id="git014"
git branch
```

Example:

```text id="git015"
main
feature-login
* feature-dashboard
```

---

## 7️⃣ List Local and Remote Branches

```bash id="git016"
git branch -a
```

Example:

```text id="git017"
* feature-dashboard
  feature-login
  main
  remotes/origin/main
```

---

## 8️⃣ Verify Current Branch

```bash id="git018"
git branch --show-current
```

Example output:

```text id="git019"
feature-dashboard
```

---

# 📚 Concepts Learned

## What is a Git Branch?

A Git branch is an independent line of development that allows developers to work on features or fixes without affecting the main codebase.

Each branch has its own commit history until it is merged.

---

## Why Use Branches?

Branches help teams:

* Develop new features
* Fix bugs
* Test experiments
* Collaborate safely
* Prevent unstable code from reaching production

---

## Git Branch Workflow

```text id="git020"
          main
            │
            │
     Create Branch
            │
            ▼
    feature-login
            │
      Make Changes
            │
         Commit
            │
         Merge
            ▼
          main
```

---

# 🌍 Real-World Use Case

A software development team may use the following workflow:

* `main` → Stable production code
* `develop` → Integration branch
* `feature/*` → New feature development
* `bugfix/*` → Bug fixes
* `hotfix/*` → Emergency production fixes

Each developer works on their own branch and submits a Pull Request before merging into the main branch.

---

# 🔍 Verification

Verify:

✅ New branch created successfully.
✅ Switched to the new branch.
✅ Current branch verified.
✅ Existing branches listed correctly.

Useful commands:

```bash id="git021"
git branch
```

```bash id="git022"
git branch -a
```

```bash id="git023"
git branch --show-current
```

```bash id="git024"
git status
```

---

# 🔐 Best Practices

* Create a new branch for every feature or bug fix.
* Use meaningful branch names such as `feature/login` or `bugfix/api-error`.
* Keep branches short-lived and merge frequently.
* Delete branches after they are merged.
* Avoid committing directly to the `main` branch.
* Use Pull Requests for code reviews before merging.

---

# 🧠 Key Takeaways

* Created multiple Git branches.
* Switched between branches.
* Verified active and available branches.
* Learned how branching supports parallel development.
* Understood Git workflows used in DevOps teams.

---

# 🚀 Skills Practiced

* Git
* Git Branching
* Version Control
* Branch Management
* Software Collaboration
* DevOps Fundamentals

---

# 💡 Interview Questions

### Q1. What is a Git branch?

A Git branch is an independent line of development that allows developers to work on changes without affecting the main codebase.

---

### Q2. What is the difference between `git branch` and `git checkout -b`?

| Command                       | Purpose                                              |
| ----------------------------- | ---------------------------------------------------- |
| `git branch branch-name`      | Creates a new branch but stays on the current branch |
| `git checkout -b branch-name` | Creates a new branch and switches to it immediately  |

---

### Q3. How do you check the current Git branch?

```bash
git branch --show-current
```

or

```bash
git branch
```

(The active branch is marked with `*`.)

---

### Q4. Why are Git branches important?

Branches allow developers to work on new features, bug fixes, or experiments independently without affecting the stable codebase, making collaboration easier and safer.

---

### Q5. What is a common Git branching strategy?

A common strategy includes:

* `main` – Production-ready code
* `develop` – Integration branch
* `feature/*` – New features
* `bugfix/*` – Bug fixes
* `hotfix/*` – Urgent production fixes

---

# 📌 Resources

* Git Documentation
* Pro Git Book
* GitHub Documentation
* Atlassian Git Tutorials

---

# ⭐ Day 024 Summary

Today's hands-on exercise focused on **creating and managing Git branches**. I created new branches, switched between them, verified the active branch, and learned how branching enables parallel development without impacting the main codebase. This exercise reinforced a core Git concept that is widely used in collaborative software development and DevOps workflows.
