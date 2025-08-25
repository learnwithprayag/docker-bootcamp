# Lab 6 – Docker Networking Basics

**Objective:** Learn how to create networks, connect containers, and manage port mappings for container communication.

---

## Lab 6: Part A – Ubuntu/Linux

### List Existing Networks

```bash
docker network ls
```

### Create a Custom Bridge Network

```bash
docker network create mynetwork
```

### Run Two Containers on the Custom Network

```bash
docker run -d --name web1 --network mynetwork nginx
docker run -d --name web2 --network mynetwork nginx
```

### Inspect Network

```bash
docker network inspect mynetwork
```

* Shows which containers are connected to the network.

### Connect a Running Container to the Network

```bash
docker run -d --name web3 nginx
docker network connect mynetwork web3
```
### Instll ping command
docker exec -it web1/web2/web3
 apt update && apt install -y iputils-ping

### Test Connectivity Between Containers

```bash
docker exec -it web1 ping web2
docker exec -it web3 ping web1
```

### Remove Containers

```bash
docker stop web1 web2 web3
docker rm web1 web2 web3
```

### Remove Network

```bash
docker network rm mynetwork
```

---

## Lab 6: Part B – Windows (Using Docker Desktop / PowerShell)

### List Existing Networks

```powershell
docker network ls
```

### Create a Custom Bridge Network

```powershell
docker network create mynetwork
```

### Run Two Containers on the Custom Network

```powershell
docker run -d --name web1 --network mynetwork nginx
docker run -d --name web2 --network mynetwork nginx
```

### Inspect Network

```powershell
docker network inspect mynetwork
```

### Connect a Running Container to the Network

```powershell
docker run -d --name web3 nginx
docker network connect mynetwork web3
```
### Instll ping command
docker exec -it web1/web2/web3
 apt update && apt install -y iputils-ping

### Test Connectivity Between Containers

```powershell
docker exec -it web1 ping web2
docker exec -it web3 ping web1
```

### Remove Containers

```powershell
docker stop web1 web2 web3
docker rm web1 web2 web3
```

###  Remove Network

```powershell
docker network rm mynetwork
```

---

**Expected Outcome:**

* Able to create custom Docker networks and connect containers.
* Containers can communicate using container names as hostnames.
* Port mapping and network isolation can be tested and managed.
