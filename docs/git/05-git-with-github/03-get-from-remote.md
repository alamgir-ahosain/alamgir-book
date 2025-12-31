<h1> Get Code from Remote Repository</h1>

There are **two ways** to get code from a remote repository:

<h2> 1. Fetch Code</h2>

* Downloads updates from the remote repo
* **Does not merge** changes into your local branch

```bash
git fetch <remote-name>
```

**Example:**

```bash
git fetch origin
```

![alt text](image/gr1.png)

---

<h2> 2. Pull Code</h2>

* Downloads updates **and merges** them into your local branch
* Equivalent to: `git fetch` + `git merge`

```bash
git pull <remote-name> <branch-name>
```

**Example:**

```bash
git pull origin master
```
![alt text](image/gr2.png)
---

<h1>Summary</h1>

* `git fetch` → remote → local (no merge)
* `git pull` → remote → local + merge

