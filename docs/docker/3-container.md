<h1>Container</h1>

A container is a lightweight, isolated environment that runs an application with all its dependencies.
It uses:

- Namespaces → to isolate what the app can see
- cgroups → to control what the app can use

>A container = isolated process + packaged dependencies + shared OS kernel.

<h3> 1. Namespaces </h3>

Namespaces isolate **what a process can see**.They create separate “views” of system resources.

**Types of namespaces:**

* **PID** → isolates process IDs
* **NET** → separate network (IP, ports, routing)
* **MNT** → separate filesystem mount points
* **UTS** → separate hostname/domain name
* **IPC** → isolates shared memory & message queues
* **USER** → isolates user/group IDs inside container


>Namespaces = *visibility isolation* → each container sees its own OS world.



<h3>2. cgroups - Control Groups  </h3>

cgroups (control groups) **limit what a process can use**.They control resource consumption.

**What cgroups manage:**

* CPU usage
* Memory limits
* Disk I/O
* Network bandwidth
* Process limits


>cgroups = resource control → prevent one container from using too much CPU/RAM.

