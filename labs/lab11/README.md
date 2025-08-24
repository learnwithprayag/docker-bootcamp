# Lab 11 – Docker Capstone Exercise

## Objective
Consolidate all Docker knowledge by deploying a real-world, multi-container application using Docker Compose.  
This lab includes a **Flask web app**, **Redis cache**, and **PostgreSQL database**.

---

## Features
- Multi-container orchestration
- Container networking
- Data persistence with PostgreSQL
- Redis caching
- Hands-on Dockerfile and Docker Compose usage
- Compatible with Linux, WSL, and Windows PowerShell/CMD

---

## A. Linux  Setup

```bash
# 1. Create directories
mkdir -p docker-capstone/{app,db,redis}

# 2. Create Flask app
cat >> docker-capstone/app/app.py << 'EOF'
from flask import Flask
import redis
import os

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)

@app.route('/')
def hello():
    count = cache.incr('hits')
    return f'Hello World! This page has been viewed {count} times.'

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
EOF

# 3. Create requirements.txt
cat >> docker-capstone/app/requirements.txt << 'EOF'
Flask==2.3.2
redis==5.2.0
EOF

# 4. Create Dockerfile
cat >> docker-capstone/app/Dockerfile << 'EOF'
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "app.py"]
EOF

# 5. Create Docker Compose file
cat >> docker-capstone/docker-compose.yml << 'EOF'
version: "3.9"
services:
  web:
    build: ./app
    ports:
      - "5000:5000"
    depends_on:
      - redis
      - db
  redis:
    image: redis:7.0
    ports:
      - "6379:6379"
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: capstone
      POSTGRES_PASSWORD: capstone123
      POSTGRES_DB: capstone_db
    ports:
      - "5432:5432"
    volumes:
      - db_data:/var/lib/postgresql/data
volumes:
  db_data:
EOF

# 6. Deploy the application
cd docker-capstone
docker-compose up -d --build
````

---

## B. Windows PowerShell / CMD Setup

```powershell
# 1. Create directories
mkdir docker-capstone
cd docker-capstone
mkdir app db redis

# 2. Create Flask app
Set-Content -Path app\app.py -Value @"
from flask import Flask
import redis
import os

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)

@app.route('/')
def hello():
    count = cache.incr('hits')
    return f'Hello World! This page has been viewed {count} times.'

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
"@

# 3. Create requirements.txt
Set-Content -Path app\requirements.txt -Value @"
Flask==2.3.2
redis==5.2.0
"@

# 4. Create Dockerfile
Set-Content -Path app\Dockerfile -Value @"
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "app.py"]
"@

# 5. Create Docker Compose file
Set-Content -Path docker-compose.yml -Value @"
version: '3.9'
services:
  web:
    build: ./app
    ports:
      - "5000:5000"
    depends_on:
      - redis
      - db
  redis:
    image: redis:7.0
    ports:
      - "6379:6379"
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: capstone
      POSTGRES_PASSWORD: capstone123
      POSTGRES_DB: capstone_db
    ports:
      - "5432:5432"
    volumes:
      - db_data:/var/lib/postgresql/data
volumes:
  db_data:
"@

# 6. Deploy the application
docker-compose up -d --build
```

---

## Validation

1. Open browser: [http://localhost:5000](http://localhost:5000) → should show the hit counter.
2. Redis keys:

```bash
docker exec -it <redis-container-id> redis-cli get hits
```

3. PostgreSQL connection:

```bash
docker exec -it <db-container-id> psql -U capstone -d capstone_db
```

---

## Cleanup

```bash
docker-compose down -v
```

---

## Notes

* This lab provides hands-on experience with:

  * Dockerfiles
  * Docker Compose
  * Multi-container orchestration
  * Redis caching
  * PostgreSQL persistence
  * Container networking


