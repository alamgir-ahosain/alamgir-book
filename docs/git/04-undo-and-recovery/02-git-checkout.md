<h1> Checking Out a Previous Commit</h1>

* Git allow you **move to older commits** to inspect or test code
* Checking out a commit hash puts Git in **detached HEAD**
* In detached HEAD:

    *  can view/run the code
    * New commits are **not on any branch**

* To keep changes, create a **new branch** from that commit



**Commands**

```bash

git checkout <hash>     # Detach HEAD at a specific commit (can create a new branch from here)
git checkout HEAD~2     # View the state 2 commits before HEAD
git checkout HEAD~2 file.txt #view the state of file
git checkout main       # Re-attach HEAD to a branch
git reflog              # Show history of HEAD movements (branch changes, commits, resets)
git restore <filename>  # Restore file to last committed version
```


