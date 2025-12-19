
<h1>Process Hierarchy</h1>

* **Init Process**

    * Kernel starts `init` after boot, always assigned **PID 1**.
    * System V: `/sbin/init`
    * systemd: `/bin/systemd` → usually links to `/lib/system/systemd`.

* **Parent and Child Processes**

    * Process starting another → **Parent Process**
    * Process started → **Child Process**
    * Parent PID is labeled **PPID**.

* **PID Limits**

    * Maximum PID value can be viewed/changed: `/proc/sys/kernel/pid_max`
    * After reaching maximum, PID **rolls over** to available values.

* **Process Tree**

    * Processes can be visualized as a **family tree**.
    * Command: `pstree`
      Example:

      ```bash
      sysadmin@localhost:~$ pstree
      init-+-cron
          |-login---bash---pstree
          |-named---18*[{named}]
          |-rsyslogd---2*[{rsyslogd}]
          `-sshd
      ```
    * Relationships from example:

      * `init` → parent of `login`
      * `login` → child of `init`, parent of `bash`
      * `bash` → child of `login`, parent of `pstree`
      * `pstree` → child of `bash`

