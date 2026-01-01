
# `git diff` – Compare Changes

 `git diff` command:

* Shows differences **between working directory and staging area**
* Helps see what is modified but **not yet staged**
![alt text](image/diff-workflow.png)
<h2>How to Read Diff</h2>

* `a/` → old version of file
* `b/` → new version of file
* `---` → old file
* `+++` → new file
* Lines prefixed with `-` → removed
* Lines prefixed with `+` → added

**Example workflow:**

```bash

nano nav-bar.html    # Edit a file
git add nav-bar.html # Stage the file

git diff --staged    # Check staged changes
git diff HEAD        # same as above
```
![alt text](image/diff1.png)

<h2> Comparing Commits
</h2>

| Command / Option                 | Purpose / Description                                              |
| -------------------------------- | ------------------------------------------------------------------ |
| `git diff`                       | Show changes in **working directory vs staging area**              |
| `git diff --staged` / `--cached` | Show changes in **staging area vs last commit**                    |
| `git diff <file>`                | Show changes for a **specific file**                               |
| `git diff --name-only`           | Show **only filenames** that changed                               |
| `git diff --name-status`         | Show filenames + **status** (Added / Modified / Deleted)           |
| `git diff --color-words`         | Show **inline word-level differences**                             |
| `git diff --stat`                | Show **summary/statistics** (files changed, insertions, deletions) |
| `git diff <commit>`              | Show changes between **working directory and a specific commit**   |
| `git diff <commit1> <commit2>`   | Show changes between **two commits**                               |
| `git diff <hash1>..<hash2>`      | Compare changes between **two commits** (shorthand for above)      |
| `git diff <branch1>..<branch2>`  | Show differences between **two branches**                          |
| `git diff <commit> -- <file>`    | Show changes of a **specific file** compared to a specific commit  |
| `git diff --word-diff`           | Highlight changes at **word level** instead of line level          |
| `git diff --check`               | Show **whitespace errors** in changes                              |


<h3>Quick Tips</h3>

* `--staged` = view what is about to be committed
* `--stat` = quick summary of changes
* `<commit>` or `<branch>` = compare historical or branch differences
* Combine options for clarity, e.g., `git diff --stat --staged`



