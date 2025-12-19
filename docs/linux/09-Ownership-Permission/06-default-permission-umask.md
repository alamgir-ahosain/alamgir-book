
<h1> Default Permissions (umask)</h1>

<h3>What is umask?</h3>

* Determines **default permissions** for newly created files and directories.
* Default permissions = **max permissions -  umask**.
* Maximum default permissions:

  | Type      | Max Permissions   |
  | --------- | ----------------- |
  | File      | `rw-rw-rw-` (666) |
  | Directory | `rwxrwxrwx` (777) |






<h3>Check Current umask</h3>

![alt text](image/umask.png)
**Breakdown of 0027:**

* First `0`: octal number

* Second `0`: subtract from **user**

* Third `2`: subtract from **group**

* Fourth `7`: subtract from **others**



---

<h3>Example: File Permissions</h3>

* Assume `umask = 027`
* Default file permissions = 666
* Resulting permissions = 666 - 027 = 640 → `rw-r-----`

![alt text](image/umask-f.png)
---

<h3>Example: Directory Permissions</h3>

* Assume `umask = 027`
* Default directory permissions = 777
* Resulting permissions = 777 - 027 = 750 → `rwxr-x---`

![alt text](image/umask-d.png)

---

<h3>Important Notes</h3>

* **Umask applies only to new files/directories in the current session.**
* To make it **permanent**, modify the user's `.bashrc` in their home directory.

