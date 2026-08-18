
Connected to the Storage Server
ssh natasha@ststor01

Navigated to the Repository
cd /usr/src/kodekloudrepos/blog

Handled Git Safe Directory & Permission Issues
Sometimes in shared environments, Git warns about “dubious ownership.” I resolved it by marking the directory as safe:

git config - global - add safe.directory /usr/src/kodekloudrepos/blog

Fetched the Latest Changes
sudo git fetch origin

Switched to the Feature Branch
sudo git checkout feature

Rebased Feature onto Master
sudo git rebase master


Outcome

feature branch is now perfectly in sync with master.
Commit history is linear and clean.
No merge clutter, making future reviews and debugging easier.

Key Takeaways

git rebase is great for maintaining a clean history — but requires careful use, especially on shared branches.
Always fetch before rebasing to ensure you’re working with the latest state.
— force-with-lease is safer than a blind — force push.
