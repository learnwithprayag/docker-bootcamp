# Lab 11 – Docker Capstone Exercise

## Objective
Consolidate all Docker knowledge by deploying a real-world, multi-container application using Docker Compose.  
This lab includes a **Flask web app**, **Redis cache**, and **PostgreSQL database**.


## Features
- Multi-container orchestration
- Container networking
- Data persistence with PostgreSQL
- Redis caching
- Hands-on Dockerfile and Docker Compose usage


### Create directories
```bash
mkdir -p ~/docker-labs/docker-capstone/{app,db,redis}
```

### Create Flask app
```bash
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
```

### Create requirements.txt
```bash
cat >> docker-capstone/app/requirements.txt << 'EOF'
Flask==2.3.2
redis==5.2.0
EOF
```

### Create Dockerfile
```bash
cat >> docker-capstone/app/Dockerfile << 'EOF'
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "app.py"]
EOF
```

### Create Docker Compose file
```bash
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
```

### Deploy the application
```bash
cd docker-capstone
docker compose up -d --build
```


### Test the Flask Web App

```bash
# From host
curl http://localhost:5000

# From inside the web container
docker exec -it docker-capstone-web-1 curl http://localhost:5000
```

**Expected output:**

```
Hello World! This page has been viewed 1 times.
```

Each refresh or request increments the count.


###  Test Redis (cannot use curl)

```bash
# From host
docker exec -it docker-capstone-redis-1 redis-cli ping
# Output: PONG

# From web container (optional)
docker exec -it docker-capstone-web-1 python3 -c "import redis; r=redis.Redis(host='redis'); print(r.ping())"
# Output: True
```

### Test PostgreSQL (cannot use curl)

```bash
# From host
docker exec -it docker-capstone-db-1 psql -U capstone -d capstone_db -c "\l"

# From web container (optional, requires installing client)
docker exec -it docker-capstone-web-1 bash
 apt update && apt install -y postgresql-client
 PGPASSWORD=capstone123 psql -h db -U capstone -d capstone_db -c "\l"

```

## Notes

* This lab provides hands-on experience with:

  * Dockerfiles
  * Docker Compose
  * Multi-container orchestration
  * Redis caching
  * PostgreSQL persistence
  * Container networking
