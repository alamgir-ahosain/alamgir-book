
<h1>Virtual Machine vs Container</h1>

- A hypervisor lets run multiple virtual machines on one physical machine by virtualizing hardware.
- Container Engine is what unpacks the container file and handle them off to the operating system kernel. 


![ Virtual Machine vs Container](<image/container-vs-vm.png>)


| Feature        | Virtual Machine (VM)                                 | Container                                      |
| -------------- | ---------------------------------------------------- | ---------------------------------------------- |
| OS Dependency  | Each VM has its **own full OS** → heavier and slower | Must use the **same OS kernel** as host        |
| Resource Usage | High (CPU, RAM, storage)                             | Low, but limited by host resources             |
| Crash Impact   | VM isolated → host crash usually does not affect VM  | If **host OS crashes**, all containers go down |
| OS Flexibility | Can run **different OS** on same host                | Cannot run a different OS than host            |
| Technology     | Hypervisor-based                      | Namespace + cgroup based         |
| Use Case       | Multi-OS, strong security             | Microservices, CI/CD, cloud apps |





<h2> ❓ Can virtual machines and containers run on the same machine?</h2>

Yes,Virtual machines and containers can coexist on the same physical server.

- The server runs multiple virtual machines.
- Inside each VM, We can run **containers** (Docker, Kubernetes, etc.).



