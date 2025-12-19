
<h1>Modifying a User</h1>


<h3>Important Considerations</h3>

* Some changes (e.g., login name) cannot be applied if the user is logged in.
* Group membership changes take effect after the user logs out and logs back in.
* Use `who`, `w`, and `last` to check who is currently logged in:

  * `who` – Shows currently logged-in users.
  * `w` – Verbose; shows logged-in users, system uptime, load, and running processes.
  * `last` – Shows past login sessions; can filter by username or tty.

---

<h3>usermod Command Options</h3>

| Option           | Description                                                         | Example Command                        |
| ---------------- | ------------------------------------------------------------------- | -------------------------------------- |
| `-c COMMENT`     | Set GECOS/comment field.                                            | `usermod -c "Alamgir Here" alamgir`    |
| `-d HOME_DIR`    | Set new home directory.                                             | `usermod -d /home/alamgir_new alamgir` |
| `-e EXPIRE_DATE` | Set account expiration date.                                        | `usermod -e 2026-12-31 alamgir`        |
| `-f INACTIVE`    | Permit login for INACTIVE days after password expires.              | `usermod -f 10 alamgir`                |
| `-g GROUP`       | Set primary group.                                                  | `usermod -g users alamgir`             |
| `-G GROUPS`      | Set supplementary groups (overwrites existing unless `-a` is used). | `usermod -G cse,ict alamgir`    |
| `-a -G GROUPS`   | Append supplementary groups instead of overwriting.                 | `usermod -aG cps alamgir`      |
| `-h`             | Show help.                                                          | `usermod -h`                           |
| `-l NEW_LOGIN`   | Change login name.                                                  | `usermod -l alamgirhere alamgir`             |
| `-L`             | Lock the user account.                                              | `usermod -L alamgir`                   |
| `-s SHELL`       | Set login shell.                                                    | `usermod -s /bin/bash alamgir`         |
| `-u NEW_UID`     | Change user UID (may orphan files).                                 | `usermod -u 1500 alamgir`              |
| `-U`             | Unlock the user account.                                            | `usermod -U alamgir`                   |



