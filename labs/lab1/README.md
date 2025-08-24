# 🐳 Lab 1 – Hello World Container

**Objective:** Run your first Docker container to verify Docker installation and understand basic container behavior.

---

## Lab 1: Part A – Installation and Hello World on Ubuntu/Linux

### Step 1: Install Docker

```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 2: Verify Docker Installation

```bash
docker --version
sudo systemctl status docker
```

### Step 3: Run Hello World Container

```bash
docker run hello-world
```

* Downloads the `hello-world` image if not already present.
* Prints a confirmation message.

### Step 4: Check Running Containers

```bash
docker ps -a
```

* Lists all containers, including stopped ones.

### Step 5: Remove the Container

```bash
docker rm <container_id>
```

* Clean up the container after testing.

### Step 6 (Optional): Check Downloaded Images

```bash
docker images
```

**Expected Outcome:**

* Message confirming Docker is installed and container ran successfully:
  `"Hello from Docker! This message shows your installation appears to be working correctly."`

---

## Lab 1: Part B – Installation and Hello World on Windows

### Step 1: Install Docker Desktop

* Download and install [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop/).
* Ensure Docker Desktop is **running**.

### Step 2: Verify Installation

Open **PowerShell** or **Command Prompt**:

```powershell
docker --version
```

### Step 3: Run Hello World Container

```powershell
docker run hello-world
```

* Confirms Docker installation by printing a success message.

### Step 4: Check Running Containers

```powershell
docker ps -a
```

* Lists all containers, including stopped ones.

### Step 5: Remove the Container

```powershell
docker rm <container_id>
```

* Clean up after testing.

### Step 6 (Optional): Check Downloaded Images

```powershell
docker images
```

**Expected Outcome:**

* Message confirming Docker is installed and container ran successfully:
  `"Hello from Docker! This message shows your installation appears to be working correctly."`



Do you want me to prepare **Lab 2 in the same dual OS format** next?
