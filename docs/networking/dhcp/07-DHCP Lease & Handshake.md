

<h2> DHCP Lease Table – Quick Overview</h2>

The **Lease Table** is the router’s record of which IPs are “rented” and to whom.

| Column              | What It Shows                 | Example               |
| ------------------- | ----------------------------- | --------------------- |
| **IP Address**      | Assigned address              | `192.168.1.10`        |
| **MAC Address**     | Device hardware ID            | `A:B:C:D:E:F`         |
| **Hostname**        | Device name                   | `DESKTOP-PC1`         |
| **Lease Start/End** | When IP was given & expires   | `2024-05-20 10:00:00` |
| **Lease Type**      | Dynamic (temporary) or Static | `Dynamic`             |

**Key Points:**

* Devices **rent** IPs; they don’t own them.
* The router checks the table to **avoid IP conflicts**.
* During **DORA**, IPs go **Pending** at Offer and **Locked** at ACK.


---

<h2>DHCP “Secret Handshake” (How Client & Server Recognize Each Other)</h2>

| Feature                  | Purpose                                                                       |
| ------------------------ | ----------------------------------------------------------------------------- |
| **Transaction ID (xid)** | Random code from client : must match in server’s Offer/ACK. Prevents mix-ups. |
| **DHCP Message Type**    | Labels the packet: Discover (1), Offer (2), Request (3), ACK (5).             |
| **UDP Ports 67/68**      | Only server (67) and client (68) listen ; ignores other traffic.              |
| **chaddr (MAC)**         | Ensures server assigns IP to the correct NIC.                                 |

