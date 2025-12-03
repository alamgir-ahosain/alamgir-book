<h1>Virtual Machine (VM)</h1>

A Virtual Machine is a full computer inside another computer.
Key points:

- Runs a full OS (with its own kernel)
- Uses a hypervisor to virtualize CPU, RAM, storage
- Heavy but fully isolated
- Each VM has its own operating system
- Each VM can run a different OS from the host or from other VMs.

>Use cases: multi-OS environments, high security, legacy apps.


![ Virtual Machine](<image/virtual_machine.png>)

<h2>Why Use a Hypervisor? </h2>

>A hypervisor lets run multiple virtual machines on one physical machine by virtualizing hardware.

use a hypervisor because it provides:

- Virtualizes hardware to run multiple VMs on one machine
- Shares resources (CPU, RAM, Disk) efficiently ( **Balloing Technique**)
- Strong isolation between VMs for security
- Run multiple OS on the same hardware
- Supports snapshots & cloning for testing and backups
- Flexible resource management for each VM
- Improves hardware utilization by consolidating workloads