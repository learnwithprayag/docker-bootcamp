# 🐳 Lab 10 – Docker Cleanup and Best Practices (Demo Version)

**Objective:** Practice creating Docker resources and then cleaning them up while learning best practices.

---

## Lab 10: Part A – Ubuntu/Linux

### Step 1: Create Temporary Containers

```bash
docker run -d --name demo-nginx nginx
docker run -d --name demo-httpd httpd
```

### Step 2: Create a Temporary Volume

```bash
docker volume create demo-volume
docker run -d --name demo-volume-container -v demo-volume:/data nginx
```

### Step 3: Create a Temporary Network

```bash
docker network create demo-network
docker run -d --name demo-network-nginx --network demo-network nginx
```

### Step 4: List All Resources

```bash
docker ps -a
docker images
docker volume ls
docker network ls
```

### Step 5: Stop and Remove Containers

```bash
docker stop demo-nginx demo-httpd demo-volume-container demo-network-nginx
docker rm demo-nginx demo-httpd demo-volume-container demo-network-nginx
```

### Step 6: Remove Temporary Images (Optional)

```bash
docker rmi nginx httpd
```

### Step 7: Remove Temporary Volume

```bash
docker volume rm demo-volume
```

### Step 8: Remove Temporary Network

```bash
docker network rm demo-network
```

### Step 9: Apply Best Practices (Recap)

* Use minimal images (Alpine)
* Tag images properly
* Multi-stage builds for smaller images
* Avoid running containers as root
* Limit CPU/memory per container
* Regularly prune unused resources

---

## Lab 10: Part B – Windows (Docker Desktop / PowerShell)

### Step 1: Create Temporary Containers

```powershell
docker run -d --name demo-nginx nginx
docker run -d --name demo-httpd httpd
```

### Step 2: Create Temporary Volume

```powershell
docker volume create demo-volume
docker run -d --name demo-volume-container -v demo-volume:/data nginx
```

### Step 3: Create Temporary Network

```powershell
docker network create demo-network
docker run -d --name demo-network-nginx --network demo-network nginx
```

### Step 4: List All Resources

```powershell
docker ps -a
docker images
docker volume ls
docker network ls
```

### Step 5: Stop and Remove Containers

```powershell
docker stop demo-nginx demo-httpd demo-volume-container demo-network-nginx
docker rm demo-nginx demo-httpd demo-volume-container demo-network-nginx
```

### Step 6: Remove Temporary Images (Optional)

```powershell
docker rmi nginx httpd
```

### Step 7: Remove Temporary Volume

```powershell
docker volume rm demo-volume
```

### Step 8: Remove Temporary Network

```powershell
docker network rm demo-network
```

### Step 9: Apply Best Practices

* Minimal images, proper tags, multi-stage builds
* Avoid root user, limit resources
* Cleanup unused containers, images, volumes, networks

---

**Expected Outcome:**

* You will **see creation of temporary Docker resources** first.
* Then **clean everything up**, simulating real-world Docker housekeeping.
* Reinforces best practices and cleanup commands.

