# 🐳 Lab 1 – Hello World Container

**Objective:** Run your first Docker container to verify Docker installation and understand basic container behavior.

---

## Lab 1: Part A – Installation and Hello World on Ubuntu/Linux (Official Method)

### Step 1: Update Package Index

```bash
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common gnupg lsb-release
```

### Step 2: Add Docker’s Official GPG Key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### Step 3: Add Docker Repository

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Step 4: Install Docker Engine

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

### Step 5: Start and Enable Docker Service

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 6: Verify Docker Installation

```bash
docker --version
sudo systemctl status docker
```

### Step 7: Run Hello World Container

```bash
docker run hello-world
```

* Downloads the `hello-world` image if not present.
* Prints a confirmation message.

### Step 8: Check All Containers

```bash
docker ps -a
```

### Step 9: Remove the Container

```bash
docker rm <container_id>
```

### Step 10 (Optional): Check Downloaded Images

```bash
docker images
```

**Expected Outcome:**

* Message: `"Hello from Docker! This message shows your installation appears to be working correctly."`

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

### Step 4: Check Running Containers

```powershell
docker ps -a
```

### Step 5: Remove the Container

```powershell
docker rm <container_id>
```

### Step 6 (Optional): Check Downloaded Images

```powershell
docker images
```

**Expected Outcome:**

* Message confirming Docker is installed and container ran successfully:
  `"Hello from Docker! This message shows your installation appears to be working correctly."`
