
# `.git` Folder

<h2>Folders</h2>

* **`hooks/`**

    * Scripts triggered by Git events
    * Examples: `pre-commit`, `post-commit`

* **`info/`**

    * Repository-specific info
    * Example: `exclude` (local `.gitignore`)

* **`logs/`**

    * history of branch and HEAD changes
    * Records updates to `HEAD` and branches
    * Helps in recovery and auditing

* **`objects/`**

    * Stores all Git data
    * Includes commits, trees, and file contents

* **`refs/`**

    * Pointers to commits
    * **`heads/`** → local branches
    * **`remotes/`** → remote branches
    * **`tags/`** → tags

<h2>Files</h2>

  * **`HEAD`** → points to current branch
  * **`config`** → repository configuration settings
  * **`index`** →  Stores staging area information
  * **`description`** → used by GitWeb


<h2> Internal / Auto-generated (may appear)</h2>

* **`packed-refs`** → Optimized storage for references
* **`ORIG_HEAD`** → Previous `HEAD` (used in reset/merge)
* **`FETCH_HEAD`** → last fetch info
* **`COMMIT_EDITMSG`** → last commit message

