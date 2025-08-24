# 🐳 Lab 7 – Deploying Multi-Container App with Docker Compose

**Objective:** Learn to define multi-container applications using Docker Compose and deploy them together.

---

## Lab 7: Part A – Ubuntu/Linux

### Step 1: Install Docker Compose (if not installed)

```bash
sudo apt update
sudo apt install -y docker-compose
docker-compose --version
```

### Step 2: Create Project Directory

```bash
mkdir -p ~/docker-labs/lab7
cd ~/docker-labs/lab7
```

### Step 3: Create `docker-compose.yml`

```bash
cat > docker-compose.yml <<EOF
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  app:
    image: httpd
    ports:
      - "8081:80"
EOF
```

### Step 4: Deploy the Multi-Container App

```bash
docker-compose up -d
```

* Deploys both Nginx and Apache containers together.

### Step 5: Verify Running Containers

```bash
docker ps
```

### Step 6: Test in Browser

* Nginx: `http://localhost:8080`
* Apache: `http://localhost:8081`

### Step 7: Scale a Service (Optional)

```bash
docker-compose up -d --scale web=2
docker ps
```

* Launches 2 instances of the web service.

### Step 8: Stop and Remove Containers

```bash
docker-compose down
```

---

## Lab 7: Part B – Windows (Using Docker Desktop / PowerShell)

### Step 1: Install Docker Compose

* Included with Docker Desktop. Verify:

```powershell
docker-compose --version
```

### Step 2: Create Project Directory

```powershell
mkdir C:\docker-labs\lab7
cd C:\docker-labs\lab7
```

### Step 3: Create `docker-compose.yml`

```powershell
cat > docker-compose.yml <<EOF
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  app:
    image: httpd
    ports:
      - "8081:80"
EOF
```

### Step 4: Deploy the Multi-Container App

```powershell
docker-compose up -d
```

### Step 5: Verify Running Containers

```powershell
docker ps
```

### Step 6: Test in Browser

* Nginx: `http://localhost:8080`
* Apache: `http://localhost:8081`

### Step 7: Scale a Service (Optional)

```powershell
docker-compose up -d --scale web=2
docker ps
```

### Step 8: Stop and Remove Containers

```powershell
docker-compose down
```

---

**Expected Outcome:**

* Multi-container app deployed with Docker Compose.
* Containers accessible on assigned ports.
* Able to scale services and manage the entire stack with a single command.
