<h1>Loops in shell scripts</h1>


<h2>1. For Loops</h2>

* Iterate over a **finite list** of items (files, names, servers).

 Syntax:
```bash
for VAR in list; do
  commands
done
```

![alt text](image/for.png)
![alt text](image/for2.png)

<h2>2. While Loops</h2>

* Repeat commands **while a condition is true**.

Syntax:
```bash
while [ condition ]; do
  commands
done
```


 **Notes:**

* `for` is best for **known lists**.
* `while` is best for **unknown/conditional repetitions**.
* Use `$(( ))` for arithmetic operations.


![alt text](image/while.png)