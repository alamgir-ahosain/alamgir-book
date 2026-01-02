<h1>Container vs Image</h1>

| Feature         | Docker Image                                        | Docker Container                      |
| --------------- | --------------------------------------------------- | ------------------------------------- |
| What it is      | A **blueprint / template** for running applications | A **running instance** of an image    |
| State           | Read-only                                           | Read–write                            |
| Created from    | Dockerfile or another image                         | Docker image                          |
| Can be modified |  No                                                | Yes                                 |
| Purpose         | Used to create containers                           | Runs applications                     |
| Lifecycle       | Built → Stored → Shared                             | Created → Running → Stopped → Removed |
| Example         | `ubuntu:24.04`                                      | `my_ubuntu`                           |
