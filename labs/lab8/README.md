# 🐳 Lab 8 – Pushing and Pulling Images from Docker Hub

**Objective:** Learn to interact with Docker registries, push your custom images, and pull images for deployment.

---

## Create Docker Hub Account & Token

1. Go to [https://hub.docker.com](https://hub.docker.com) → **Sign Up**
2. After login, navigate to: **Account Settings → Security → New Access Token**

   * Name it (e.g., `lab8-token`)
   * Copy the generated token (you won’t see it again)

Use this token instead of your password when logging in via CLI.

---

## Part A – Ubuntu/Linux

### Create a Sample Custom Docker Image

```bash
# Create a simple Dockerfile
mkdir lab8 && cd lab8
cat > Dockerfile <<EOF
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EOF

# Create a sample webpage
echo "<h1>Hello from Docker Bootcamp Lab 8 🚀</h1>" > index.html

# Build image
docker build -t custom-nginx:1.0 .
```

### Login to Docker Hub (Using Access Token)

```bash
docker login -u yourdockerhubusername
```

*When prompted for password, paste the **token** created earlier.*

### Tag Your Image

```bash
docker tag custom-nginx:1.0 yourdockerhubusername/custom-nginx:1.0
```

### Push Image to Docker Hub

```bash
docker push yourdockerhubusername/custom-nginx:1.0
```

### Pull Image from Docker Hub

```bash
docker pull yourdockerhubusername/custom-nginx:1.0
```

### Run Container from Pulled Image

```bash
docker run -d -p 8080:80 --name pulled-nginx yourdockerhubusername/custom-nginx:1.0
```

### Verify in Browser

Open: `http://localhost:8080`
You should see: **Hello from Docker Bootcamp Lab 8 🚀**

### Cleanup

```bash
docker stop pulled-nginx
docker rm pulled-nginx
```

---

## 🖥️ Lab 8: Part B – Windows (Docker Desktop / PowerShell)

### Create Sample Custom Image

```powershell
# Create Dockerfile
echo FROM nginx:alpine > Dockerfile
echo COPY index.html /usr/share/nginx/html/index.html >> Dockerfile

# Create sample page
echo "<h1>Hello from Docker Bootcamp Lab 8 🚀</h1>" > index.html

# Build image
docker build -t custom-nginx:1.0 .
```

### Login with Token

```powershell
docker login -u yourdockerhubusername
```

Use your **token** when asked for password.

### Same as Linux

```powershell
docker tag custom-nginx:1.0 yourdockerhubusername/custom-nginx:1.0
docker push yourdockerhubusername/custom-nginx:1.0
docker pull yourdockerhubusername/custom-nginx:1.0
docker run -d -p 8080:80 --name pulled-nginx yourdockerhubusername/custom-nginx:1.0
docker stop pulled-nginx
docker rm pulled-nginx
```
---

## Expected Outcome

* You created a **custom Nginx image** with your own webpage.
* Successfully **pushed** it to Docker Hub.
* **Pulled** and **ran** it on another machine.
