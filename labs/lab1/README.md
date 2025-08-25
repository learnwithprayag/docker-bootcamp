# 🐳 Lab 1 – Hello World Container

**Objective:** Run your first Docker container to verify Docker installation and understand basic container behavior.

---

## Lab 1: Part A – Installation and Hello World on Ubuntu/Linux (Official Method)

### Update Package Index

```bash
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common gnupg lsb-release
```

### Add Docker’s Official GPG Key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### Add Docker Repository

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker Engine

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

### Start and Enable Docker Service

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Verify Docker Installation

```bash
docker --version
sudo systemctl status docker
```
### Add user in docker group
```bash
sudo usermod -aG docker $USER
exit
```

### Run Hello World Container

```bash
docker run hello-world
```

* Downloads the `hello-world` image if not present.
* Prints a confirmation message.

### Check All Containers

```bash
docker ps -a
```

### Remove the Container

```bash
docker rm <container_id>
```

### Check Downloaded Images

```bash
docker images
```

**Expected Outcome:**

* Message: `"Hello from Docker! This message shows your installation appears to be working correctly."`

---

## Lab 1: Part B – Installation and Hello World on Windows

### Install Docker Desktop

* Download and install [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop/).
* Ensure Docker Desktop is **running**.

### Verify Installation

Open **PowerShell** or **Command Prompt**:

```powershell
docker --version
```

### Run Hello World Container

```powershell
docker run hello-world
```

### Check Running Containers

```powershell
docker ps -a
```

### Remove the Container

```powershell
docker rm <container_id>
```

### Check Downloaded Images

```powershell
docker images
```

**Expected Outcome:**

* Message confirming Docker is installed and container ran successfully:
  `"Hello from Docker! This message shows your installation appears to be working correctly."`
