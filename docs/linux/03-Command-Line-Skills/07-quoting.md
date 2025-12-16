
<h1>Quoting</h1>

Quotes modify how the shell interprets text.
Three  types of quotes for Bash shell

<h2>1. Double quotes</h2>

*  prevents most special characters from being interpreted.
* Glob characters ( `* ? [ ]` ) inside quotes are trated  literallly.
* Allows variable and command substitution.
* Example :

  ```bash
  echo "The glob characters are *, ? and [ ]"
  # Output: The glob characters are *, ? and [ ]

  echo "The path is $PATH"
  # Output: The path is /usr/bin/custom:/home/sysadmin/bin:...
  ```


<h2>2. Single quotes</h2>

*  prevents the shell from interpreting **any** special characters.
* **Variables**, **command substitution,** and **globs** are treated literally.

Example  : 
```bash
 echo The car costs $100    # The car costs 00
 echo 'The car costs $100'  # The car costs $100
```

<h2>Escape Character</h2>

* `\` escapes a single character, preventing the shell from interpreting it.
* Useful when mixing literal characters and variables in the same string.
* Example:

```bash
echo "The service costs $1 and the path is $PATH"
#‌⁠​​⁠​The service costs  and the path is /usr/bin/custom:/home/sysadmin/bin:...

echo 'The service costs $1 and the path is $PATH' 
#The service costs $1 and the path is $PATH 

echo The service costs \$1 and the path is $PATH
# Output: The service costs $1 and the path is /usr/bin/custom:/home/sysadmin/bin:...

echo This is the command \`date\`     
# This is the command `date`  
```

<h2>3. Back quotes</h2>

perform  **command substitution** (execute a command and use its output).


Example:

```bash

  date
 # Thu Dec 11 05:55:43 UTC 2025                                                    

  echo Today is date                               
  #Today is date

  echo Today is `date`
  echo Today is $(date)
  # Output: Today is Thu Dec 11 05:55:43 UTC 2025             
  
  echo This is the command "`date`"               
  # This is the command Thu Dec 11 05:55:43 UTC 2025     
```


---
>* **Double quotes `"`** – preserve literal text but allow variable and command substitution.
>* **Single quotes `'`** – preserve text exactly as typed, no substitution.
>* **Back quotes `` ` ``** – execute the command inside and replace with its output.
