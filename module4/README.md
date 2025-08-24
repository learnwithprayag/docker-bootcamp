# 🐳 Docker Bootcamp – Module 4: Dockerfile Essentials

## CMD, ENTRYPOINT, ADD, COPY, ENV, ARG
Dockerfiles are scripts used to **build custom Docker images**. Key instructions include:

- **CMD:** Default command to run in the container  
- **ENTRYPOINT:** Specifies the executable for the container  
- **ADD / COPY:** Add files or directories to the image  
- **ENV:** Define environment variables inside the container  
- **ARG:** Define build-time variables  

Understanding these instructions helps in creating **flexible and reusable images**.

---

## Building Custom Docker Images
Docker images can be **custom-built** from a Dockerfile:

- Define a base image  
- Add application code and dependencies  
- Configure environment variables and commands  
- Build the image and tag it for reuse  

This allows developers to **package applications with all dependencies** for consistent deployment.

---

## Differences Between Dockerfile Instructions
- **CMD vs ENTRYPOINT:**  
  - CMD sets default commands, can be overridden  
  - ENTRYPOINT sets the main executable, less easily overridden  
- **ADD vs COPY:**  
  - COPY copies files and directories  
  - ADD can also extract archives and fetch remote URLs  
- **ENV vs ARG:**  
  - ENV persists in the container at runtime  
  - ARG is only available during build time  

Knowing these differences ensures **efficient and correct image creation**.

---

## Lab 4: Creating a Custom Docker Image
**Objective:** Build a custom Docker image using Dockerfile instructions and understand how each command works.

**Lab Name:** Lab 4 – Creating a Custom Docker Image  

*Lab instructions will be provided separately.*
