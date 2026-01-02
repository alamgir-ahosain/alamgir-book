
<h1>WORKDIR</h1>

`WORKDIR` in a Dockerfile sets the **current working directory** for:

* All **RUN** commands
* All **COPY** and **ADD** commands that use **relative paths**
* The **default directory** when a container starts

>In short, it’s like `cd` in Linux—but it persists for the rest of the Dockerfile.
**It’s like saying "Hey Docker, from now on, consider this folder the 'home base' for all my operations".**


---

<h1>Why use it?</h1>

**Keeps paths clean and predictable**<br>
   Without `WORKDIR`, we would have to use **absolute paths everywhere**, which can be messy:

   ```dockerfile
   RUN mkdir here
   COPY ./server.go  .here/server.go
   CMD [ "go", "run","/here/server.go" ]
   ```

   With `WORKDIR`, we can simplify:

   ```dockerfile
   WORKDIR /here
   COPY ./server.go  ./server.go
   CMD [ "go", "run","server.go" ]
   ```


