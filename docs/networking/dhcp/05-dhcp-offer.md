

![alt text](dhcp-offer.png)


1. **Application Layer:**

    - Contains assigned IP (`192.168.1.10`), subnet mask, gateway (`192.168.1.1`)
    -  Includes client MAC (`chaddr`) so the client knows the offer is for it

2. **Transport Layer:**

    - Source Port 67: The Router (Server).
    - Destination Port 68: The Computer (Client).

3. **Network:**

    - Source IP: 192.168.1.1 router’s LAN IP (gateway)
    - Destination IP: 255.255.255.255 (broadcast ip, because the client has no IP yet)

4. **Data Link Layer (MAC)**

    - Source MAC: A1:B1:C1:D1:E1:F1
    - Destination MAC: Broadcast (FF:FF:FF:FF:FF:FF)

5. **Physical Layer & NIC**

    * NIC converts frame  to electrical/wireless signals and sent on network.



> Broadcast ensures delivery to clients without IP; `chaddr` + `xid` ensures correct matching.


<h3>Summary Table: How the Client Processes the DHCP Offer</h3>

| Layer | Information Checked | Other Devices (Phones, etc.) | The Client (Your Computer) |
| --- | --- | --- | --- |
| **Data Link** | MAC: `FF:FF:FF:FF:FF:FF` | "It's a broadcast, I'll take it." | "It's a broadcast, I'll take it." |
| **Network** | IP: `255.255.255.255` | "It's a broadcast, keep going." | "It's a broadcast, keep going." |
| **Transport** | **Port: 68** | **"I'm not looking for an IP. DROP."** | **"I am waiting for an IP! ACCEPT."** |
| **Application** | **chaddr:** `A:B:C:D:E:F` | (Already dropped at Transport) | **"That's MY MAC address! This is MY offer!"** |

