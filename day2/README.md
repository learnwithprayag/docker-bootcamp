
# 🐳 Day 2 — Dockerfile and Building Custom Images

Welcome to Day 2 of the Docker Bootcamp by [LearnWithPrayag](https://learnwithprayag.com)!  
Today, you’ll learn how to **build your own Docker images** using Dockerfiles — a critical step for real-world DevOps pipelines.

---

##  Topics Covered

- What is a Dockerfile?
- Dockerfile syntax and structure
- Image build lifecycle (`docker build`, `tag`, `push`)
- DockerHub and container registries
- Creating a Personal Access Token (PAT)
- Tagging and pushing images to DockerHub
- Best practices for writing Dockerfiles

---

## 📖 What is a Dockerfile?

A **Dockerfile** is a plain-text script that defines a set of **instructions** for building a Docker image.  
It automates the setup of everything your app needs — from installing dependencies to defining the command to run.

>  It's the blueprint for your container.

---

##  What is a Container Image?

A **Docker image** is a **read-only template** created from a Dockerfile.  
When you run an image, Docker creates a live, isolated instance of it called a **container**.

Images are made of **layers** — every instruction in your Dockerfile creates a new layer.

---

##  What is DockerHub?

**DockerHub** is the default **container registry** used by Docker. It stores and distributes Docker images.

You can:
- Pull images (like `nginx`, `ubuntu`, `alpine`)
- Push your custom images
- Host public or private repositories

>  DockerHub = GitHub for container images.

Other registries include:
- GitHub Container Registry (GHCR)
- Amazon ECR (AWS)
- Google Artifact Registry (GCP)
- Azure Container Registry (ACR)

---

## Dockerfile Example – Static HTML with Nginx

You will now build a simple image that serves an HTML page using Nginx.

📁 Folder structure:
```
nginx-static-app/
├── Dockerfile
└── index.html
```

**index.html**
```html
<!DOCTYPE html>
<html>
<head>
  <title>Docker Bootcamp</title>
</head>
<body>
  <h1>Welcome to LearnWithPrayag </h1>
  <p>Dockerized Nginx Static Site</p>
</body>
</html>
```

**Dockerfile**
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

---

##  Build and Run the Image

```bash
docker build -t static-nginx-app .
docker run -d -p 8080:80 --name mysite static-nginx-app
```

Open in browser: [http://localhost:8080](http://localhost:8080)

---

## 🛠 Create a DockerHub Account, PAT, and Repository

###  Step 1: Create a DockerHub Account

1. Visit [https://hub.docker.com/](https://hub.docker.com/)  
2. Click **Sign Up**, enter your details, confirm your email  
3. Log in to your DockerHub dashboard

---

###  Step 1.5: Create a Personal Access Token (PAT)

Docker CLI login now **requires a PAT instead of your password**.

1. Go to: [https://hub.docker.com/settings/security](https://hub.docker.com/settings/security)  
2. Scroll down to **Access Tokens**  
3. Click **New Access Token**
   - Name: `docker-cli`
   - Access: **Read/Write**
4. Copy and save your PAT securely

You will use this PAT instead of your DockerHub password for CLI login.

---

###  Step 2: Create a Repository

1. In DockerHub, go to your profile → **Repositories**  
2. Click **Create Repository**  
3. Fill in:
   - **Repository Name**: `static-nginx-app`
   - **Visibility**: Public  
4. Click **Create**

---

##  Push Your Image to DockerHub

###  Log in:

```bash
docker login
```

> Use your DockerHub username and **PAT as password**.

---

###  Tag the image:

```bash
docker tag static-nginx-app yourdockerid/static-nginx-app:v1
```

Replace `yourdockerid` with your DockerHub username (e.g., `learnwithprayag`)

---

###  Push the image:

```bash
docker push yourdockerid/static-nginx-app:v1
```

---

###  Pull the image anywhere:

```bash
docker pull yourdockerid/static-nginx-app:v1
```

---

## Best Practices

- Use small base images (`alpine`, `nginx:alpine`, etc.)
- Use `.dockerignore` to avoid unnecessary files
- Always tag with version numbers
- Combine `RUN` instructions to reduce layers
- Keep images small and minimal

---

## Resources

- [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)
- [DockerHub](https://hub.docker.com/)
- [Access Tokens](https://docs.docker.com/docker-hub/access-tokens/)
- [Registry Overview](https://docs.docker.com/docker-hub/registry-overview/)
- [.dockerignore Reference](https://docs.docker.com/engine/reference/builder/#dockerignore-file)

---

> Great work! You've now built, tagged, and published your **first static web app image** using Docker.  
> Next up: **Docker Compose** for multi-container orchestration!

````

