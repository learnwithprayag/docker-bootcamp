# 🐳 Lab 9 – Automating Docker Deployment with GitHub Actions

**Objective:** Learn to create a CI/CD pipeline using GitHub Actions to build and deploy Docker containers automatically.

---

### Create Docker Hub Account

1. Go to [https://hub.docker.com/signup](https://hub.docker.com/signup)
2. Enter **username, email, password** → click **Sign Up**
3. Verify your email.

### Create Repository

1. Log in at [https://hub.docker.com](https://hub.docker.com)
2. Click **Repositories → Create Repository**
3. Enter repo **gitlab-ci-cd-demo**, choose **Public/Private**
4. Click **Create** 

Would you like me to also give the **CLI commands** to create and push your first image to that repo?


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
git config --global user.name "Your name"
git config --global user.email your-email-address
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
<h1>Hello from GitHub Actions CI CD</h1>
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
cat > .github/workflows/docker-ci-cd.yml <<EOF
name: Docker CI

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
      run: docker build -t yourdockerhubusername/gitlab-ci-cd-demo:latest .

    - name: Push Docker image
      run: docker push yourdockerhubusername/gitlab-ci-cd-demo:latest
EOF
```
### Create ssh key pair
```bash
ssh-keygen -t rsa -b 4096 -C "docker-ci-cd-deploy" -f docker_ci_cd_key
```
### Manually append docker_ci_cd_key.pub content to ~/.ssh/authorized_keys on EC2

### Set Secrets in GitHub

* Navigate to **Settings → Secrets and variables → Actions**
* Add `DOCKER_USERNAME` and `DOCKER_PASSWORD` (Docker Hub Access token).
* EC2_HOST → EC2 public IP
* EC2_USER → EC2 user (e.g., ubuntu)
* EC2_SSH_KEY → private key content (docker_ci_key)

### Commit and Push

```bash
git add .
git commit -m "Add GitHub Actions workflow for Docker CI"
git push origin main
```

### Verify Workflow

* Go to **Actions** tab in GitHub repo.
* Workflow runs automatically on push and builds/pushes Docker image.

---

**Expected Outcome:**

* CI pipeline triggers on every push to `main`.
* Docker image is built and pushed to Docker Hub automatically.
* Demonstrates automated Docker deployment using GitHub Actions.

