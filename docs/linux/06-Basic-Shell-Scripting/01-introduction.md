
<h2>Shell Script</h2>

* A **shell script** is a text file containing **executable commands**.
* Scripts can automate repetitive tasks and **change behavior** based on conditions.

Example of a simple script:

  ```bash
  echo "Hello, World!"
  ```
Run a script with:

  ```bash
  sh script.sh      # via shell
  ./script.sh       # directly (needs execute permission)
  ```

<h3>Shebang (#!) specifies the interpreter for the script</h3>

  ```bash
  #!/bin/bash
  echo "Hello, World!"
  ```
* Shebang works for shells and other scripting languages (Python, Perl, Ruby).
* Always create scripts in **plain text**, not formatted office documents.
