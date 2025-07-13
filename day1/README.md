#  Day 1 — Introduction to Docker

Welcome to Day 1 of the Docker Bootcamp by [LearnWithPrayag](https://learnwithprayag.com)!  
Today, you'll learn **what Docker is**, **why it's essential in DevOps**, and how to **run your first containers** with real-world examples.

---

## What is Docker?

**Docker** is a containerization platform that lets you package applications and their dependencies into a single unit called a **container**.  
This ensures your app **runs the same** in development, staging, or production — whether on your laptop or in the cloud.

---

## Why Docker?

-  **Consistency**: Same environment across all stages (Dev, Test, Prod)
-  **Isolation**: Each app runs in its own container
-  **Portability**: Runs on any OS with Docker Engine
-  **Lightweight**: Containers use fewer resources than VMs
-  **DevOps Ready**: Integrates with CI/CD, Kubernetes, cloud, GitOps

> "Docker is the foundation of modern DevOps and cloud-native development."

---

## 🖥Containers vs Virtual Machines

| Feature            | Container                         | Virtual Machine                   |
|--------------------|------------------------------------|-----------------------------------|
| Boot Time          | Seconds                            | Minutes                           |
| Size               | MBs                                | GBs                               |
| Isolation Level    | Process level                      | Hardware level                    |
| Performance        | Near-native                        | Slightly lower                    |
| Use Case           | Microservices, CI/CD, Dev          | Legacy apps, full OS isolation    |

---

## How Docker Works

1. **Docker Engine**: The runtime installed on your machine.
2. **Images**: Read-only templates (like `nginx:latest`).
3. **Containers**: Live instances of images.
4. **Docker Hub**: Public registry for images.
5. **CLI / API**: Used to interact with Docker engine.

---

##  Installing Docker

- [Install on Linux](https://docs.docker.com/engine/install/ubuntu/)
- [Install on Windows](https://docs.docker.com/desktop/install/windows-install/)
- [Install on macOS](https://docs.docker.com/desktop/install/mac-install/)

Use this command to verify Docker is working:

```bash
docker version
````

---

## Hands-On Commands

```bash
# Pull an image
docker pull alpine

# Run a container in interactive mode
docker run -it alpine sh

# Run a container in detached mode
docker run -d --name web nginx

# List running containers
docker ps

# Stop a container
docker stop web

# Remove a container
docker rm web

# List all containers (including stopped)
docker ps -a

# View all local images
docker images
```

---

## Lab Tasks

Run the following containers:

* Alpine in interactive shell (`sh`)
* Nginx in detached mode
* Redis container for testing

Inspect them using:

* `docker ps`, `docker inspect`, `docker logs`

 Change port mapping

* Change port mappings for Nginx:

  ```bash
  docker run -d -p 8080:80 --name web nginx
  ```

Then access: [http://localhost:8080](http://localhost:8080)

---

##  Key Takeaways

* Docker simplifies app packaging and shipping
* Containers are faster and lighter than VMs
* Docker CLI gives full control over images and containers
* Port mapping (`-p`) connects container ports to your host

---

##  Additional Resources

*  [Docker CLI Reference](https://docs.docker.com/engine/reference/commandline/docker/)
*  [Docker Hub](https://hub.docker.com/)
*  [Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)

---

>  **Congrats!** You’ve just learned the Docker basics.
> Next, we'll dive into **Dockerfiles** and learn how to build your own custom images.

---

