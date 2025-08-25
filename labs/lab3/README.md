# 🐳 Lab 3 – Container Lifecycle Management

**Objective:** Learn to manage container lifecycle and inspect container behavior using basic Docker commands.

---

## Lab 3: Part A – Ubuntu/Linux

### Verify Docker Installation

```bash
docker --version
sudo systemctl status docker
```

### Run a Sample Container

```bash
docker run -d --name test-container nginx
```

* Starts an Nginx container in detached mode.

### Check Running Containers

```bash
docker ps
```

* Lists all running containers.

### Pause the Container

```bash
docker pause test-container
```

* Temporarily suspends container processes.

### Unpause the Container

```bash
docker unpause test-container
```

* Resumes container processes.

### Stop the Container

```bash
docker stop test-container
```

* Gracefully stops the container.

### Restart the Container

```bash
docker start test-container
docker restart test-container
```

* Restarts the container if needed.

### Inspect Container Logs

```bash
docker logs test-container
```

### Inspect Container Metadata

```bash
docker inspect test-container
```

### Enter inside the container
```bash
docker exec -it test-container /bin/bash
```

### Remove the Container

```bash
docker rm test-container
```

---

## Lab 3: Part B – Windows (Using Docker Desktop)

### Verify Docker Installation

Open **PowerShell**:

```powershell
docker --version
```

### Run a Sample Container

```powershell
docker run -d --name test-container nginx
```

### Check Running Containers

```powershell
docker ps
```

### Pause the Container

```powershell
docker pause test-container
```

### Unpause the Container

```powershell
docker unpause test-container
```

### Stop the Container

```powershell
docker stop test-container
```

### Restart the Container

```powershell
docker start test-container
docker restart test-container
```

### Inspect Container Logs

```powershell
docker logs test-container
```

### Inspect Container Metadata

```powershell
docker inspect test-container
```

### Remove the Container

```powershell
docker rm test-container
```

---

**Expected Outcome:**

* Able to start, pause, unpause, stop, restart, inspect, and remove containers.
* Logs and inspection commands give insight into container behavior and status.

