
<h2>CPU Information</h2>

* Display detailed CPU architecture info: `lscpu`
* Show first 20 lines of `/proc/cpuinfo` (detailed CPU specs): `head -n 20 /proc/cpuinfo`


<h2>Memory Information</h2>

* Display RAM and swap usage in **megabytes**: `free -m`
* Display RAM and swap usage in **gigabytes**: `free -g`



<h2>PCI Devices</h2>

* List all devices on the PCI bus: `lspci`
* List PCI devices **with kernel driver and module info**: `lspci -k`

<h2>USB Devices</h2>

* List all USB connected devices: `lsusb`

<h2>Kernel Modules</h2>

* View currently loaded kernel modules (drivers): `lsmode`


<h2>Disk Devices and Partitions</h2>

* List disk devices and partition tables: `fdisk -l`

