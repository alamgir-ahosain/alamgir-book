

When a computer connects to a router, the OS does **not** know:

* The router’s IP address
* The router’s MAC address

So how does it request an IP?

> The Answer: **Broadcast**

The computer sends a **broadcast message** on the local network.
During the first step of DHCP (Discovery), the computer sends a message to:

```
IP address: 255.255.255.255
MAC address: FF:FF:FF:FF:FF:FF
```

This is called a **broadcast address**  
meaning:
> All devices on this local network, please listen.

The router (DHCP server) receives this broadcast and replies.
