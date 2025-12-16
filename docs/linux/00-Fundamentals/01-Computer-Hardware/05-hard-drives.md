

<h1>Hard Drives</h1>

* Store data for the operating system and programs.
* Can be connected via **motherboard, PCI card, or USB**.
* Includes HDDs, SSDs, and other storage devices.


<h3>Partitions</h3>

* A **partition** is a logical division of a disk.
* Linux commonly uses **multiple partitions per disk**.
* Helps organize data and system files.



<h3>Partitioning Types</h3>

* **MBR (Master Boot Record)**

    * Older technology.
    * Limited partitions and max size **2 TB**.
    * Tools: `fdisk`, `cfdisk`, `sfdisk`
  
* **GPT (GUID Partition Table)**

    * Newer and more flexible.
    * Supports **larger disks** and more partitions.
    * Tools: `gdisk`, `cgdisk`, `sgdisk`

* **Universal Tools**
    * `parted`, `gparted` (graphical)


<h3>Device Files</h3>

* Stored in the **/dev** directory.
* Disk type prefix:

    * `hd` → IDE disks
    * `sd` → SATA, SCSI, USB disks

<h3>Disk Naming</h3>

* Disk order: `/dev/sda`, `/dev/sdb`, `/dev/sdc`
* Partitions:

    * `/dev/sda1`, `/dev/sda2`, etc.


>Use `lsmod`  command to view the currently loaded modules

<h3> View Disk Devices</h3>

* Command: `ls /dev/sd*`
* Shows disks and their partitions.


<h3> View Partition Details</h3>

* Command: `fdisk -l /dev/sda`
* Displays size, type, and partition layout.
* **Requires root access**.

