
<h1>Account Considerations</h1>

>Information to Plan Before Creating a User : Username, UID, Primary group, Supplementary groups,  Home directory,  Skeleton directory, Shell,  Comment (GECOS)



---

| Category                  | Key Points                                                                                                                                                     | Example Command                  |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| **Username**              | Required for `useradd`<br> First char: `_` or `a–z`<br>Max: 32 (≤16 recommended)<br>Allowed: letters, numbers, `-`, `_`<br>Last char: not `-`<br>Must be unique | `useradd jane`                   |
| **User Identifier (UID)** | Auto-increment by default<br>Set manually with `-u`<br>Recommended max: 60000<br>`root` UID = 0<br>System: 1–999<br>Regular users: ≥1000                       | `useradd -u 1000 jane`           |

![alt text](image/u1.png)


---

| Group Type               | Description                                                                                                      | Command                          |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| **Primary Group**        | Default group if not specified<br>UPG: group auto-created<br>Non-UPG: usually `users` (GID 100)<br>Set with `-g` | `useradd -g users jane`          |
| **Supplementary Groups** | Extra group memberships<br>Comma-separated list<br>Set with `-G`                                                 | `useradd -G sales,research jane` |


![alt text](image/u2.png)

---


| Item                   | Description                                                                                                                                                   | Command                                                                        |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Home Directory**     | Default: `/home/username`<br>Created automatically if enabled<br><br>Controlled by  `/etc/default/useradd` and    `/etc/login.defs`<br><br>Options :<br>`-m` create home<br>`-M` do not create home<br>`-b` set base directory<br>`-d` set full path | `useradd -m jane`<br>`useradd -mb /test jane`<br>`useradd -md /test/jane jane` |
| **Skeleton Directory** | Default: `/etc/skel`<br>Files copied to home<br>`-k` set custom skeleton<br>Requires `-m`                                                                     | `useradd -mk /home/sysadmin jane`                                              |



![alt text](image/u3.png)
![alt text](image/u4.png)

---
| Item                | Description                                                                                            | Command                      |
| ------------------- | ------------------------------------------------------------------------------------------------------ | ---------------------------- |
| **Shell**           | Default from `/etc/default/useradd`<br>Override with `-s`<br>System accounts often use `/sbin/nologin` | `useradd -s /bin/bash jane`  |
| **Comment (GECOS)** | Usually full name<br>Shown by login managers<br>Set with `-c`                                          | `useradd -c "Jane Doe" jane` |
