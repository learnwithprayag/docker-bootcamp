# 🐳 Lab 4 – Creating a Custom Docker Image

**Objective:** Build a custom Docker image using Dockerfile instructions and understand how each command works.

---

### Create a Project Directory

```bash
mkdir -p ~/docker-labs/lab4
cd ~/docker-labs/lab4
```

### Create a Sample HTML File

```bash
echo "<h1>Hello from Custom Docker Image</h1>" > index.html
```

### Create a Dockerfile

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

### Build the Docker Image

```bash
docker build -t custom-nginx:1.0 .
```

### List Docker Images

```bash
docker images
```

* Verify your `custom-nginx:1.0` image is present.

### Run the Custom Image

```bash
docker run -d -p 8080:80 --name custom-nginx-container custom-nginx:1.0
```

### Verify in Browser

* Open `http://localhost:8080` and check the custom HTML page.

### Stop and Remove Container

```bash
docker stop custom-nginx-container
docker rm custom-nginx-container
```


