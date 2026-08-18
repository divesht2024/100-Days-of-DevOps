# Git Rebase: Feature Branch Sync with Master

## Steps Performed

### 1. Connected to the Storage Server

```bash
ssh natasha@ststor01
```

### 2. Navigated to the Repository

```bash
cd /usr/src/kodekloudrepos/blog
```

### 3. Handled Git Safe Directory & Permission Issues

In shared environments, Git may warn about **“dubious ownership.”** I resolved this by marking the repository as a safe directory:

```bash
git config --global --add safe.directory /usr/src/kodekloudrepos/blog
```

### 4. Fetched the Latest Changes

```bash
sudo git fetch origin
```

### 5. Switched to the Feature Branch

```bash
sudo git checkout feature
```

### 6. Rebased Feature onto Master

```bash
sudo git rebase master
```

## Outcome

* The `feature` branch is now perfectly in sync with `master`.
* The commit history is linear and clean.
* There is no unnecessary merge clutter, making future reviews and debugging easier.

## Key Takeaways

* **`git rebase`** is useful for maintaining a clean and linear Git history, but it should be used carefully, especially on shared branches.
* Always **fetch the latest changes** before rebasing to ensure you are working with the most up-to-date state.
* **`git push --force-with-lease`** is safer than a blind `git push --force` when updating a rebased remote branch.
