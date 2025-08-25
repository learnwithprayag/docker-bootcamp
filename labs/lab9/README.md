# 🐳 Lab 9 – Automating Docker Deployment with GitHub Actions

**Objective:** Learn to create a CI/CD pipeline using GitHub Actions to build and deploy Docker containers automatically.

---

## Lab 9: Part A – Ubuntu/Linux

### Create a new GitHub account:

Go to <a href="https://github.com/join" target="_blank">https://github.com/join</a>.

Enter your **username**, **email address**, and **password**.

Verify your email through the confirmation link sent by GitHub.

Choose a plan (Free is enough to start).

Set up your profile and you’re ready to create repositories. 

### Create GitHub Repository

* Go to GitHub and create a new repository (e.g., `docker-ci-cd-lab`).

### Clone Repository Locally

```bash
git clone https://github.com/yourusername/docker-ci-cd-lab.git
cd docker-ci-cd-lab
```

### Add a Sample Docker Project

* Example folder structure:

```
docker-ci-cd-lab/
 ├── index.html
 ├── Dockerfile
```

* Sample `index.html`:

```html
<h1>Hello from GitHub Actions CI/CD</h1>
```

* Sample `Dockerfile`:

```dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### Create GitHub Actions Workflow

```bash
mkdir -p .github/workflows
cat > .github/workflows/docker-ci.yml <<EOF
name: Docker CI/CD

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v2

    - name: Log in to Docker Hub
      uses: docker/login-action@v2
      with:
        username: \${{ secrets.DOCKER_USERNAME }}
        password: \${{ secrets.DOCKER_PASSWORD }}

    - name: Build Docker image
      run: docker build -t yourdockerhubusername/gitlab-ci-demo:latest .

    - name: Push Docker image
      run: docker push yourdockerhubusername/gitlab-ci-demo:latest
EOF
```

### Set Secrets in GitHub

* Navigate to **Settings → Secrets → Actions**
* Add `DOCKER_USERNAME` and `DOCKER_PASSWORD` (Docker Hub credentials).

### Commit and Push

```bash
git add .
git commit -m "Add GitHub Actions workflow for Docker CI/CD"
git push origin main
```

### Verify Workflow

* Go to **Actions** tab in GitHub repo.
* Workflow runs automatically on push and builds/pushes Docker image.

---

## Lab 9: Part B – Windows (Using Docker Desktop / PowerShell)

### Clone GitHub Repository

```powershell
git clone https://github.com/yourusername/docker-ci-cd-lab.git
cd docker-ci-cd-lab
```

### Add Sample Project (index.html + Dockerfile)

* Same content as Part A.

### Create GitHub Actions Workflow

```powershell
mkdir .github\workflows -Force
cat > .github\workflows\docker-ci.yml <<EOF
name: Docker CI/CD

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v2

    - name: Log in to Docker Hub
      uses: docker/login-action@v2
      with:
        username: \${{ secrets.DOCKER_USERNAME }}
        password: \${{ secrets.DOCKER_PASSWORD }}

    - name: Build Docker image
      run: docker build -t yourdockerhubusername/gitlab-ci-demo:latest .

    - name: Push Docker image
      run: docker push yourdockerhubusername/gitlab-ci-demo:latest
EOF
```

### Set Secrets in GitHub

* Add `DOCKER_USERNAME` and `DOCKER_PASSWORD` under repository **Settings → Secrets → Actions**.

### Commit and Push

```powershell
git add .
git commit -m "Add GitHub Actions workflow for Docker CI/CD"
git push origin main
```

### Verify Workflow

* Check **Actions** tab in GitHub. Workflow will build and push Docker image automatically.

---

**Expected Outcome:**

* CI/CD pipeline triggers on every push to `main`.
* Docker image is built and pushed to Docker Hub automatically.
* Demonstrates automated Docker deployment using GitHub Actions.

