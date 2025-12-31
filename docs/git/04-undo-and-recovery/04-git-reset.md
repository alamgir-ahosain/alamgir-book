
# `git reset`

* Used to **undo changes** by moving `HEAD`
* Can affect:

    * Commit history
    * Staging area
    * Working directory


<h2>Common Commands</h2>

```bash
git reset file.txt           # Unstage a specific file
git reset                    # Unstage all staged files

git reset --soft <commit>    # Move HEAD to commit, keep staged & working files
git reset --mixed <commit>   # Move HEAD to commit, unstage changes (default)
git reset --hard <commit>    # Move HEAD to commit, discard staged & working changes
```



<h2> Undo Last Commit</h2>

```bash
git reset HEAD~               # Undo last commit, keep changes staged
git reset --soft HEAD~        # Same as above
git reset --mixed HEAD~       # Undo last commit, unstage changes
git reset --hard HEAD~        # Undo last commit, discard changes completely
```



<h2>Dangerous but Useful</h2>

```bash
git reset --hard               # Restore working directory to last commit
git reset --hard <commit-hash> # Reset to specific commit, discard all changes
```


<h1>When to Use</h1>

* `--soft` → fix commit message or regroup commits
* `--mixed` → redo staging
* `--hard` → discard unwanted work

