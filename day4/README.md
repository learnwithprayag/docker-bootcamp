
#  Day 4 — Docker Compose for Multi-Container Applications

Welcome to Day 4 of the Docker Bootcamp by [LearnWithPrayag](https://learnwithprayag.com)!  
Today, you’ll learn how to use **Docker Compose** to define and run multi-container applications with a single YAML file.

---

##  Topics Covered

- What is Docker Compose?
- Why use Compose instead of raw Docker CLI
- Compose file syntax and structure (`docker-compose.yml`)
- Defining services, ports, volumes, and dependencies
- Running and stopping multi-container setups
- Hands-on: Static site with Nginx + Live hot reload using bind mount

---

##  What is Docker Compose?

**Docker Compose** is a tool that lets you **define and manage multi-container applications** using a YAML file.

Instead of running long `docker run` commands repeatedly, Compose allows you to:

Build  
Run  
Scale  
Network  
…all services from a single file.

---

## Example: Static Site using Docker Compose

📁 Folder structure:

```
static-site/
├── docker-compose.yml
└── site/
    └── index.html
```

**site/index.html**
```html
<!DOCTYPE html>
<html>
<head>
  <title>Docker Compose Demo</title>
</head>
<body>
  <h1>Welcome to LearnWithPrayag</h1>
  <p>This site is powered by Docker Compose!</p>
</body>
</html>
```

---

##  `docker-compose.yml`

```yaml
version: '3.8'

services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./site:/usr/share/nginx/html:ro
```

###  Explanation:
| Key        | Purpose                                 |
|------------|------------------------------------------|
| `services` | List of containers to run                |
| `web`      | Name of the container                    |
| `image`    | Base Docker image to use                 |
| `ports`    | Host:Container port mapping              |
| `volumes`  | Mount local folder into the container    |

---

## Run the Application

```bash
docker compose up
```

> Now visit: [http://localhost:8080](http://localhost:8080)

To stop:
```bash
docker compose down
```

---

## Lab Tasks

Create a folder named `static-site`  
Add an `index.html` inside `site/`  
Create a `docker-compose.yml` to serve it using Nginx  
Run the site and test changes with hot reload  
Explore:

```bash
docker compose ps
docker compose logs
docker compose stop
```

---

## Rebuild with Custom Nginx Image

Add a `Dockerfile` to change default Nginx behavior, and reference it in Compose:

```dockerfile
# Dockerfile
FROM nginx:alpine
COPY site /usr/share/nginx/html
```

Update `docker-compose.yml`:
```yaml
services:
  web:
    build: .
    ports:
      - "8080:80"
```

---

## Clean Up

```bash
docker compose down --volumes
```

---

## Resources

- [Docker Compose Docs](https://docs.docker.com/compose/)
- [Compose File Reference](https://docs.docker.com/compose/compose-file/)
- [Nginx on Docker Hub](https://hub.docker.com/_/nginx)

---

> You’ve now mastered Docker Compose — a must-have tool for real-world DevOps workflows.  
> Next up: building your **own images and deploying them with Compose** on Day 5!
````


