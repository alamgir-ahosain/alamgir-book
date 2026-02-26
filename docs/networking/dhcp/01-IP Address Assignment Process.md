
<h1>How a Computer Gets an IP Address?</h1>

---

<h2> 1. The Role of the NIC (Network Interface Card)</h2>

A computer needs a **NIC** to connect to a network.
Without a NIC, it cannot communicate and therefore has no MAC or IP address.

When a NIC is installed or enabled:

* The computer gets a MAC address.
* It can request and receive an IP address.

>Modern laptops and desktops have a built-in NIC on the motherboard.
 The MAC address belongs to the NIC hardware. If you replace the NIC, the MAC address changes.



<h2> 2. What happens if there is no DHCP server? (APIPA)</h2>

If a computer cannot find a DHCP server, the OS assigns a temporary IP address called **APIPA (Automatic Private IP Addressing)**.

- APIPA Range: 169.254.0.1 to 169.254.255.254.
- APIPA is used **only when DHCP fails**.



<h2> 3. Understanding the Router: LAN vs. WAN</h2>

A router has two main interfaces:

<h3> LAN Interface</h3>

* Connects local devices (computers, phones, etc.)
* Has a private IP address (e.g., 192.168.1.1)
* Acts as the default gateway

<h3> WAN Interface</h3>

* Connects to the Internet Service Provider (ISP)
* Receives a public IP address from the ISP

Most home routers:

* Have a pre-configured LAN IP address
* Automatically obtain the WAN IP from the ISP


<h2>4. What Happens When You Connect a Computer to a Router?</h2>

When you connect a computer to a router using an Ethernet cable:

- The NIC becomes active.
- The computer sends a broadcast message asking:"Is there any DHCP server available?"

>Even if the computer does not yet know the router’s IP or MAC address, it can still send this message using a broadcast.


<h2> 5. How Does the Computer Get an IP? (DORA Process)</h2>

Most routers run a **DHCP (Dynamic Host Configuration Protocol)** server.When a computer connects to a router, it gets an IP using the **DORA process**:

* **D – Discovery** (Computer broadcasts for DHCP server)
* **O – Offer** (Router offers an IP)
* **R – Request** (Computer requests that IP)
* **A – Acknowledge** (Router confirms)

Now the computer has:

* IP address
* Subnet mask
* Default gateway
* DNS server

