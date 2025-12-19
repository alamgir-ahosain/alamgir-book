<h1>The netstat Command</h1>

> Displays **network connections, routing tables, interface stats, and open ports**.

<br>

* **Interface stats:** `netstat -i`
  * Shows RX/TX packets and errors.
  * **TX-ERR** high → possible network issues.

![alt text](image/i.png)

* **Routing table:** `netstat -r`


  * Similar to `route`; shows where packets are sent.

![alt text](image/r.png)

* **Open ports (listening services):**  `netstat -tln`


  * `-t` → TCP, `-l` → listening, `-n` → numeric addresses.
  * Example: port #22 is listening, which means it is open.

![alt text](image/tln.png)

* **Show names instead of numbers:** `netstat -tl`
  

![alt text](image/tl.png)

---
* **Notes:**

  * `netstat` is **obsolete** in many distributions.
  * Replacements:

    * `ss` → network connections
    * `ip route` → routing table
    * `ip -s link` → interface stats
    * `ip maddr` → multicast addresses

