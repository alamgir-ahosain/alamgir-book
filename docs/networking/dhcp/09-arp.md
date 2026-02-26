<h1>Address Resolution Protocol (ARP)</h1>


**ARP** is a protocol that finds a device’s **MAC address** when its **IP address** is known inside a local network.



<h3>Why ARP is Needed</h3>

* **Layer 3 (Network layer)** uses **IP address**
* **Layer 2 (Data Link layer)** uses **MAC address**

When sending data on a LAN:

* The device knows the **destination IP**
* But it must know the **destination MAC**
* So it sends an **ARP request**

---

![alt text](switch-router-hub.png)
![alt text](a-to-h.png)



<h2>Summary Table: Packet Journey & Table Updates (A to H)</h2>


| Device | Incoming Port | Layer Logic & Action | Result / Outgoing Ports | CAM Table Update | ARP Table Update |
| --- | --- | --- | --- | --- | --- |
| **Computer A** | - | Generates ARP Request: "Who is 192.168.1.16?" | Out: **Port 1** | - | (Waiting for H) |
| **Hub-1** | Port 1 | Physical Layer: Repeats signal to all ports. | Out: **2, 3, 4** | None (Hub) | - |
| **Computer B & C** | - | Check Dest. MAC (Broadcast) and Target IP. | **DROP** | - | **Learns MAC A** |
| **Hub-2** | Port 5 | Physical Layer: Repeats signal to all ports. | Out: **6, 7** | None (Hub) | - |
| **Computer D** | - | Check Dest. MAC (Broadcast) and Target IP. | **DROP** | - | **Learns MAC A** |
| **Switch-1** | **Port 8** | **Learning:** Sees MAC A on Port 8. **Forwarding:** Floods. | Out: **9, 10, 11** | **MAC A → Port 8** | - |
| **Router (E)** | Port 11 | Check Dest. MAC (Broadcast) and Target IP. | **DROP** | - | **Learns MAC A** |
| **Computer F** | Port 10 | Check Dest. MAC (Broadcast) and Target IP. | **DROP** | N/A | **Learns MAC A** |
| **Hub-3** | Port 12 | Physical Layer: Repeats signal to all ports. | Out: **13, 14** | None (Hub) | - |
| **Computer G** | Port 13 | Check Dest. MAC (Broadcast) and Target IP. | **DROP** | - | **Learns MAC A** |
| **Switch-2** | **Port 15** | **Learning:** Sees MAC A on Port 15. **Forwarding:** Floods. | Out: **16** | **MAC A → Port 15** | - |
| **Computer H** | Port 16 | **Match!** IP is 192.168.1.16. | **ACCEPT & REPLY** | - | **Learns MAC A** |






<h2>Summary Table: Packet Journey & Table Updates (H to A)</h2>

| Device             | Incoming Port | Action / Layer Logic                                | Outgoing Port(s) | CAM Table (Current State)          | ARP Table (Current State)                    |
| ------------------ | ------------- | --------------------------------------------------- | ---------------- | ---------------------------------- | -------------------------------------------- |
| **Computer H**     | -             | Creates **Unicast ARP Reply** (Dest MAC = A)        | Port 16          | -                                  | 192.168.1.10 → **MAC A**                     |
| **Switch-2**       | Port 16       | Learns **MAC H → Port 16**. Looks up MAC A.         | Port 15          | MAC A → Port 15<br>MAC H → Port 16 | -                                            |
| **Hub-3**          | Port 14       | Physical layer repeat (broadcast electrical signal) | Ports 12, 13     | -                                  | -                                            |
| **Computer G**     | Port 13       | Destination MAC ≠ G → Frame discarded               | DROP             | -                                  | 192.168.1.10 → MAC A<br>192.168.1.16 → MAC H |
| **Switch-1**       | Port 9        | Learns **MAC H → Port 9**. Looks up MAC A.          | Port 8           | MAC A → Port 8<br>MAC H → Port 9   | -                                            |
| **Hub-2**          | Port 7        | Repeats signal to all ports                         | Ports 5, 6       | -                                  | -                                            |
| **Computer D**     | Port 6        | Destination MAC ≠ D → Frame discarded               | DROP             | -                                  | 192.168.1.10 → MAC A<br>192.168.1.16 → MAC H |
| **Hub-1**          | Port 4        | Repeats signal to all ports                         | Ports 1, 2, 3    | -                                  | -                                            |
| **Computer B & C** | Ports 2, 3    | Destination MAC ≠ B/C → Frame discarded             | DROP             | -                                  | 192.168.1.10 → MAC A<br>192.168.1.16 → MAC H |
| **Computer A**     | Port 1        | Destination MAC = A → Frame accepted                | ACCEPT           | -                                  | 192.168.1.16 → MAC H                         |

