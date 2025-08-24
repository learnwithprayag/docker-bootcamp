# 🐳 Lab 4 – Creating a Custom Docker Image

**Objective:** Build a custom Docker image using Dockerfile instructions and understand how each command works.

---

## Lab 4: Part A – Ubuntu/Linux

### Step 1: Create a Project Directory

```bash
mkdir -p ~/docker-labs/lab4
cd ~/docker-labs/lab4
```

### Step 2: Create a Sample HTML File

```bash
echo "<h1>Hello from Custom Docker Image</h1>" > index.html
```

### Step 3: Create a Dockerfile

```bash
cat > Dockerfile <<EOF
# Base image
FROM nginx:latest

# Maintainer info
LABEL maintainer="yourname@example.com"

# Copy HTML file into container
COPY index.html /usr/share/nginx/html/index.html

# Set environment variable
ENV APP_ENV=development

# Expose port
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
EOF
```

### Step 4: Build the Docker Image

```bash
docker build -t custom-nginx:1.0 .
```

### Step 5: List Docker Images

```bash
docker images
```

* Verify your `custom-nginx:1.0` image is present.

### Step 6: Run the Custom Image

```bash
docker run -d -p 8080:80 --name custom-nginx-container custom-nginx:1.0
```

### Step 7: Verify in Browser

* Open `http://localhost:8080` and check the custom HTML page.

### Step 8: Stop and Remove Container

```bash
docker stop custom-nginx-container
docker rm custom-nginx-container
```

---

## Lab 4: Part B – Windows (Using Docker Desktop)

### Step 1: Create Project Folder

```powershell
mkdir C:\docker-labs\lab4
cd C:\docker-labs\lab4
```

### Step 2: Create Sample HTML File

```powershell
echo "<h1>Hello from Custom Docker Image</h1>" > index.html
```

### Step 3: Create Dockerfile

```powershell
cat > Dockerfile <<EOF
FROM nginx:latest
LABEL maintainer="yourname@example.com"
COPY index.html /usr/share/nginx/html/index.html
ENV APP_ENV=development
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
EOF
```

### Step 4: Build the Docker Image

```powershell
docker build -t custom-nginx:1.0 .
```

### Step 5: List Docker Images

```powershell
docker images
```

### Step 6: Run the Custom Image

```powershell
docker run -d -p 8080:80 --name custom-nginx-container custom-nginx:1.0
```

### Step 7: Verify in Browser

* Open `http://localhost:8080` and check the custom HTML page.

### Step 8: Stop and Remove Container

```powershell
docker stop custom-nginx-container
docker rm custom-nginx-container
```

---

Expected Outcome:

* Successfully build a Docker image from a Dockerfile.
* Run a container based on your custom image.
* See the custom HTML content in the browser.


Do you want me to do that?
