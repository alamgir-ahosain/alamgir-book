

<h1>Processes</h1>



* **Process**: A running instance of a program.
* **Pseudo-filesystem**: Files that exist in memory and represent kernel or process info (`/proc`, `/sys`).
* **PID (Process ID)**: Unique identifier for each running process(  Example: PID 72 → `/proc/72/`)
* **Module**: Kernel driver that extends functionality.
* **Sysctl**: Tool and configuration for modifying kernel parameters.
* `/proc` also contains kernel/system info such as:

    * `/proc/cmdline` → Kernel startup parameters
    * `/proc/meminfo` → Memory usage
    * `/proc/modules` → Loaded kernel modules

---

<h3>Example /proc Output</h3>

```bash
sysadmin@localhost:~$ ls /proc
1   128   17   21   23   39   60   72   cpuinfo  modules  meminfo ...
```

* Directories with numbers = active processes
* Files like `cpuinfo`, `modules`, `meminfo` = kernel/system info



<h3>Modifying Kernel Behavior</h3>

* `/proc/sys` contains files that **can be modified by root** to change kernel behavior.
* Changes made directly are **temporary**; permanent changes require `/etc/sysctl.conf`.
* Example: Disable ping (ICMP echo) responses:

```bash
# Check current ICMP echo response setting
cat /proc/sys/net/ipv4/icmp_echo_ignore_all
0

# Ping localhost works
ping -c1 localhost
# 1 packets transmitted, 1 received

# Disable ping responses
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all

# Ping localhost fails
ping -c1 localhost
# 1 packets transmitted, 0 received
```


