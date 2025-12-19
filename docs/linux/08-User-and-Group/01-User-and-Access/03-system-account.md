<h1>System accounts </h1>

System accounts are special accounts used by the system and services rather than regular users.

<h3>Key Points</h3>

* **UID Range:** 1–499 (system accounts); root has UID 0.
* **Purpose:** Run system services (e.g., `sshd`, `bind`) and perform background tasks.
* **Login:** Typically **not used for interactive login**.
* **Shell Field:** Non-login shells in `/etc/passwd` (e.g., `/usr/sbin/nologin`).
* **Home Directory:** Often **none** or minimal, e.g., `/var/run/sshd`.
* **Password Field:** Usually an asterisk `*` in `/etc/shadow`.

<h3>Examples</h3>

| File          | Example Entry                                       | Description                                     |
| ------------- | --------------------------------------------------- | ----------------------------------------------- |
| `/etc/passwd` | `sshd:x:103:65534::/var/run/sshd:/usr/sbin/nologin` | System account for SSH service; non-login shell |
| `/etc/shadow` | `sshd:*:16874:0:99999:7:::`                         | No password; account cannot be used to log in   |

---

<h3>Notes</h3>

* System accounts are **essential** for normal system operation.
* **Do not delete** system accounts unless certain it will not break functionality.
* Administrators must **secure system accounts** to maintain system security.
