
<h1>Publish Code to Remote Repository</h1>

After setting up your **SSH key** and adding it to GitHub, you can push your code to a remote repo.



<h2>1. Create Local Repository</h2>

```bash
git init
git add <files>
git commit -m "Your commit message"
```



<h2>2.  Check Remote URLs</h2>

```bash
git remote -v    # View configured remote repositories
```



<h2>3.  Add Remote Repository</h2>

```bash
git remote add origin <remote-url>
```

* `origin` → default name for the remote repo
* `<remote-url>` → GitHub repository URL

**Example:**

```bash
git remote add origin https://github.com/alamgir-ahosain/git-test.git
```

![alt text](image/pr1.png)


<h2>4.  Push Code to Remote</h2>

```bash
git push origin master
```

* Pushes local `master` branch to remote `origin`

![alt text](image/pr2.png)

<h2>5. Set Upstream (Recommended)</h2>

```bash
git push -u origin master
```

* Sets `origin/master` as the upstream branch
* Allows future use of:

  ```bash
  git push
  git pull
  ```

  ![alt text](image/pr3.png)
![alt text](image/pr4.png)


<h2>6. Upstream Remote (Optional – for forks)</h2>

```bash
git remote add upstream <remote-url>
```

* Used to sync with the original repository

---

<h1>Summary</h1>

* `origin` → your remote repo
* `upstream` → original source repo
* `-u` → link local branch with remote branch

