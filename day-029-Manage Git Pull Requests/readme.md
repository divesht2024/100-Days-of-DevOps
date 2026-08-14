# Git Pull Request Workflow – Lab Solution

## Overview

This lab demonstrates a standard Git workflow using **feature branches**, **Pull Requests**, **code review**, and **merging changes into the master branch**.

In this lab:

* **Max** has created a new story on a feature branch.
* Max creates a **Pull Request** to merge the changes into `master`.
* **Tom** reviews the Pull Request.
* Tom approves the changes.
* The Pull Request is merged into the `master` branch.

---

# Part 1: Lab Step-by-Step Solution

## Step 1: SSH into the Storage Server

From the jump host, connect to the storage server as user `max`:

```bash
ssh max@ststor01
```

Enter the password:

```text
Max_pass123
```

---

## Step 2: Navigate to the Git Repository

Check your current directory:

```bash
pwd
```

List the available files and directories:

```bash
ls
```

Navigate to the cloned Git repository:

```bash
cd <repository-name>
```

For example:

```bash
cd story-blog
```

---

## Step 3: Verify Sarah's Existing Work

Check the contents of the repository:

```bash
ls -la
```

View the commit history:

```bash
git log --oneline --decorate --graph
```

For detailed commit information:

```bash
git log
```

Verify the following:

* Sarah's commits exist.
* The commit author information is correct.
* The commit messages are present.
* The repository history is available.

---

## Step 4: Verify Max's Feature Branch

Check the available local branches:

```bash
git branch
```

You can also check both local and remote branches:

```bash
git branch -a
```

You should see branches similar to:

```text
master
story/fox-and-grapes
```

The branch:

```text
story/fox-and-grapes
```

contains Max's new story.

---

## Step 5: Open the Gitea Web Interface

Open the **Gitea UI** from the lab environment.

Log in using:

```text
Username: max
Password: Max_pass123
```

---

## Step 6: Create a Pull Request

Open the `story-blog` repository.

Navigate to:

```text
Pull Requests
→ New Pull Request
```

Configure the Pull Request as follows:

| Option             | Value                  |
| ------------------ | ---------------------- |
| Source Branch      | `story/fox-and-grapes` |
| Destination Branch | `master`               |

Click **Compare**.

Then click:

```text
Create Pull Request
```

Use the following Pull Request title:

```text
Added fox-and-grapes story
```

Finally, click:

```text
Create Pull Request
```

At this stage, the changes have **not been merged yet**. The Pull Request is waiting for review.

---

## Step 7: Add Tom as the Reviewer

Inside the Pull Request, locate the **Reviewers** section on the right side.

Select:

```text
tom
```

Tom is now assigned as the reviewer for the Pull Request.

---

## Step 8: Log Out as Max

Click your profile and select:

```text
Sign Out
```

---

## Step 9: Log In as Tom

Log in using:

```text
Username: tom
Password: Tom_pass123
```

---

## Step 10: Open the Pull Request

Navigate to:

```text
Pull Requests
```

Open the Pull Request:

```text
Added fox-and-grapes story
```

---

## Step 11: Review and Approve the Pull Request

Review the changes made by Max.

If everything looks correct, click:

```text
Review
→ Approve
→ Submit Review
```

Tom has now approved the Pull Request.

---

## Step 12: Merge the Pull Request

Click:

```text
Merge Pull Request
```

Confirm the merge.

The changes from:

```text
story/fox-and-grapes
```

will now be merged into:

```text
master
```

The Pull Request should now show that it has been successfully merged.

---

## Step 13: Verify the Merge

Return to the storage server and switch to the `master` branch:

```bash
git checkout master
```

Pull the latest changes:

```bash
git pull
```

Check the commit history:

```bash
git log --oneline
```

The output should show a merge commit similar to:

```text
b4673ac Merge pull request 'Added fox-and-grapes story' (#1) from story/fox-and-grapes into master
3603693 Added fox-and-grapes story
0d97f1b Merge branch 'story/frogs-and-ox'
e1bbdfe Fix typo in story title
1fdc99d Completed frogs-and-ox story
8d2151a Added the lion and mouse story
a3b4476 Add incomplete frogs-and-ox story
```

You can also verify that the new story file has been added:

```bash
ls
```

The repository should now contain:

```text
fox-and-grapes.txt
```

---

# Part 2: Beginner-Friendly Explanation

## What Is Happening in This Lab?

This lab demonstrates a common Git workflow used by software development teams.

