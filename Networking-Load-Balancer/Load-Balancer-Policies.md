# Lesson on Load Balancer Policies

## Introduction
In OCI, there are **three types of load balancer policies**:
1. **Round Robin** (default)
2. **Least Connections**
3. **IP Hash**

Additionally, you can **assign a weight to backend servers** to influence traffic distribution.  
These policies behave differently depending on:
- **TCP Load Balancer**
- **HTTP Requests (Sticky)**
- **HTTP Requests (Non-Sticky)**

---

## How Policies Apply in Different Scenarios

### 1. TCP Load Balancer
- The **initial incoming request** is routed based on the defined **policy and weight criteria**.  
- Once assigned, all **subsequent packets of that connection** go to the same backend server.  

Example:  
- Client’s first request → Backend 1 (based on policy/weight).  
- All subsequent packets in that session → Backend 1.  

---

### 2. HTTP Requests (Sticky)
- Request is routed to the backend server defined by the **session cookie**.  
- Ensures continuity for **shopping carts, login sessions, etc.**

---

### 3. HTTP Requests (Non-Sticky)
- The **policy and weight criteria** are applied to **every incoming request**.  
- Different requests from the same client may go to **different backend servers**.  

Example:  
- Request 1 → Backend 1  
- Request 2 → Backend 2  

---

## Load Balancer Policies Explained

### 1. Round Robin
- Default policy.  
- Distributes requests **sequentially** across backend servers.  

**Best suited when:**
- Backend servers have **similar capacity**.  
- **Processing load** per request does not vary significantly.  

⚠️ If backend servers differ greatly in capacity, Round Robin may not be ideal.  

---

### 2. Least Connections
- Routes traffic to the server with the **fewest active connections**.  
- Helps balance workloads in **uneven demand scenarios**.  
- Can also be configured with **weights** (Weighted Least Connections).  

---

### 3. IP Hash
- Uses the **client’s IP address as a hashing key**.  
- Ensures traffic from the same client IP is routed to the **same backend server**.  
- Only applies to **non-sticky traffic**.  

---

## Recap of Policy Behavior
- **TCP Load Balancer** → Policy & weights apply to **initial connection**, then all packets stick to same backend.  
- **Sticky HTTP** → Routed based on **session cookie**.  
- **Non-Sticky HTTP** → Policy & weights applied for **every request** (may go to different servers).  

---

## Conclusion
- OCI Load Balancer supports **three policies**: Round Robin, Least Connections, and IP Hash.  
- Policies can be **weighted** for finer control.  
- The **effect of each policy** depends on whether traffic is TCP, Sticky HTTP, or Non-Sticky HTTP.  
