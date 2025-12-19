<h1>The route Command</h1>

* A **router (gateway)** connects different networks and directs network traffic.
* The **`route` command** displays the **kernel IP routing table**, showing where packets are sent.


Example : 
![alt text](image/route1.png)

* **192.168.1.0** → Local network; packets sent **directly** (* no gateway).
* **default / 0.0.0.0** → All other destinations; packets sent to **router** at `192.168.1.1`.


<h3> Numeric View</h3>

* Use `-n` to show **IP addresses only**:

![alt text](image/route2.png)

* **0.0.0.0** = default route (all other machines).

---

<h3>Modern Replacement</h3>

* `route` is **deprecated** in many Linux distributions.
* Use **`ip route show`** instead:

![alt text](image/route3.png)

* `default via 192.168.1.254` → router for all external traffic.
* `192.168.1.0/24` → local network, directly reachable.

