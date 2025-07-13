# Day 5 — Optimizing Docker Images + CI/CD with GitHub Actions

Welcome to Day 5 of the Docker Bootcamp by [LearnWithPrayag](https://learnwithprayag.com)!  
Today, you'll **optimize Dockerfiles** using best practices and implement a **CI/CD pipeline** using GitHub Actions — pushing and deploying images to a remote EC2 server.

---

## Topics Covered

- Image optimization & caching
- Multi-stage builds
- Using `.dockerignore`
- Automating build & push using GitHub Actions
- Deploying to EC2 via SSH from GitHub

---

## Dockerfile Optimization Tips

- Use **slim or alpine** base images
- Always specify fixed versions (`python:3.10-slim`)
- Use **multi-stage builds** to reduce final size
- Clean up caches using `rm`, `apt clean`, etc.
- Combine `RUN` commands using `&&`
- Use `.dockerignore` to exclude unnecessary files

---

## Sample: Multi-Stage Dockerfile (Static Site)

```dockerfile
# Stage 1: Builder
FROM nginx:alpine as builder

# Just simulate build step for static site
RUN echo "<h1>Optimized Docker Image</h1>" > /usr/share/nginx/html/index.html

# Final stage: copy only needed files
FROM nginx:alpine
COPY --from=builder /usr/share/nginx/html /usr/share/nginx/html
````

---

## .dockerignore Example

```
.git
__pycache__/
*.log
*.md
Dockerfile.old
```

---

## Image Build & Push Locally

```bash
docker build -t learnwithprayag/optimized-site:v1 .
docker push learnwithprayag/optimized-site:v1
```

---

## CI/CD with GitHub Actions (Build + Deploy to EC2)

### Step 1: Required GitHub Secrets

Go to your GitHub repo → **Settings → Secrets → Actions**

| Secret Name           | Description                          |
| --------------------- | ------------------------------------ |
| `DOCKER_USERNAME`     | Your DockerHub username              |
| `DOCKER_PASSWORD`     | DockerHub PAT                        |
| `EC2_HOST`            | EC2 IP address (e.g., 3.110.111.120) |
| `EC2_USER`            | `ubuntu` or `ec2-user`               |
| `EC2_SSH_PRIVATE_KEY` | Paste content of `~/.ssh/id_rsa`     |

---

### Step 2: GitHub Actions Workflow

**File: `.github/workflows/docker-deploy.yml`**

```yaml
name: Build & Deploy to EC2

on:
  push:
    branches:
      - main

jobs:
  build-deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Log in to DockerHub
      run: echo "${{ secrets.DOCKER_PASSWORD }}" | docker login -u "${{ secrets.DOCKER_USERNAME }}" --password-stdin

    - name: Build Docker image
      run: docker build -t ${{ secrets.DOCKER_USERNAME }}/optimized-site:latest .

    - name: Push Docker image
      run: docker push ${{ secrets.DOCKER_USERNAME }}/optimized-site:latest

    - name: Deploy to EC2 via SSH
      uses: appleboy/ssh-action@v1.0.3
      with:
        host: ${{ secrets.EC2_HOST }}
        username: ${{ secrets.EC2_USER }}
        key: ${{ secrets.EC2_SSH_PRIVATE_KEY }}
        script: |
          docker pull ${{ secrets.DOCKER_USERNAME }}/optimized-site:latest
          docker stop site || true
          docker rm site || true
          docker run -d -p 80:80 --name site ${{ secrets.DOCKER_USERNAME }}/optimized-site:latest
```

---

## Verify

After push to `main` branch:

* GitHub builds & pushes image to DockerHub
* EC2 instance pulls new image and restarts container
* App should be accessible at `http://<EC2-IP>`

---

## Optional Lab Tasks

* Optimize a Dockerfile using `alpine`
* Implement a multi-stage build for a Node.js app
* Modify workflow to deploy with `docker-compose`

---

## Resources

* [GitHub Actions Docs](https://docs.github.com/en/actions)
* [Docker Build Cache](https://docs.docker.com/build/cache/)
* [Multi-stage Builds](https://docs.docker.com/build/building/multi-stage/)
* [appleboy/ssh-action](https://github.com/appleboy/ssh-action)

---

> You now have a **real CI/CD pipeline** pushing to DockerHub and deploying on EC2!
> You’re ready for production workflows using Docker and GitHub Actions.


```
