
<h1>Networking command</h1>

1. **`ping google.com`** – Checks connectivity to a remote server.


4. **`netstat -tulnp`** – Displays open network connections.
5. **`curl https://example.com`** – Fetches a webpage's content.
6. **`wget https://example.com/file.zip`** – Downloads a file from the internet.


---

<h1>Network Manager</h1>

1.   **`ip a`** – Check IP address 
2. **`nmcli device status`** – Show active network connections 
3.  **`nmcli connection show`**  – View detailed connection info
4.  **`nmcli device show`** – Check if DHCP or Static IP is used
5. **`resolvectl status`** – Check DNS and Gateway 
6.  **`nmcli device wifi list`** – See Wi-Fi details (laptop specific)
7. **`ifconfig`** – Display network configuration information
8. **`ip addr show`** – Modern replacement for `ifconfig`

---

<h1>The route command</h1>

1. **`route`** – Show routing table.
2. **`route -n`** – Show numeric routing table.
3. **`ip route show`** – Modern command to display the routing table with detailed info

---

<h1>The netstat command</h1>

1. **`netstat -i`** – Show network interface statistics (RX/TX packets and errors).
2. **`netstat -r`** – Show kernel IP routing table (similar to `route`).
3. **`netstat -tln`** – Show listening TCP ports with numeric addresses.
4. **`netstat -tl`** – Show listening TCP ports with service names.

---

<h1>The ss command</h1>

10. **`ss`** – Display current socket connections and states (modern replacement for `netstat`).
11. **`ss -s`** – Show summary statistics of all socket types.
3. **`ss | less`** – for easier viewing

--- 

<h1>The dig command</h1>

1. **`dig example.com`** –  Tests DNS server functionality and performs DNS queries

---
<h1>The host command</h1>

1. **`host example.com`** – Resolve a hostname to its IP address.
2. **`host 192.168.1.2`** – Perform a reverse DNS lookup (IP → hostname).
3. **`host -t CNAME example.com`** – Query the CNAME (canonical name) record.
4. **`host -t SOA example.com`** – Query the Start of Authority (SOA) record.
5. **`host -a example.com`** – Display all DNS records for a domain.

---

<h1>The ssh command</h1>

1. **`ssh hostname`** –  Logs in using your current username on the remote host
2. **`ssh username@hostname`** –  Logs in with a specific username

---