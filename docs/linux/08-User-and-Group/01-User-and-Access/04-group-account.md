<h1>Group Accounts</h1>

Users can belong to one or more groups, which affects **system access and permissions**.


<h3>Key Points</h3>

* **Primary Group:** Defined in `/etc/passwd`.
* **Secondary Groups:** Defined in `/etc/group`.
* **Modern Linux:** Users can belong to **over 65,000 groups** (older UNIX limited to 16).
* **Group names vs. GID:** Names are for humans; system uses numeric **GID** internally.

---


Example : 
![alt text](image/group.png)


| Field                    | Example      | Description                                                    |
| ------------------------ | ------------ | -------------------------------------------------------------- |
| **Group Name**           | mail         | Name of the group, easier to remember than the numeric GID.    |
| **Password Placeholder** | x            | Indicates group password is **not stored here** (rarely used). |
| **GID**                  | 12           | Unique numeric ID of the group.                                |
| **User List**            | mail,postfix | Members of the group (secondary membership).                   |

