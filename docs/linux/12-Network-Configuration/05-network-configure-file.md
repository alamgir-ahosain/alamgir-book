<h1>Network Configuration Files</h1>

>**Linux name resolution** relies on three key files: **`/etc/hosts`**, **`/etc/resolv.conf`**, and **`/etc/nsswitch.conf`**.Together, they define **where** and **in what order** to look for hostname information.



<h2> 1. /etc/hosts</h2>

* Contains a **table of hostnames and their IP addresses**.
* Can **supplement DNS** for name resolution.
* Example:

  ```bash
  127.0.0.1   localhost
  ```
* **Lookups** in this file are **checked first** if `/etc/nsswitch.conf` prioritizes `files`.


<h2>2. /etc/resolv.conf</h2>

* Stores **DNS server IP addresses** for hostname resolution.
* Can include **additional keywords** like `domain` and `search`.
* Example:

  ```bash
  nameserver 10.0.2.3
  nameserver 10.0.2.4
  ```
* Resolution process:

  1. Tries the **first nameserver**.
  2. If unavailable or timeout, tries the **second nameserver**.
* **Keywords:**

    * `domain`: Appends the domain for partial hostnames (e.g., `polaris` → `polaris.snowblower.example.com`).
    * `search`: Lists multiple domains to try in order for name resolution.


<h2> 3. /etc/nsswitch.conf</h2>

* Configures **the order of hostname lookup sources**.
* Example entry:

  ```text
  hosts: files dns
  ```

  * `files` → `/etc/hosts` is checked first.
  * `dns` → DNS server(s) in `/etc/resolv.conf` are used second.
* Order affects resolution behavior:

  * If a hostname is found in `/etc/hosts`, DNS may **not be used**, even if the IP is incorrect.

---

<h2>Name Resolution Flow</h2>

1. System consults **`/etc/nsswitch.conf`** to determine lookup order.
2. Checks **`/etc/hosts`** for a matching entry.
3. If no match, queries the **DNS server(s)** listed in **`/etc/resolv.conf`**.
4. Result is cached for a configurable period.


