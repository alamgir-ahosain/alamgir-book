
<h1>Git Behind the Scenes</h1>

Git is a **version control system** that tracks changes in files and folders by storing the project history internally.


<h2>Git Snapshots</h2>

* A **snapshot** represents the state of the code at a specific time
* Each snapshot is identified by a **unique hash**
* Git does **not store differences**, it stores **snapshots**
* Internally, Git stores data as **objects** in a key-value database



<h2>Git Objects (3 Musketeers)</h2>

<h3>1. Commit Object</h3>

* Represents a snapshot
* Stored inside the `.git` folder
* Contains:

    * Tree object reference
    * Parent commit reference
    * Author & committer
    * Commit message



<h3>2. Tree Object</h3>

* Represents directories and file structure
* Contains:

    * File mode
    * File name
    * File hash

Everything is stored as key-value pairs in the tree object. The key is the file name and the value is the file hash.


<h3>3. Blob Object</h3>

* tree object and contains the  **actual file content**
* Does not store file name or path



---

<h2>Helpful Git Internal Commands</h2>

```bash
git show -s --pretty=raw <commit-hash>   # View raw commit object
git ls-tree <tree-id>                    # View tree object contents
git show <blob-id>                       # View file content (blob)
git cat-file -p <commit-id>              # Inspect commit object
```

