<h1>Groups</h1> 

**Purpose of Groups**

* Used mainly to **share files** among users.
* Common in **team or project collaboration**.
* Files/directories can be owned by a group.
* Permissions allow **group members** to access shared files.

**How Groups Are Used**

* Add users to a **common group**.
* Change directory ownership to that group.
* Set group permissions for access.

**Verify Group Information**

* **`/etc/group`** stores group details.
* Use **grep** for local groups:  `grep root /etc/group`

* Use **getent** for local + network groups:  `getent group root`
  

![alt text](image/g1.png)

---
