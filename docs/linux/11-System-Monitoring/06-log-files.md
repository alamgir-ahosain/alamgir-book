<h1> Log Files </h1>

* Logs track system and process activity; stored in `/var/log`.
* Modern daemon: `rsyslogd` or `journald` (systemd).
* Logs can be rotated; binary logs: `/var/log/wtmp`, `/var/log/btmp`.
* Common log files:

  * `boot.log` – startup services messages
  * `cron` – cron job messages
  * `dmesg` – kernel boot messages
  * `maillog` – mail daemon messages
  * `messages` – general kernel/process messages
  * `secure` – authentication/authorization messages
  * `journal` – systemd journal logs
  * `Xorg.0.log` – GUI server messages
* Binary logs: `/var/log/wtmp`, `/var/log/btmp` → use `last` or `lastb` to view.

**Commands:**

```bash
cat /var/log/messages   # View log file contents
less /var/log/secure    # Scroll/search log file
journalctl              # View systemd journal logs
file /var/log/wtmp      # Check if log file is binary
last                    # View login records from /var/log/wtmp
sudo lastb              # View failed login attempts from /var/log/btmp
```


