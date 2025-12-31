
<h1>Git Architecture: Local vs Remote</h1>

<h2>1.  Local Repository</h2>

* Stored on your **machine**
* Includes:

    * **Working Directory** → your files
    * **Staging Area** → files ready to commit
    * **.git folder** → stores commit history and metadata

* You can **commit, branch, and revert** without internet

---

<h2>2. Remote Repository</h2>

* Stored on a **server** (GitHub, GitLab, Bitbucket)
* Shared among multiple developers
* Used for **collaboration** and backup
* Common operations:

    * `git push` → send local change to remote
    * `git fetch` →bringing remote changes into local repo, but not merging them yet.
    * `git pull` → fetch + merge changes from remote


>pull=fetch+merge

---

<h3>Summary</h3>

* **Local repo** → your private workspace
* **Remote repo** → shared team workspace
* Git **syncs local and remote** via push, pull, and fetch
