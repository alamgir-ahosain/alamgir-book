<h1>Introduction</h1>

<h3>User Accounts</h3>

* Linux creates a regular user with **sudo** or requires a **root** password.
* Administrative tasks run as **root**, directly or via **sudo**.
* Single-user systems may need one account.
* Multi-user systems should use separate accounts.

<h3>Advantages of Separate Accounts</h3>

* Private **home directories** for security.
* **Selective sudo** access with logging.
* Flexible **group-based permissions**.

<h3>Groups & User Management</h3>

* Some systems auto-create a **User Private Group (UPG)**.
* **UPG**: group name = username; only that user is a member.
* Without UPG, users get the **users** group as primary.
* Users must belong to **at least one group**.
* Shared groups support collaboration.

<h3>Best Practice</h3>

* **Create groups first**, then users.
* Creating users first requires extra changes later.
