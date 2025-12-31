

<h1> git rebase : Cleaning Up History</h1>

![alt text](image/rebase.png)

* An **alternative to `git merge`**
* Used to **keep commit history clean and linear**
* Updating a feature branch with latest `main`
* Rewrites commit history (moves commits on top of another branch)

>**Remember** :  Do not run **rebase** on **`main` / `master`** branch.



<h2>Common Rebase Commands</h2>

```bash
git rebase bugfix       # Re-apply current branch commits on top of bugfix branch
git rebase --continue   # Continue rebase after resolving conflicts
git rebase --abort      # Cancel rebase and restore previous state
git rebase -i HEAD~n    # Interactive rebase to clean, squash, or reorder commits
```


