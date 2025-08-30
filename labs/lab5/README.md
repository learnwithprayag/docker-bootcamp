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

