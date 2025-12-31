
<h1>Git Reflog</h1>

* Shows the **history of HEAD and branch movements**
* Useful for **debugging** and **recovering lost commits**

<h3> Common Commands</h3>

```bash
git reflog                      # Show history of HEAD changes
git reflog show <branch>        # Show reflog for a specific branch

git reset --hard <commit-hash>  # Reset branch to a specific commit
git reset --hard HEAD@{n}       # Reset to nth previous HEAD state
```

**Use Cases:**

* Find a **specific commit**
* Recover **lost commits or deleted branches**
* Undo accidental changes not visible in normal commit history