Instead of allowing developers to directly push changes to the `master` branch, developers work on separate **feature branches**.

Once the work is completed, the developer creates a **Pull Request (PR)**.

Another developer reviews the changes before they are merged into the main branch.

The workflow looks like this:

```text
Developer creates a feature branch
            ↓
Developer makes changes
            ↓
Developer commits the changes
            ↓
Developer creates a Pull Request
            ↓
Reviewer checks the changes
            ↓
Reviewer approves the Pull Request
            ↓
Changes are merged into master
```

---

## Step 1: Connect to the Storage Server

You connect to the storage server as `max`.

```bash
ssh max@ststor01
```

This gives you access to Max's local copy of the Git repository.

---

## Step 2: Navigate to the Repository

You move into the cloned Git repository:

```bash
cd story-blog
```

This directory contains the project files and Git history.

---

## Step 3: Check the Existing Git History

Running:

```bash
git log
```

allows you to see:

* Previous commits.
* Who created the commits.
* Commit messages.
* The history of the repository.

This confirms that Sarah's previous work already exists in the project.

---

## Step 4: Check Max's Feature Branch

The branch:

```text
story/fox-and-grapes
```

contains Max's new work.

Instead of directly modifying the `master` branch, Max worked on a separate feature branch.

This is a good practice because it keeps the main branch safe from unfinished or unreviewed changes.

---

## Step 5: Log In to Gitea as Max

Max logs in to the Gitea web interface.

Gitea provides a web interface where developers can manage repositories, branches, Pull Requests, and code reviews.

---

## Step 6: Create a Pull Request

Max requests to merge:

```text
story/fox-and-grapes
```

into:

```text
master
```

The Pull Request title is:

```text
Added fox-and-grapes story
```

At this point, the changes are **not merged yet**.

The Pull Request is waiting for another developer to review the changes.

---

## Step 7: Assign Tom as the Reviewer

Tom is assigned as the reviewer.

His responsibility is to check Max's changes before they are merged into the main branch.

The reviewer can:

* Approve the changes.
* Request changes.
* Comment on the code.

This process helps maintain code quality.

---

## Step 8: Log Out as Max

Max logs out after creating the Pull Request and assigning Tom as the reviewer.

---

## Step 9: Log In as Tom

Now you log in as:

```text
tom
```

You are now acting as the reviewer.

---

## Step 10: Open the Pull Request

Tom opens the Pull Request created by Max.

He can now see the changes that Max wants to merge into the `master` branch.

---

## Step 11: Approve the Changes

Tom reviews the changes.

If everything looks correct, he selects:

```text
Approve
```

This means that the changes have been reviewed and are acceptable.

---

## Step 12: Merge the Pull Request

After approval, the Pull Request can be merged.

The changes move from:

```text
story/fox-and-grapes
```

into:

```text
master
```

The new story is now officially part of the main project.

---

# Final Workflow Summary

```text
                    Max
                     │
                     ▼
        Creates a feature branch
        story/fox-and-grapes
                     │
                     ▼
              Makes changes
                     │
                     ▼
          Creates Pull Request
                     │
                     ▼
           Assigns Tom as reviewer
                     │
                     ▼
                    Tom
                     │
                     ▼
            Reviews the changes
                     │
                     ▼
          Approves the Pull Request
                     │
                     ▼
           Merge Pull Request
                     │
                     ▼
                  master
```

---

# Commands Used in This Lab

| Command               | Purpose                                                           |
| --------------------- | ----------------------------------------------------------------- |
| `ssh max@ststor01`    | Connect to the storage server                                     |
| `pwd`                 | Display the current directory                                     |
| `ls`                  | List files and directories                                        |
| `cd story-blog`       | Navigate to the Git repository                                    |
| `git log`             | View detailed commit history                                      |
| `git log --oneline`   | View a simplified commit history                                  |
| `git branch`          | List local branches                                               |
| `git branch -a`       | List local and remote branches                                    |
| `git checkout master` | Switch to the master branch                                       |
| `git pull`            | Download and update the latest changes from the remote repository |

---

# Key Concepts Learned

* Git branches
* Feature branches
* Pull Requests
* Code review
* Assigning reviewers
* Pull Request approval
* Merging branches
* Checking Git commit history
* Synchronizing a local repository with a remote repository

---

## Final Result

The changes created by Max in the:

```text
story/fox-and-grapes
```

branch are successfully reviewed by Tom and merged into:

```text
master
```

The `fox-and-grapes.txt` file is now part of the main project branch.

**Lab completed successfully.**
