
<h1>What is Docker Engine?</h1>

Docker Engine is the core part of Docker — it handles everything from:

- Running containers
- Managing images
- Building images
- Handling networking & storage for containers


<h1>Docker Engine Architecture</h1>

Docker Engine has three main components:

1. Docker Daemon (dockerd)

      - Core background service of Docker.
      - Builds images and runs containers.
      - Manages networks, volumes, and storage.
      - Listens to Docker CLI / API requests.
      - Handles all container lifecycle operations.

      >The Docker Daemon does all the heavy lifting behind Docker.

2. Docker CLI (docker)	

      - Command-line tool to interact with the Docker Daemon(e.g., docker run, docker ps)

3. REST API	

      - A REST interface that connects the CLI (or any other tool) to the Docker Daemon.


<h1>Types of Container Runtimes Used by Docker</h1>

1. containerd

      - High-level runtime managed by Docker Daemon
      - Handles images, storage, and container lifecycle
      - Interfaces between Docker Daemon and runc

2. runc

      - Low-level runtime that actually runs containers
      - Uses Linux namespaces & cgroups for isolation
      - Follows OCI (Open Container Initiative) standard


>Flow : docker CLI → dockerd → containerd → runc → kernel (namespaces, cgroups)


<h1>How Docker Engine Works </h1>

- Run: docker run hello-docker
- Docker CLI → Sends command to dockerd via REST API.
- dockerd → Checks/pulls image, delegates to containerd.
- containerd → Prepares container, calls runc.
- runc → Creates container process using namespaces & cgroups.
- Container runs → hello-world app executes in isolation.

![ Docker Workflow](<image/docker-ecosystem.png>)


```terminal
alamgir@fedora:~$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.
```

