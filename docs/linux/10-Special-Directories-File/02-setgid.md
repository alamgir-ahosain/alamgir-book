
<h1>setgid on Files </h1>

* **Definition**:

  * Setgid (set group ID) on a file allows a user to execute a file with the **group privileges** of the file owner temporarily.
  * Similar to setuid but applies to **group access** instead of user access.

 **Example**: 

| File          | Permissions | Owner | Group | Notes                                                 |
| ------------- | ----------- | ----- | ----- | ----------------------------------------------------- |
| /usr/bin/wall | -rwxr-sr-x  | root  | tty   | Executable with setgid; grants temporary group access |
| /dev/tty0     | crw--w----  | root  | tty   | Terminal device; writable by tty group only           |
| /dev/tty1     | crw--w----  | root  | tty   | Terminal device; writable by tty group only           |

* **Key Points**:

  * Setgid allows commands to access **group-owned resources** that normal users cannot access.
  * Without setgid, `/usr/bin/wall` would fail to write to `/dev/tty*` files.

