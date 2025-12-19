

<h1>Linux Shutdown Command</h1>

The **`shutdown`** command safely powers off or restarts the system.
It warns all logged-in users and blocks new logins during the final 5 minutes.



Basic Syntax :  `shutdown [OPTIONS] TIME [MESSAGE]`


<h3>TIME formats</h3>

* `now` → shutdown immediately
* `hh:mm` → shutdown at a specific time
* `+minutes` → shutdown after a delay

>Requirement : The `shutdown` command needs **administrative/root access**.

Example : 

```bash
shutdown now                    # Shutdown right now
shutdown 01:51                  # Shutdown at 01:51
shutdown +1 "Goodbye World!"    # Shutdown after 1 minute with a custom message 
date                            # Check system time (often UTC)
```