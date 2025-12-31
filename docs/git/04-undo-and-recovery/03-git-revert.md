# `git revert` : Undoing Commit Safely

**Theory**

* Used to **undo a commit safely**
* Creates a **new commit** that reverses the changes of a previous commit
* Does **not rewrite history** (safe for shared/public branches)
* Preferred over `git reset` on `main` / `master`
* Fixing it old mistake without erase it.


**Commands**

```bash
git revert <commit-hash>     # Revert a specific commit
git revert HEAD              # Revert the latest commit
```

```bash
git revert --no-commit <commit-hash>  # Revert but do not auto-commit
```

* Opens an editor to confirm the revert commit message
* The original commit remains in history


![alt text](image/revert1.png)
![alt text](image/revert2.png)

---

**Summary**

* `reset` → removes commits (history rewrite)
* `revert` → adds a new commit to undo changes


