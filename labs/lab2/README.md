# 🐳 Lab 2 – Running Hello World, Apache, and Nginx Containers

**Objective:** Install Docker on your system and run sample containers to explore Docker basics.

---

## Lab 2: Part A – Ubuntu/Linux (Official Method) 

### Install Docker (Official Method) - (Skip this step, if already installed)

```bash
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
exit
```

### Verify Docker Installation

```bash
docker --version
sudo systemctl status docker
docker ps
docker ps -a
docker images
```

### Run Hello World Container

```bash
docker run hello-world
```

* Confirms Docker installation and container runtime.

### Run Apache HTTP Server Container

```bash
docker run -d -p 8080:80 --name apache-server httpd
```

* `-d` runs container in detached mode
* `-p 8080:80` maps container port 80 to host port 8080
* Access in browser: `http://localhost:8080`

### Run Nginx Container

```bash
docker run -d -p 8081:80 --name nginx-server nginx
```

* Maps Nginx port 80 to host port 8081
* Access in browser: `http://localhost:8081`

### Check Running Containers

```bash
docker ps
```

### Stop and Remove Containers

```bash
docker stop apache-server nginx-server
docker rm apache-server nginx-server
```

---

## Lab 2: Part B – Windows (Using Docker Desktop)

### Install Docker Desktop - (Skip this step, if already installed)

* Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/)
* Ensure Docker Desktop is running.

###  Verify Installation

Open **PowerShell**:

```powershell
docker --version
```

### Run Hello World Container

```powershell
docker run hello-world
```

### Run Apache HTTP Server Container

```powershell
docker run -d -p 8080:80 --name apache-server httpd
```

* Access: `http://localhost:8080`

### Run Nginx Container

```powershell
docker run -d -p 8081:80 --name nginx-server nginx
```

* Access: `http://localhost:8081`

### Check Running Containers

```powershell
docker ps
```

### Stop and Remove Containers

```powershell
docker stop apache-server nginx-server
docker rm apache-server nginx-server
```

---

**Expected Outcome:**

* **Hello World container** confirms Docker installation.
* **Apache container** accessible on `http://localhost:8080`
* **Nginx container** accessible on `http://localhost:8081`
* Able to start, stop, and remove containers successfully.

