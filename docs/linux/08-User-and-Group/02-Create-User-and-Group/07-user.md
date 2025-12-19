<h1>Users</h1> 

<h3>User Account Files</h3>

* **`/etc/passwd`** – Stores user account details.
* **`/etc/shadow`** – Stores encrypted passwords and authentication data.

<h3>Creating Users</h3>

* **Do not edit files manually** – high risk of login failures.
* Use **`useradd`** to safely create users.
* `useradd` automatically updates `/etc/passwd` and `/etc/shadow`.

<h3>Why Use `useradd</h3>

* Prevents syntax and permission errors.
* Ensures consistent and secure account creation.

<h3>Before Adding Users</h3>

* Check default settings used by `useradd`.
* Defaults are defined in configuration files.
* Proper defaults reduce post-creation fixes.

<h3>Key Configuration Files</h3>

| File                   | Purpose                               |
| ---------------------- | ------------------------------------- |
| `/etc/login.defs`      | Default UID, GID, password policies   |
| `/etc/default/useradd` | Default home directory, shell, groups |


> Remember : Verify useradd defaults **before** creating users to avoid reconfiguration later.

