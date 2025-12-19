<h1>Kernel Messages</h1>

* `/var/log/dmesg` → Kernel messages during startup.
* `/var/log/messages` → Kernel + daemon/process messages while running.
* Kernel messages can also be viewed in the ring buffer with `dmesg`.
* Buffer may overflow; older messages can be lost.
* Filter output with `grep` or `less` for easier reading.

**Commands:**

```bash
dmesg                    # View kernel ring buffer
dmesg | less             # Scroll through messages
dmesg | grep -i usb      # Search for USB-related messages
```
