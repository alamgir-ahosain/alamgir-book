<h1>Shell Script Conditionals</h1>


<h2>1. If else</h2>
-  `if` :   Executes commands if the exit code of a command is `0`
- `if-else` :  Provides an alternative if condition fails:
- `if-elif-else` :  Tests multiple conditions



<h2>2. test / [ ]  operators</h2>


These are same : 
```bash
if test –f /tmp/foo; then
if [ -f /tmp/foo ]; then
```

 File and directory checks:
```bash
[ -f /tmp/foo ]    # file exists
[ ! -f /tmp/foo ]  # file not exists
[ -d /tmp ]        # directory exists
[ -x `which ls` ]  # executable exists
```
Numeric and string comparisons:

```bash
[ 5 -eq 5 ]       # numeric equality
[ !5 -eq 5 ]      # numeric not equality
[ 5 -ne 5 ]       # numeric inequality

[ "a" = "a" ]     # string equality
[ "a" != "a" ]    # string different

[ 1 -ne 2 -a 3 -eq 3 ] # AND :  both must be the same
[ 1 -eq 1 -o 2 -eq 3 ] # OR :  either can be the same
```
![](image/ifelse.png)

<h2>3. case statement</h2>

* Pattern matching alternative to multiple `elif`s:


* `|` → OR multiple options
* `*` → default (else)
* `;;` → end of each block


![alt text](image/case.png)