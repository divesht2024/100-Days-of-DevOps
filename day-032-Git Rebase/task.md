
The Nautilus DevOps team had a situation:

A developer was actively working on a feature branch (still in progress).
New updates had already been pushed to the master branch.
The developer wanted the feature branch to be up-to-date with master, but without using a regular merge (to avoid extra merge commits).
This is a perfect use case for git rebase, which reapplies the commits from your current branch on top of another branch’s updated history.
