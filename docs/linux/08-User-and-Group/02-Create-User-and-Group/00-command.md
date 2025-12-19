


**``groupadd``** – Create a new group with the 
**`groupmod`** – Make changes to groups using the  
**`useradd`**– Create a new user with the  
**`passwd`** – Set and reset a user's password 
**`usermod`** Make changes to the user account 

---
<h2>Related Group Command</h2>

1. **`grep groupname /etc/group`** – View group details from local group file.
2. **`getent group groupname`** – Display group information (local + network).
3. **`id user`** – Show user and group membership information.
4. **`find / -nogroup`** – Find files owned by orphaned GIDs.



<h2>Create Group </h2>

1. **`groupadd -g 1212 alamgir`** –  create group with specify GID
2. **`groupadd auto`**  – Automatic GID Assignment
3. **`grep auto /etc/group`** – verify group creation
4. **`groupadd -r alamgir`** – assign GID by system automatically

<h2>Modify Group</h2>

1. **`groupmod -n newname oldname`** – Rename an existing group.
2. **`groupmod -g GID groupname`** – Change a group’s GID.

<h2>Delete Group</h2>

1. **`usermod -g group user`** – Change a user’s primary group.
2. **`usermod -aG group user`** – Add a user to a supplementary group.
3. **`gpasswd -d user group`** – Remove a user from a supplementary group.
4. **`groupdel groupname`** – Delete a group (must not be a primary group).

---


<h2>Create user</h2>

1. **`useradd -u 1212 -g cse -G ict,cps -m -c 'Alamgir Here' alamgir`**


<h2> User Related</h2>

1. **`useradd username`** – Add a new user.
2. **`useradd -u UID username`** – Set a specific user ID for the new user.
3. **`useradd -g groupname username`** – Set primary group.
4. **`useradd -G group1,group2 username`** – Set supplementary groups.
5. **`useradd -m username`** – Create a home directory.
6. **`useradd -M username`** – Do not create a home directory.
7. **`useradd -d /home/path username`** – Specify a full home directory path.
7. **`useradd -b /base/path username`** – Base directory for home.
8. **`useradd -d /full/path username`** – Full home directory path.
9. **`useradd -k /path/to/skel username`** – Custom skeleton directory.
10. **`useradd -s /path/to/shell username`** – Set login shell.
11. **`useradd -c "Comment" username`** – Set the GECOS/comment field.


<h2>Modify user </h2>

1. **`usermod`** – Modify an existing user account.
13. **`usermod -c "Comment" username`** – Change the GECOS/comment field.
14. **`usermod -d /home/newpath username`** – Change the user’s home directory.
15. **`usermod -e YYYY-MM-DD username`** – Set account expiration date.
16. **`usermod -f DAYS username`** – Allow login for DAYS after password expires.
17. **`usermod -g GROUP username`** – Change primary group.
18. **`usermod -G GROUPS username`** – Change supplementary groups (overwrite).
19. **`usermod -aG GROUPS username`** – Append supplementary groups.
20. **`usermod -l NEWNAME username`** – Change login name.
21. **`usermod -L username`** – Lock the user account.
22. **`usermod -U username`** – Unlock the user account.
23. **`usermod -s /path/to/shell username`** – Change the login shell.
24. **`usermod -u UID username`** – Change the UID (may orphan files).


<h2>User password </h2>

1. **`passwd username`** – Set or change a user’s password.
26. **`chage -l username`** – Show password aging info.
27. **`chage -M DAYS username`** – Set maximum password age.
28. **`chage -m DAYS username`** – Set minimum password age.
29. **`chage -W DAYS username`** – Set warning period before password expires.
30. **`chage -I DAYS username`** – Set inactive days after password expires.



<h2>Delete user </h2>

1. **`userdel username`** – Delete a user account (home directory remains).
32. **`userdel -r username`** – Delete a user account along with home directory and mail spool.

<h2>Others</h2>

1. **`id username`** – Show UID, GID, and group memberships.
34. **`groups username`** – Show groups the user belongs to.
35. **`whoami`** – Show the currently logged-in username.
36. **`who`** – Show currently logged-in users.
37. **`w`** – Show logged-in users, system uptime, and running processes.
38. **`last username`** – Show login history for the user.
39. **`getent passwd`** – Display all users from system database.
40. **`getent group`** – Display all groups from system database.
