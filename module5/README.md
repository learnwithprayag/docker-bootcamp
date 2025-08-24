# 🐳 Docker Bootcamp – Module 5: Docker Volumes & Storage

## Persistent Storage Using Volumes and Bind Mounts
Containers are ephemeral, which means **data inside a container can be lost** when it stops or is removed.  
Docker provides persistent storage options:

- **Volumes:** Managed by Docker and stored in Docker’s storage area.  
- **Bind Mounts:** Use a directory from the host machine inside the container.  

Volumes are **recommended** for most cases because they are portable, easier to back up, and work well with multi-container setups.

---

## How Containers Store and Share Data
- Containers can **share data** via volumes or mounts between multiple containers.  
- Data persistence allows containers to **maintain state** even after they are stopped or recreated.  
- Proper volume management is critical for **databases, logs, and configuration files**.

---

## Lab 5: Working with Docker Volumes
**Objective:** Learn to create and manage Docker volumes and understand how to persist container data.

**Lab Name:** Lab 5 – Working with Docker Volumes  

*Lab instructions will be provided separately.*
