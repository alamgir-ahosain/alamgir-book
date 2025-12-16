
<h1>Buses</h1>

* A **bus** is a high-speed connection for communication.
* Connects **CPU, RAM, and other components**.
* Located on the **motherboard**.



<h3>Common Bus Types</h3>

* **PCI (Peripheral Component Interconnect)**
    * Used for internal devices (network, video, storage cards).
* **USB (Universal Serial Bus)**
   * Used for external devices (keyboard, mouse, printer, storage).



<h3>Desktop / Server Systems</h3>

* CPU and RAM attached directly to motherboard.
* Expansion cards connect via **PCI slots**.
* Devices can be **upgraded or replaced**.



<h3>Laptop / Small Form Factor Systems</h3>

* Most components are **built into the motherboard**.
* Bus still exists but **upgrades are limited**.



<h3>Peripheral Devices</h3>

* Devices for **input, output, or storage**.
* Examples: keyboard, mouse, monitor, printer, hard disk.



<h3>View PCI Devices</h3>

* Command: `lspci`
* Shows video, storage, and network controllers.


<h3> USB(Universel Serial Bus) Devices</h3>

* External peripherals use **USB bus**.
* **Hot-plug** supported (no shutdown required).
* Always **unmount storage** before removal.
 **View USB Devices** :  `lsusb` ;  Lists all connected USB devices.

![alt text](image/buses.png)