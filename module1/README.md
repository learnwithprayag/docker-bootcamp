# 🐳 Docker Bootcamp – Module 1: Introduction

## What is Docker and Why it Matters
Docker is a **containerization platform** that allows you to package applications and their dependencies into a **portable container**.  
It ensures that the application runs consistently across **different environments** like development, testing, and production.

**Key Benefits:**
- Portability across environments  
- Faster deployment and scaling  
- Consistency and reproducibility  
- Lightweight compared to virtual machines  

---

## Containers vs Virtual Machines
| Feature             | Containers                     | Virtual Machines                |
|-------------------- |-------------------------------- |--------------------------------|
| Resource Efficiency | Lightweight, shares host OS    | Heavy, full OS per VM           |
| Startup Time        | Seconds                        | Minutes                         |
| Isolation           | Process-level isolation        | Full system isolation           |
| Portability         | Highly portable                | Less portable                   |

**Note:** Containers share the host OS kernel but run isolated processes, making them faster and more efficient.

---

## Docker Architecture Overview
Docker’s architecture consists of several key components:

- **Docker Engine:** Core software to run and manage containers  
- **Docker Daemon (`dockerd`):** Handles container lifecycle, images, networks, and volumes  
- **Docker CLI (`docker`):** Command-line interface to interact with Docker Daemon  
- **Docker Registry:** Stores Docker images (e.g., Docker Hub)  
- **Docker Images & Containers:**  
  - **Images:** Read-only templates  
  - **Containers:** Running instances of images  

---

## Real-World Use Cases
- Deploying microservices efficiently  
- Continuous Integration / Continuous Deployment (CI/CD) pipelines  
- Isolated development environments  
- Legacy application modernization  
- Testing applications in consistent environments  

---

## Lab 1: Exploring Hello World Container
**Objective:** Run your first container to verify Docker installation and understand basic container behavior.

**Lab Name:** Lab 1 – Hello World Container  

*Lab instructions will be provided separately.*
