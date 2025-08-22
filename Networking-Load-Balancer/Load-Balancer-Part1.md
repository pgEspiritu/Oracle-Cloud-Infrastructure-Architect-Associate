# Lesson on Load Balancers

## What is a Load Balancer?

- Imagine a **client** sending a request.
- In the middle, there is a **load balancer**.
- Behind the load balancer are multiple **servers (backends)**.

➡️ The load balancer acts as a **single entry point** and distributes traffic across multiple backend servers.

---

## Benefits of a Load Balancer

1. **Scaling**
   - At any time, you can add more backend servers.
   - Example: 3 servers → scale up to 4 servers.

2. **Resource Utilization**
   - Traffic is distributed across backends using load balancing policies.
   - Ensures optimal use of resources.

3. **High Availability**
   - Multiple backends exist.
   - If one backend becomes unhealthy, the load balancer continues to send traffic to healthy servers.

---

## Types of Load Balancers

- **Public Load Balancer**
  - Has a **public IP**.
  - Reachable from the **internet**.

- **Private Load Balancer**
  - Has a **private IP** (from the hosting subnet).
  - Accessible only **within the VCN**.

---

## Key Load Balancer Concepts

There are **9 main concepts** in OCI Load Balancing. Let's cover the first few:

### 1. Backend Servers
- Backend servers are the **actual servers** that generate content.
- The load balancer forwards traffic (HTTP/TCP) to them.
- Example:
```mermaid
flowchart LR
    client["Client"]
    lb["Load Balancer"]
    backend["Backend Server"]

    client --> lb --> backend
```


---

### 2. Backend Set
- A **logical grouping** of backend servers.
- Includes:
- List of backend servers
- **Health check policy**
- **Load balancing policy**

👉 Definition:  
**Backend Set = Backends + Health Check Policy + Load Balancing Policy**

---

### 3. Health Check Policy
- A **test** to determine if a backend is **healthy**.
- If a backend fails → it is removed from rotation.
- Two types:
- **TCP Health Check** → connection attempt
- **HTTP Health Check** → request sent to a URI and response validated

➡️ Purpose: Ensure traffic only goes to healthy servers.

---

### 4. Listener
- A **listener** monitors incoming traffic on the load balancer’s IP.
- To configure, you provide:
- **Protocol** (HTTP, HTTPS, HTTP/2, TCP)
- **Port number**
- You need **at least one listener** per traffic type.
