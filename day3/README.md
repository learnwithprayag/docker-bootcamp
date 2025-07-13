
# Day 3 — Docker Volumes, Bind Mounts & Data Persistence

Welcome to Day 3 of the Docker Bootcamp by [LearnWithPrayag](https://learnwithprayag.com)!  
Today, you'll learn how to **persist data** inside Docker containers using **Volumes** and **Bind Mounts**.

---

##  Topics Covered

- What is data persistence in Docker?
- Why containers are ephemeral
- Docker Volumes vs Bind Mounts
- Creating and using named volumes
- Using bind mounts for local development
- Database persistence explained
- Inspecting and removing volumes
- Hands-on with Nginx serving static HTML using bind mounts

---

##  Why Persistence Matters

By default, data created inside a container **disappears** when the container is removed.  
To retain this data, we use:

- **Volumes** → Docker-managed storage
- **Bind Mounts** → Mounting host directories into containers

---

##  What is Database Persistence?

When running databases like **PostgreSQL**, **MySQL**, or **MongoDB** inside containers, their internal data is stored in temporary writable layers by default.  
If the container is removed, **your data is lost** unless you **persist it using volumes or mounts**.

### Example with Named Volume:
```bash
docker volume create pgdata

docker run -d \
  --name postgres \
  -e POSTGRES_PASSWORD=mysecret \
  -v pgdata:/var/lib/postgresql/data \
  postgres
```

Even if you remove and restart the container, data in `pgdata` volume remains safe.

### Common Volume Paths for DBs:
| Database     | Path to Persist          |
|--------------|---------------------------|
| PostgreSQL   | `/var/lib/postgresql/data`|
| MySQL        | `/var/lib/mysql`          |
| MongoDB      | `/data/db`                |
| Redis        | `/data`                   |

Use **volumes for production DBs**, not bind mounts.

---

## Example 1: Named Volume

```bash
# Step 1: Create a named volume
docker volume create mydata

# Step 2: Run a container using the volume
docker run -d --name web -p 8080:80 -v mydata:/usr/share/nginx/html nginx

# Step 3: Copy HTML file into the volume
echo "<h1>Hello from LearnWithPrayag </h1>" > index.html
docker cp index.html web:/usr/share/nginx/html/index.html

# Step 4: Access it using curl
curl http://localhost:8080
```

---

##  Example 2: Bind Mount (Great for Dev)

```bash
# Step 1: Create a folder on host
mkdir site
echo "<h1>Live from Bind Mount </h1>" > site/index.html

# Step 2: Run Nginx with bind mount
docker run -d --name site-web -p 8081:80 -v $(pwd)/site:/usr/share/nginx/html nginx

# Step 3: Access the page
xdg-open http://localhost:8081
```

Now, if you **edit `site/index.html`**, refresh the browser — changes appear instantly!

---

## Lab Tasks

Create a folder named `site`  
Add your own HTML files inside  
Run Nginx using both **named volume** and **bind mount**  
Explore:

```bash
docker volume ls
docker volume inspect mydata
docker rm -f web site-web
docker volume rm mydata
```

Bonus:
Try creating a **PostgreSQL container** with volume persistence using:
```bash
docker volume create pgdata
docker run -d --name pg -e POSTGRES_PASSWORD=test123 -v pgdata:/var/lib/postgresql/data postgres
```

---

##  Volumes vs Bind Mounts

| Feature           | Docker Volume          | Bind Mount (Host Folder)   |
|------------------|------------------------|-----------------------------|
| Managed by Docker| Yes                    |  No                      |
| Use case         | DBs, persistent data   | Dev, hot-reload web files   |
| Portability      | High                   | Host-specific               |
| Setup Required   | Minimal                | Folder structure on host    |

---

##  Best Practices

- Use **volumes** for production and database persistence
- Use **bind mounts** for local dev or config testing
- Clean up unused volumes with:
  ```bash
  docker volume prune
  ```

---

##  Resources

- [Docker Volumes](https://docs.docker.com/storage/volumes/)
- [Bind Mounts](https://docs.docker.com/storage/bind-mounts/)
- [Nginx Docs](https://hub.docker.com/_/nginx)

---

> Great work! You've learned how to **persist and serve data** using Docker the right way — for both static files and real-world databases.  
> Up next: **Docker Compose** and multi-container orchestration!

