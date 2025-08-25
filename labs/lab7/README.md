# 🐳 Lab 7 – Deploying Multi-Container App with Docker Compose

**Objective:** Learn to define multi-container applications using Docker Compose and deploy them together.

---
### Install Docker Compose (if not installed). While installing docker using offical method we have already installed docker compose as well.

## Official Method (Recommended by Docker) (Skip this step if its already installed)

This installs the latest **Docker Compose plugin** as well.

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

This ensures you always get the **latest stable release** from GitHub.

Check docker and docker compose version
```bash
docker version
docker compose version
```

---

## APT Package Method (Simpler but may not be latest)

```bash
sudo apt update
sudo apt install -y docker-compose
docker-compose --version
```

Drawback: This version may **lag behind** the latest official release in Ubuntu repositories.

### Create Project Directory

```bash
mkdir -p ~/docker-labs/lab7
cd ~/docker-labs/lab7
```

### Create `docker-compose.yml`

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

### Deploy the Multi-Container App

```bash
docker compose up -d
```

* Deploys both Nginx and Apache containers together.

### Verify Running Containers

```bash
docker ps
```

### Test in Browser

* Nginx: `http://localhost:8080`
* Apache: `http://localhost:8081`

### Stop and Remove Containers

```bash
docker compose down
```



**Expected Outcome:**

* Multi-container app deployed with Docker Compose.
* Containers accessible on assigned ports.
* Able to scale services and manage the entire stack with a single command.
