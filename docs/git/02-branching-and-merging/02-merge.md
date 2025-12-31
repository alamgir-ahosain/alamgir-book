
<h1>Git Merging</h1>

---

<h1>What is Merging?</h1>

* Merging combines changes from one branch into another
* Usually done into `main` or `master`


<h2> Types of Merge</h2>



| Merge Type                 | When It Happens                  | What Git Does                             | Merge Commit | Command                    |
| -------------------------- | -------------------------------- | ----------------------------------------- | ------------ | -------------------------- |
| **Fast-Forward Merge**     | Target branch has no new commits | Moves branch pointer forward              |  No         | `git merge feature-branch` |
| **Non Fast-Forward Merge** | Both branches have new commits   | Creates a merge commit, preserves history |  Yes        | `git merge feature-branch` |

---

<h2> Branch Merge Commands</h2>

**Merge a branch**

* `git merge bug-fix` : Merge into the **current branch**

**Abort merge**

* `git merge --abort`


---

<h2>Merge Conflict</h2>

* Occurs when Git cannot auto-merge changes
* Usually when **same file, same line** is modified

**Steps to resolve:**

* Open conflicted files
* Fix conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
* `git add <file>`
* `git commit`

![alt text](image/merge-con1.png)
![alt text](image/merge-con2.png)

---

 **Point to remember**
 
* Use fast-forward for clean history
* Use non fast-forward to keep branch context


