
<h1>Command Types</h1>

* Commands in the shell come from **different sources**.
* Use the `type` command to check **where a command comes from**.
**Example** ` type command_name`  ; tells whether it is **internal**, **external**, **alias**, or **function**



<h2>Command Sources</h2>

<h3> 1.  Internal Commands </h3>

Key Points

* Internal commands = **built into the Bash shell**.
*  **do NOT require** starting a separate program.
* Shell already knows how to run them.
* Bash executes it directly.
* use `type` to check a check is internal.
* Example: `cd`, `echo`, `pwd`, `history`

**Example:** `type cd`
**Output:** cd is a shell builtin



<h3> 2. External Commands</h3>

* Stored outside the shell (not built-in).
* Shell searches **$PATH** to find them.
* Can run them using **full path**.



<h2> Useful Commands & Examples</h2>


| Purpose                               | Command        | Output / Meaning              |
| ------------------------------------- | -------------- | ----------------------------- |
| Find full path of a command           | `which ls`     | `/bin/ls`                     |
| Check full path for another command   | `which cal`    | `/usr/bin/cal`                |
| Run command using full path           | `/bin/ls`      | Executes `ls` directly        |
| Show how shell interprets the command | `type cal`     | `cal is /usr/bin/cal`         |
| Difference (builtin vs external)      | `type echo`    | `echo is a shell builtin`     |
|                                       | `which echo`   | `/bin/echo`                   |
| Show all locations of a command       | `type -a echo` | Shows builtin + external path |


<h2>3. Aliases</h2>

* Map a longer commands to shorter sequences.
* Shell substitutes alias with full command before execution.
* Each shell has its own aliases; new shells don’t inherit them.
* View current aliases: `alias`
* Create new alias: `alias name="command"`
* Identify aliases : `type`

![alt text](image/alias.png)
![alt text](image/alias2.png)

<h2> 4. Functions</h2>

* Combine multiple commands into a single callable unit.
* Can create new commands or override existing ones.
* Usually defined in shell scripts or initialization files.
* Execute the function by typing its name.

Syntax:

  ```bash
  function_name () {
      commands
  }
  ```

![alt text](image/function.png)

---

>* **Internal commands** – Built into the shell
>* **External commands** – Stored as files in system directories
>* **Aliases** – Custom shortcuts for commands
>* **Functions** – User-defined command blocks inside the shell





