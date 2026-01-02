

<h1>Dockerfile Layers Explanation </h1>


<Details>
<summary>Dockerfile</summary>

```dockerfile
FROM ubuntu:24.04
RUN apt update
RUN apt install -y golang
WORKDIR /here
COPY ./server.go ./server.go
CMD ["go", "run", "server.go"]
```
</Details>


![alt text](image/behind-dockerfile.png)

<h2>Layer-by-Layer Explanation</h2>

| Layer       | Dockerfile Instruction         | What happens internally                                                                                                                                            | Notes                                                           |
| ----------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------- |
| **Layer 0** | `FROM ubuntu:24.04`            | - Check Docker cache:<br>  - If image exists locally → load it.<br>  - If not → pull from Docker Hub.<br>- Then loaded Base image.                                     | Base layer for all subsequent layers.                           |
| **Layer 1** | `RUN apt update`               | - Create **temporary container** from Layer 0.<br>- Execute `apt update`.<br>- Commit container as **intermediate image**.<br>- Remove temporary container.        | Layer caches the updated package list.                          |
| **Layer 2** | `RUN apt install -y golang`    | - Create temporary container from Layer 1.<br>- Execute `apt install -y golang`.<br>- Commit container as **intermediate image**.<br>- Remove temporary container. | Golang is installed and saved in the layer.                     |
| **Layer 3** | `WORKDIR /here`                | - Set working directory for **subsequent instructions**.<br>- Internally creates metadata for image.                                                               | Does not create a real filesystem change.                       |
| **Layer 4** | `COPY ./server.go ./server.go` | - Copy `server.go` from build context into `/here/server.go` in the container.                                                                                     | Creates a new layer with the source file.                       |
| **Layer 5** | `CMD ["go","run","server.go"]` | - Set default command for the container at runtime.                                                                                                                | Does not create a new image layer in most cases, just metadata. |


> **intermediate layers build on top of each other until the final image**.

---

<h1>Why Docker keeps intermediate images?</h1>

* Every command that changes the filesystem (`RUN`, `COPY`, `ADD`) creates a **new intermediate image**.

* These intermediate images are cached for **faster rebuilds**:

    * If you rebuild the image and the previous layers haven’t changed, Docker will **reuse cached layers**.
    * This makes builds faster because Docker doesn’t rerun commands unnecessarily.


* By default:

    * If build **fails**, intermediate images are kept for debugging.
    * If build **succeeds**, Docker may automatically prune intermediate images unless cache is needed.



