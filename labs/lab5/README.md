# 🐳 Lab 5 – Working with Docker Volumes

**Objective:** Learn to create and manage Docker volumes and understand how to persist container data.

---

### Create a Docker Volume

```bash
docker volume create myvolume
```

### List Docker Volumes

```bash
docker volume ls
```

### Run a Container with the Volume

```bash
docker run -d -p 8080:80 --name volume-nginx -v myvolume:/usr/share/nginx/html nginx
```

* `-v myvolume:/usr/share/nginx/html` mounts the volume into the container.
* Any changes inside `/usr/share/nginx/html` are persisted in `myvolume`.

###  Add Content to Volume

```bash
docker exec -it volume-nginx bash
echo "<h1>Hello from Volume</h1>" > /usr/share/nginx/html/index.html
exit
```

###  Verify in Browser

* Open `http://localhost:8080` and see the custom content.

### Stop and Remove Container (Volume Remains)

```bash
docker stop volume-nginx
docker rm volume-nginx
```

###  Inspect Volume Data

```bash
docker run --rm -v myvolume:/data busybox ls /data
```

* Shows files stored in the volume even after the container is removed.

###  Remove Volume 

```bash
docker volume rm myvolume
```

---

## Lab 5: Part B – Windows (Using Docker Desktop / PowerShell)

###  Create a Docker Volume

```powershell
docker volume create myvolume
```

###  List Docker Volumes

```powershell
docker volume ls
```

### Run a Container with the Volume

```powershell
docker run -d -p 8080:80 --name volume-nginx -v myvolume:/usr/share/nginx/html nginx
```

###  Add Content to Volume

```powershell
docker exec -it volume-nginx powershell
echo "<h1>Hello from Volume</h1>" > /usr/share/nginx/html/index.html
exit
```

###  Verify in Browser

* Open `http://localhost:8080` to see the content.

###  Stop and Remove Container (Volume Persists)

```powershell
docker stop volume-nginx
docker rm volume-nginx
```

###  Inspect Volume Data

```powershell
docker run --rm -v myvolume:/data busybox ls /data
```

###  Remove Volume 

```powershell
docker volume rm myvolume
```

---

**Expected Outcome:**

* Able to create Docker volumes and mount them into containers.
* Data persists even after the container is removed.
* Can inspect and manage volume content.

