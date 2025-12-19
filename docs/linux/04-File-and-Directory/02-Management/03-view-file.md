
<h1>Viewing Files</h1>


| Command  | Purpose                  | Best For          | Key Features                                                                                        |
| -------- | ------------------------ | ----------------- | --------------------------------------------------------------------------------------------------- |
| **cat**  | Display entire file      | Small files       | - cat = concatenate <br>- Shows full content at once<br>- No scrolling<br>- Simple and fast                                 |
| **less** | View file with scrolling | Large files       | - Scroll up/down<br>- Search (`/word`)<br>- Does not load whole file at once<br>- Exit with `q`     |
| **more** | View file page-by-page   | Medium files      | - Scroll forward only<br>- Limited backward navigation<br>- Older pager (less advanced than `less`) |
| **head** | Show first few lines     | Quick preview     | - Default: shows first **10 lines**<br>- Can set number: `head -n 20 file`                          |
| **tail** | Show last few lines      | Logs / last lines | - Default: last **10 lines**<br>- Live updates with `tail -f file`                                  |



Structure:
```bash
cat [OPTIONS] [FILE]
less [OPTIONS] FILE
more [OPTIONS] FILE
head [OPTIONS] [FILE]
tail [OPTIONS] [FILE]
head -n number_of_lines filename
tail -n number_of_lines filename
```

Examples:
```bash
cat alphabet.txt          # Display entire file
less alphabet.txt         # View file with scrolling 
more alphabet.txt         # View file with scrolling, older/limited version
head alphabet.txt         # Show first 10 lines by default
tail alphabet.txt         # Show last 10 lines by default
head -n 5 alphabet.txt    # Show first 5 lines of the file
tail -n 5 alphabet.txt    # Show last 5 lines of the file
```

<h2>Command Line Pipes  ( | )</h2>

* `|` sends output of one command as input to another.
* Helps filter and refine large outputs.
* Commands run left → right; order matters.
* Multiple pipes can be chained.

**Examples:**

```bash
ls /etc | head               # show first 10 entries
ls /etc/ssh | nl             # number all lines
ls /etc/ssh | nl | tail -5   # number first, then show last 5
ls /etc/ssh | tail -5 | nl   # take last 5, then number 1–5
```

---
```bash
ls /etc/ssh | nl
```
* `ls /etc/ssh` → show files
* `|` → pass output
* `nl` → number each line

Example:

```text
1  ssh_config
2  ssh_config.d
3  sshd_config
```

Used to **count files** or **reference them by number**.
