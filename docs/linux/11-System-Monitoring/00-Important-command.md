<h2>The Kernel and /proc</h2>

```bash
ls /proc                    # List contents of the /proc pseudo-filesystem
cat /proc/1/cmdline; echo   # View command line of the /sbin/init process (PID 1)
ps -p 1                     # Display information about the /sbin/init process (PID 1)
cat /proc/cmdline            # View arguments passed to the kernel at boot time
```


<h2>Managing Processes</h2>

```bash
ping localhost > /dev/null     # Redirect output to /dev/null (bit bucket), runs in foreground
Ctrl+C                         # Terminate the foreground ping process

ping localhost > /dev/null &   # Start ping in the background
jobs                           # List background jobs

ping localhost > /dev/null &   # Start another ping in the background
jobs                           # Verify two background jobs running

fg %1                          # Bring first job to the foreground
Ctrl+Z                         # Suspend the foreground process
bg %1                          # Resume the suspended process in the background
jobs                           # Verify jobs status

ping localhost > /dev/null &   # Start a third ping in the background
jobs                           # Verify three background jobs running

kill %3                        # Stop the third ping job
jobs                           # Verify the third job is terminated

killall ping                   # Stop all ping processes
jobs                           # Verify all ping jobs are terminated
```


<h2> Use Top to view the process</h2>

```bash
ping localhost > /dev/null &   # Start first ping in the background
ping localhost > /dev/null &   # Start second ping in the background

top                            # Start interactive top command to monitor processes

# Inside top:
k              # Press 'k' to kill a process
122            # Enter PID of first ping process
Enter          # Press Enter to use default signal (15), first ping terminated

k              # Press 'k' again to kill another process
123            # Enter PID of second ping process
9              # Enter signal 9 to force kill, second ping terminated

q              # Exit the top command
```

<h2>Use pkill and kill To Terminate Processes</h2>

```bash
sleep 888888 &           # Start first sleep command in the background
sleep 888888 &           # Start second sleep command in the background

jobs                     # View running background jobs

ps                       # List processes to find PIDs of sleep commands
kill 134                 # Kill the first sleep process using its PID
jobs                     # Verify first sleep process is terminated

pkill -15 sleep          # Kill remaining sleep process using its name
jobs                     # Verify all sleep processes are terminated
```

<h2>Using ps to Select and Sort Processes</h2>

```bash
ping localhost > /dev/null &           # Start ping in the background
ps                                     # View current shell processes

ps -e                                  # List all processes on the system
ps -o pid,tty,time,%cpu,cmd            # Show selected columns: PID, TTY, TIME, %CPU, CMD
ps -o pid,tty,time,%mem,cmd --sort %mem # Sort processes by memory usage

free                                   # View overall system memory usage

kill 138                               # Stop the background ping process
jobs                                   # Verify the ping process has been terminated
```

<h2> Viewing System Logs</h2>

```bash
ls /var/log                             # List all system log files

ssh localhost                            # Attempt SSH login to generate log entries
# Type responses at prompts:
#   yes (to accept host key)
#   abc (three times as password, to simulate failed login)

tail -5 /var/log/auth.log               # View the last 5 lines of the auth.log file
# Shows recent authentication attempts, including failures
```