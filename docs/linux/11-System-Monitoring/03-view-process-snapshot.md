

<h1>Viewing Process Snapshot</h1>

* **Basic `ps` command**

  * Shows processes running in the **current shell**.
  * Includes `ps` itself in the output.


* **Parent-child view**

  * Use `--forest` to show hierarchical relationships like `pstree`.


* **View all system processes**

  * `ps aux` or `ps -ef`

* **Viewing processes of a specific user**

  * Use the `-u` option:

 
```bash
ps # Shows processes running in the current shell
ps --forest # Displays parent-child hierarchy of processes
ps aux | head # Shows all system processes, first 10 lines only
ps -ef | head #  Displays full-format list of all processes, first 10 lines
ps -ef | grep firefox #  Filters and shows processes with firefox in the name
ps -u root #  Displays processes owned by user root
```


---

<h1>Viewing Processes in Linux</h1>

A **process** is an instance of a running command.

* Processes run with the **user privileges** of the user who started them.
* **Regular users** can control only their own processes.
* **Root/administrator** can control **all processes**.


<h2>1.  Basic ps Command</h2>

```bash
ps
```

**Example Output:**

``` 
  PID    TTY          TIME        CMD
   80    pts/0        00:00:00    bash
   94    pts/0        00:00:00    ps
```

| Column   | Meaning                               |
| -------- | ------------------------------------- |
| **PID**  | Process ID (unique identifier)        |
| **TTY**  | Terminal where the process is running |
| **TIME** | CPU time used by the process          |
| **CMD**  | Command that started the process      |


<h2>2. View All Processes</h2>

```bash
ps          # Show processes in current terminal
ps -e       # Show every process on the system
ps -ef      # Show all processes with full details (UID, PPID, CMD, etc.)
```

**Example Output (`ps -e`):**

```
  PID TTY    TIME      CMD
   1 ?      00:00:00   init
   33 ?     00:00:00   rsyslogd
```

**Example Output (`ps -ef`):**

```
UID        PID    PPID  C   STIME TTY      TIME       CMD
root         1     0    0   19:16 ?        00:00:00   /sbin/init
syslog      33     1    0    19:16 ?       00:00:00   /usr/sbin/rsyslogd
```

| Column    | Meaning                     |
| --------- | --------------------------- |
| **UID**   | User who owns the process   |
| **PID**   | Process ID                  |
| **PPID**  | Parent Process ID           |
| **C**     | CPU usage percentage        |
| **STIME** | Process start time          |
| **TTY**   | Terminal of the process     |
| **TIME**  | CPU time used               |
| **CMD**   | Full command with arguments |

