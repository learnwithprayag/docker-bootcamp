# 🐳 Lab 3 – Container Lifecycle Management

**Objective:** Learn to manage container lifecycle and inspect container behavior using basic Docker commands.

---

## Lab 3: Part A – Ubuntu/Linux

### Step 1: Verify Docker Installation

```bash
docker --version
sudo systemctl status docker
```

### Step 2: Run a Sample Container

```bash
docker run -d --name test-container nginx
```

* Starts an Nginx container in detached mode.

### Step 3: Check Running Containers

```bash
docker ps
```

* Lists all running containers.

### Step 4: Pause the Container

```bash
docker pause test-container
```

* Temporarily suspends container processes.

### Step 5: Unpause the Container

```bash
docker unpause test-container
```

* Resumes container processes.

### Step 6: Stop the Container

```bash
docker stop test-container
```

* Gracefully stops the container.

### Step 7: Restart the Container

```bash
docker start test-container
docker restart test-container
```

* Restarts the container if needed.

### Step 8: Inspect Container Logs

```bash
docker logs test-container
```

### Step 9: Inspect Container Metadata

```bash
docker inspect test-container
```

### Step 10: Remove the Container

```bash
docker rm test-container
```

---

## Lab 3: Part B – Windows (Using Docker Desktop)

### Step 1: Verify Docker Installation

Open **PowerShell**:

```powershell
docker --version
```

### Step 2: Run a Sample Container

```powershell
docker run -d --name test-container nginx
```

### Step 3: Check Running Containers

```powershell
docker ps
```

### Step 4: Pause the Container

```powershell
docker pause test-container
```

### Step 5: Unpause the Container

```powershell
docker unpause test-container
```

### Step 6: Stop the Container

```powershell
docker stop test-container
```

### Step 7: Restart the Container

```powershell
docker start test-container
docker restart test-container
```

### Step 8: Inspect Container Logs

```powershell
docker logs test-container
```

### Step 9: Inspect Container Metadata

```powershell
docker inspect test-container
```

### Step 10: Remove the Container

```powershell
docker rm test-container
```

---

**Expected Outcome:**

* Able to start, pause, unpause, stop, restart, inspect, and remove containers.
* Logs and inspection commands give insight into container behavior and status.

