
<h1>1. Docker Basic Workflow (Ubuntu Example)</h1>

1. Pull Ubuntu Image from Docker Hub
   ![alt text](image/w1.png)

2. Verify Downloaded Docker Images
   ![alt text](image/w2.png)

3. Run Ubuntu Container in Interactive Mode
   ![alt text](image/w3.png)

4. List All Containers (Running + Stopped)
   ![alt text](image/w4.png)

5. Create a Named Ubuntu Container
   ![alt text](image/w5.png)

6. Access a Running Container Using Name
   ![alt text](image/w6.png)

---

<h1>2. Create a Custom Docker Image</h1>

<h3>Step 1: Create a Dockerfile</h3>

```dockerfile
FROM ubuntu:24.04
RUN echo "Hello Alamgir" > /hello.txt
CMD ["cat", "/hello.txt"]
```

<h3> Step 2: Build the Image</h3>

```bash
docker build .
docker build -t custom_ubuntu . # assigns a name (tag) to the image
```

![alt text](image/cd1.png)
![alt text](image/cd2.png)
![alt text](image/cd3.png)
![alt text](image/cd4.png)

<h3>Step 3: Run the Custom Image</h3>

```bash
docker run custom_ubuntu
```

![alt text](image/cd5.png)
