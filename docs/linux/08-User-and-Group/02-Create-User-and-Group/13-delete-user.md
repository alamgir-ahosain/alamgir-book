

<h1>Deleting a User</h1>

* **Command:** `userdel` – Deletes a user account.

<h3>Options and Considerations</h3>

* **Without `-r`:**

  * Deletes the user account only.
  * Home directory and mail spool remain.
  * Files in the home directory become orphaned (owned by UID/GID).
  * **Example:**

    ```bash
    userdel jane
    ```

* **With `-r`:**

  * Deletes the user account, home directory, and mail spool.
  * Files outside the home directory remain as orphaned files.
  * **Example:**

    ```bash
    userdel -r jane
    ```

* **Important:**

  * Backup important files before deleting a user.
  * Deletion is irreversible.



