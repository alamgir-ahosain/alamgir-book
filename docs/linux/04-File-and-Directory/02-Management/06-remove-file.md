
# **Removing Files (`rm` Command)**

The `rm` command is used to **delete files and directories permanently**.


Command Structure : `rm [OPTIONS] FILE`  
>FILE → file(s) or directory to remove





---


<h2>Important Notes</h2>

* **Permissions Required:**

  * Must have **write (w)** and **execute (x)** permissions on the **directory containing the file**
* Use **caution** — `rm` permanently deletes files
* Recursive removal (`-r` / `-R`) deletes **all subdirectories and files** inside a folder



Examples:
```bash
rm linux.txt              # Remove a single file
rm -r Work/               # Remove a directory and all its contents recursively
rm a.txt b.txt c.txt      # Remove multiple files at once
rm -i important.txt       # Remove a file interactively (ask before deleting)
rm *.log                  # Remove all files with .log extension in the current directory
```

![alt text](image/remove.png)