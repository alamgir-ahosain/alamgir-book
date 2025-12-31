

<h1> Git workflow </h1>

![alt text](image/workflow.png)

---

<h1>git add : staging changes</h1>

* Stages file changes for commit
* Moves files from **working directory to  staging area**

**Examples:**


| Command           | What it stages                     | Includes subfolders | Includes deletions | Notes                           |
| ----------------- | ---------------------------------- | ------------------- | ------------------ | ------------------------------- |
| `git add new.txt` | Single file                        | ❌                   | ❌                  | Stage one specific file         |
| `git add .`       | New & modified files               | ✅                   | ❌                  | From current directory downward |
| `git add *`       | Visible files in current folder    | ❌                   | ❌                  | Ignores hidden files (`.`)      |
| `git add *.txt`   | All `.txt` files in current folder | ❌                   | ❌                  | Shell glob, not recursive       |
| `git add -A`  or <br>`git add --all`     | All changes in repo                | ✅                   | ✅                  | Best for full staging           |



**Unstaging Changes**:
```bash
git reset file.txt   # only unstages that file (changes remain in working directory)
git reset            # Unstage all staged changes (keeps working directory changes)
```
![alt text](image/add.png)
