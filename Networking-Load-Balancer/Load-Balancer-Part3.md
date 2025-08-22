# Lesson on Load Balancers (Part 3 – Deck Recap)

## What is an OCI Load Balancer?
- Sits **between clients and backend servers**.  
- Responsible for **distributing client requests** across backend instances.  
- Benefits include:
  - **Scaling**: Easily increase backend servers.
  - **Resource Utilization**: Even distribution of requests.
  - **Fault Tolerance & High Availability**: Continues routing traffic even if some servers fail.

---

## Types of Load Balancers
1. **Public Load Balancer**
   - Has a **public IP address**.
   - Accessible from the **internet**.
   
2. **Private Load Balancer**
   - Has a **private IP address**.
   - Accessible **only inside the VCN**.

---

## Supported Protocols
- **Layer 4**: TCP  
- **Layer 7**: HTTP, HTTPS, HTTP/2  

---

## Advanced Features
- **Session Persistence** (sticky sessions)  
- **Path-Based Routing**  
- **SSL Options**:
  - SSL Termination
  - Point-to-Point SSL
  - SSL Tunneling  

---

## Load Balancer Concepts Recap
- **Backend Server** → Generates content.  
- **Backend Set** → Group of backend servers + health check + load balancing policy.  
- **Health Check** → Ensures servers are available before routing traffic.  
- **Listener** → Defines protocol & port to accept traffic.  
- **Load Balancing Policies** → Round Robin, Least Connection, IP Hash.  
- **Shape** → Minimum and maximum bandwidth (10–8,000 Mbps).  
- **Session Persistence** → Ensures same client requests go to same backend.  
- **Certificates** → Required for HTTPS listeners.  

---

## Load Balancer Shape
- **Flexible Shape** (current option in OCI)  
  - Specify **Minimum Bandwidth** → Ensures readiness for load.  
  - Specify **Maximum Bandwidth** → Controls cost.  
- Range: **10 Mbps – 8,000 Mbps**.  
- ⚠️ **Dynamic shapes** are no longer supported.  

---

## Host-Based Routing
- Routes traffic based on **hostname**.  
- Example:
  - `host1.domain1.com` → Backend Set 1  
  - `host2.domain2.com` → Backend Set 2  
- Also called **Content-Based Routing**.  
- Enables hosting **multiple websites on a single load balancer**.  

---

## Path-Based Routing
- Routes traffic based on **URI path**.  
- Example:
  - `/app` → Backend Set 1  
  - `/videos` → Backend Set 2  
- Helps optimize **resource utilization** by segmenting workloads.  

---

## Wrap-Up
In this deck recap, we reinforced:
- The role and benefits of OCI Load Balancers  
- Types (public vs private) and supported protocols  
- Key concepts (backend set, listener, health checks, policies, shapes)  
- Advanced features: session persistence, SSL options, routing policies  
