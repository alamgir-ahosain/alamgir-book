<h1>Understanding the -it Flags</h1>

| Flag | Meaning     | Purpose                           |
| ---- | ----------- | --------------------------------- |
| `-i` | Interactive | Keeps STDIN open for user input   |
| `-t` | TTY         | Provides terminal-like formatting |

**Example command** `docker run -it ubuntu:24.04 bash`

**Command breakdown:**

- `docker run` → Create and start a container
- `-it` → Interactive terminal mode
- `ubuntu:24.04` → Base image
- `bash` → Program to run inside the container

---
<h1>Detached vs  Interactive Mode</h1>

| Feature               | Detached Mode (`-d`)                                        | Interactive Mode (`-it`)                                           |
| --------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------ |
| **Meaning**           | Runs container in the **background**                        | Runs container in the **foreground** with **interactive terminal** |
| **Command Example**   | `docker run -d ubuntu`                                       | `docker run -it ubuntu bash`                                       |
| **Terminal Behavior** | Terminal is **free immediately**                            | Terminal is **attached to container** and blocked until exit       |
| **Logs/Output**       | Logs not shown automatically; use `docker logs <container>` | Logs/output **shown live in terminal**                             |
| **Use Case**          | Running services (web server, DB)                           | Debugging, testing, or running commands interactively              |
| **Exit Behavior**     | Container keeps running until stopped explicitly            | Container stops when you exit the terminal (unless `--rm` is used) |
| **Attach Later**      | Can attach later with `docker attach <container>`           | Already attached; no need to attach                                |



 **Notes:**  We can combine modes:

```bash
docker run -dit ubuntu
```

* `-d` = detached
* `-i` = interactive
* `-t` = terminal
* This runs in the background **but keeps STDIN open**, useful for background containers you might exec into later.
