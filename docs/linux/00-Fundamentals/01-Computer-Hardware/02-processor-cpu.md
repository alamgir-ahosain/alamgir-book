
<h1>Processors (CPU)</h1>

* CPU (processor) is the **brain of the computer**.
* Executes programs and performs calculations.
* Installed directly on the **motherboard**.

<h3>Processor Types</h3>

* **Single processor** → one CPU
* **Multiprocessor** → multiple CPUs
* **Multi-core** → multiple cores in one CPU chip



<h3>CPU Architectures</h3>

* **x86 (32-bit)** → processes 32 bits at a time
* **x86_64 (64-bit)** → processes 64 bits (also supports 32-bit)
* **64-bit advantages**:
    * Uses **more memory**
    * Better performance
    * Improved security



<h3>x86 History</h3>

* Originated by **Intel (8086, 1978)**
* Common generations:
    * i386, i486
    * Pentium (i586)
    * Pentium Pro (i686)

* Other makers: **AMD, Cyrix**
* Many Linux distros support **i686 or newer**



<h3>Modern Systems</h3>

* Most modern CPUs are **x86_64**
* Some software is still **32-bit**

<h3>Check CPU Architecture</h3>

```bash
arch
```

**Example output:**

```text
x86_64
```

<h3>View Detailed CPU Info</h3>

```bash
lscpu
```

Shows:

* Architecture (32/64-bit)
* Number of CPUs
* Cores and threads
* Vendor (Intel/AMD)
