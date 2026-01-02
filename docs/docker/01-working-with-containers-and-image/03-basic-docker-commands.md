<h1>Docker Command</h1>

---
<h3>  Docker Images</h3>

```bash
docker images        # Lists all locally available images
docker rmi           # deletes unused images to free disk space.
docker rmi <id>      # Remove a specific image
docker rmi -f <id>   # Force remove a specific image
```

<h3>Docker Containers</h3>

```bash
docker ps            # Show running containers
docker ps -a         # Show all containers (running + stopped)
```

<h3>Managing Container</h3>

```bash
docker start <CONTAINER_NAME>       # Start an existing container
docker stop <CONTAINER_NAME>        # Stop a running container
docker restart <CONTAINER_NAME>     # Restart a running container
docker rm <CONTAINER_NAME>          # Remove a stopped container
docker rm -f <CONTAINER_NAME>       # Forcefully remove a container (stops it if running)
```

<h3> Pulling and Running an Image</h3>

```bash
docker pull ubuntu:24.04         # Downloads  image (if not already present)

docker run -it ubuntu:24.04 bash # Running Containers with bash Shells
docker run -it ubuntu:24.04 sh   # Running Containers with lightweight Shells
```

<h3>Naming Containers</h3>

```bash
docker run --name my_ubuntu -it ubuntu:24.04 bash
```

**Why name containers?**

- Easier to manage containers
- Avoids remembering container IDs

