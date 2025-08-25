# 🐳 Lab 10 – Docker Cleanup and Best Practices (Demo Version)

**Objective:** Practice creating Docker resources and then cleaning them up while learning best practices.

---
### Create Temporary Containers

```bash
docker run -d --name demo-nginx nginx
docker run -d --name demo-httpd httpd
```

### Create a Temporary Volume

```bash
docker volume create demo-volume
docker run -d --name demo-volume-container -v demo-volume:/data nginx
```

### Create a Temporary Network

```bash
docker network create demo-network
docker run -d --name demo-network-nginx --network demo-network nginx
```

### List All Resources

```bash
docker ps -a
docker images
docker volume ls
docker network ls
```

### Stop and Remove Containers

```bash
docker stop demo-nginx demo-httpd demo-volume-container demo-network-nginx
docker rm demo-nginx demo-httpd demo-volume-container demo-network-nginx
```

### Remove Temporary Images 

```bash
docker rmi nginx httpd
```

### Remove Temporary Volume

```bash
docker volume rm demo-volume
```

### Remove Temporary Network

```bash
docker network rm demo-network
```

