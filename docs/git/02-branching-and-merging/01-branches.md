
<h1>Git Branches</h1>

---

<h2>What is a Branch?</h2>

* Allows  to keep track of different changes separately.
* Used to develop features, fixes, or experiments safely without affecting main code.


![alt text](image/branch.png)


---


<h2> HEAD and Branch</h2>

* `HEAD` points to the **current branch**

* Switching branches moves `HEAD`
* Check active branch: `cat .git/HEAD` or `git branch`

![alt text](image/head1.png)

![alt text](image/head2.png)




---

<h2>Branch Commands</h2>

**List branches**

* `git branch` → local branches
* `git branch -a` → all branches (local + remote)

**Create a branch**

* `git branch bug-fix`

**Switch branch**

* `git checkout bug-fix`
* `git switch bug-fix`

**Create & switch**

* `git checkout -c bug-fix`
* `git switch -c bug-fix`

**Rename branch**

* `git branch -m old-name new-name`
* `git branch -M main`

**Delete branch**

* `git branch -d bug-fix`
* `git branch -D bug-fix` (force)


![alt text](image/branch-command.png)


<h3> Remote Branches</h3>

* `git branch -r`→View remote branches 
*  `git push origin bug-fix`→Push a branch
*  `git push origin --delete bug-fix`→Delete remote branch

---



**Best Practices**

* Commit before switching branches
* One feature or fix per branch
* Delete branches after merge





