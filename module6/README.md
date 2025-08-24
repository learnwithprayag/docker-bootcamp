# 🐳 Docker Bootcamp – Module 6: Docker Networking

## Bridge, Host, and Overlay Networks
Docker containers communicate through **networks**, which allow them to interact securely and efficiently.  

- **Bridge Network:** Default network; isolates containers on a single host  
- **Host Network:** Uses the host machine’s network stack directly  
- **Overlay Network:** Connects containers across multiple Docker hosts (used in Swarm mode)  

Understanding networks helps in **scaling applications and ensuring container communication**.

---

## Connecting Multiple Containers
- Containers can communicate using **network aliases** and **DNS resolution** within a network  
- Multiple containers can share the same network to **simulate real-world multi-service applications**  
- Proper networking is crucial for **microservices and multi-container apps**

---

## Network Isolation and Port Mapping
- **Isolation:** Containers on different networks cannot communicate unless explicitly connected  
- **Port Mapping:** Expose container ports to the host machine to allow access from outside  

This ensures both **security** and **accessibility** of containerized applications.

---

## Lab 6: Docker Networking Basics
**Objective:** Learn how to create networks, connect containers, and manage port mappings for container communication.

**Lab Name:** Lab 6 – Docker Networking Basics  

*Lab instructions will be provided separately.*
