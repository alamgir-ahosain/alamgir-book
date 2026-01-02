<h1>run vs exec</h1>

| Feature          | `docker run`                           | `docker exec`                                      |
| ---------------- | -------------------------------------- | -------------------------------------------------- |
| Purpose          | Creates **and starts** a new container | Runs a command in an **already running** container |
| Container state  | Always creates a **new container**     | Uses an **existing running container**             |
| Image required   | Yes (from an image)                    | No (container already exists)                      |
| Typical use      | Start an app or shell                  | Debug, inspect, or manage a container              |
| Interactive mode | Commonly used with `-it`               | Often used with `-it`                              |
| Example          | `docker run -it ubuntu bash`           | `docker exec -it my_ubuntu bash`                   |


