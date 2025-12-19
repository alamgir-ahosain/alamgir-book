
<h1>Changing Groups</h1>

<h3>Switching Primary Group Temporarily</h3>

* **Command:** `newgrp group_name` – Change current primary group in the active shell.
* Verify the change with `id`.
    ![alt text](image/group-permission1.png)


* Files created in the new shell will belong to the new primary group:

    ![alt text](image/group-permission11.png)

* To revert to the original primary group, **exit the new shell**:

    ![alt text](image/group-permission2.png)



<h3>Changing Primary Group Permanently</h3>

* Requires **administrative privileges**.
* **Command:** `usermod -g groupname username`


<h3>Checking Group Membership</h3>

* `groups` – Show all groups a user belongs to.
* `id` – Show UID, GID, and all group memberships (more detailed).



