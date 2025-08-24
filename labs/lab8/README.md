# 🐳 Lab 8 – Pushing and Pulling Images from Docker Hub

**Objective:** Learn to interact with Docker registries, push your custom images, and pull images for deployment.

---

## Lab 8: Part A – Ubuntu/Linux

### Step 1: Create or Verify a Custom Docker Image

```bash
docker images
```

* Ensure you have an image, e.g., `custom-nginx:1.0` from Lab 4.

### Step 2: Login to Docker Hub

```bash
docker login
```

* Enter your Docker Hub **username** and **password**.

### Step 3: Tag Your Image for Docker Hub

```bash
docker tag custom-nginx:1.0 yourdockerhubusername/custom-nginx:1.0
```

### Step 4: Push Image to Docker Hub

```bash
docker push yourdockerhubusername/custom-nginx:1.0
```

* Uploads your image to Docker Hub.

### Step 5: Pull Image from Docker Hub

```bash
docker pull yourdockerhubusername/custom-nginx:1.0
```

### Step 6: Run Container from Pulled Image

```bash
docker run -d -p 8080:80 --name pulled-nginx yourdockerhubusername/custom-nginx:1.0
```

### Step 7: Verify in Browser

* Open `http://localhost:8080` to see your app.

### Step 8: Cleanup

```bash
docker stop pulled-nginx
docker rm pulled-nginx
```

---

## Lab 8: Part B – Windows (Using Docker Desktop / PowerShell)

### Step 1: Verify or Build a Custom Docker Image

```powershell
docker images
```

* Use `custom-nginx:1.0` or any other image you built.

### Step 2: Login to Docker Hub

```powershell
docker login
```

* Enter Docker Hub **username** and **password**.

### Step 3: Tag Your Image

```powershell
docker tag custom-nginx:1.0 yourdockerhubusername/custom-nginx:1.0
```

### Step 4: Push Image to Docker Hub

```powershell
docker push yourdockerhubusername/custom-nginx:1.0
```

### Step 5: Pull Image from Docker Hub

```powershell
docker pull yourdockerhubusername/custom-nginx:1.0
```

### Step 6: Run Container from Pulled Image

```powershell
docker run -d -p 8080:80 --name pulled-nginx yourdockerhubusername/custom-nginx:1.0
```

### Step 7: Verify in Browser

* Open `http://localhost:8080` to see the app.

### Step 8: Cleanup

```powershell
docker stop pulled-nginx
docker rm pulled-nginx
```

---

**Expected Outcome:**

* Successfully push a local image to Docker Hub.
* Pull the image from Docker Hub on any machine.
* Run containers using images from Docker Hub.

