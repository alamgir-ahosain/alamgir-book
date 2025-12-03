<h1>What is a Docker Container?</h1>

A container is an isolated environment that runs on top of the host operating system using Docker’s container engine. It shares the OS kernel but runs independently — lightweight and faster than VMs.




<h3> How It Works</h3>

- Start with a Docker image (blueprint).
- When Run Docker image → Docker creates a container.
- The container runs the app in isolation but can still communicate with the outside world if configured.


<h3>Key Features</h3>

- Isolation :	Each container runs in its own environment.
- Portability :	Runs the same way on any machine with Docker.
- Lightweight :	Shares OS kernel — faster than VMs.
- Reproducible :	Same image = same behavior everywhere.
- Disposable :	Easy to start/stop/remove



<h3>Common Commands</h3>

| Command                    |  Function         |
| --------------------------- | ------------------- |
| docker create           |  Create a container but don’t start it.  |
|  docker run    |   Create & start container  |
| docker start    |  Start existing one  |
| docker stop    |  Stop running container  |
| docker rm    |  Remove a stopped container  |
| docker logs    |  View container logs.  |
| docker exec -it <container> bash    |  Access the container shell.    |

<h1>Docker Desktop</h1>

- All-in-one app for Windows/macOS to run Docker.
- Provides Docker Engine, CLI, GUI dashboard, and optional Kubernetes.
- Uses a lightweight Linux VM to run containers on non-Linux OS.
- Easy setup, manage images/containers, integrates with VS Code/WSL2.

> Docker Desktop = Docker + GUI + Linux VM for easy container management.




<h2>Architecture</h2>


![ Docker Engine for Linux ](<image/linux-docker.png>)
<br><br>
![ Docker Engine for other OS ](<image/linux-other.png>)