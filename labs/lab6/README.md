# Lab 6 – Docker Networking Basics

**Objective:** Learn how to create networks, connect containers, and manage port mappings for container communication.

---

## Lab 6: Part A – Ubuntu/Linux

### Step 1: List Existing Networks

```bash
docker network ls
```

### Step 2: Create a Custom Bridge Network

```bash
docker network create mynetwork
```

### Step 3: Run Two Containers on the Custom Network

```bash
docker run -d --name web1 --network mynetwork nginx
docker run -d --name web2 --network mynetwork nginx
```

### Step 4: Inspect Network

```bash
docker network inspect mynetwork
```

* Shows which containers are connected to the network.

### Step 5: Connect a Running Container to the Network

```bash
docker run -d --name web3 nginx
docker network connect mynetwork web3
```

### Step 6: Test Connectivity Between Containers

```bash
docker exec -it web1 ping web2
docker exec -it web3 ping web1
```

### Step 7: Remove Containers

```bash
docker stop web1 web2 web3
docker rm web1 web2 web3
```

### Step 8: Remove Network

```bash
docker network rm mynetwork
```

---

## Lab 6: Part B – Windows (Using Docker Desktop / PowerShell)

### Step 1: List Existing Networks

```powershell
docker network ls
```

### Step 2: Create a Custom Bridge Network

```powershell
docker network create mynetwork
```

### Step 3: Run Two Containers on the Custom Network

```powershell
docker run -d --name web1 --network mynetwork nginx
docker run -d --name web2 --network mynetwork nginx
```

### Step 4: Inspect Network

```powershell
docker network inspect mynetwork
```

### Step 5: Connect a Running Container to the Network

```powershell
docker run -d --name web3 nginx
docker network connect mynetwork web3
```

### Step 6: Test Connectivity Between Containers

```powershell
docker exec -it web1 ping web2
docker exec -it web3 ping web1
```

### Step 7: Remove Containers

```powershell
docker stop web1 web2 web3
docker rm web1 web2 web3
```

### Step 8: Remove Network

```powershell
docker network rm mynetwork
```

---

**Expected Outcome:**

* Able to create custom Docker networks and connect containers.
* Containers can communicate using container names as hostnames.
* Port mapping and network isolation can be tested and managed.


Do you want me to do that?
