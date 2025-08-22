# Lesson on Load Balancers (Part 2)

## 5. Load Balancing Policy
Load balancing policy defines **how the load balancer distributes traffic** among backend servers.

### Types of Policies
1. **Round Robin (default)**
   - Requests are sent sequentially across all servers.
   - Example: Request 1 → Server A, Request 2 → Server B, Request 3 → Server C, then back to Server A.

2. **Least Connection**
   - Traffic goes to the backend server with the **fewest active connections**.

3. **IP Hash**
   - Uses the **source IP address** as a hashing key.
   - Ensures requests from the same client IP go to the same backend server (non-sticky sessions).

👉 Note: Policies apply differently depending on **TCP**, **sticky HTTP**, and **non-sticky HTTP** scenarios.

---

## 6. Load Balancer Shape
- OCI load balancers use **flexible shapes**.
- You specify:
  - **Minimum bandwidth**
  - **Maximum bandwidth**

### Example
- Minimum: `10 Mbps`  
- Maximum: `3,000 Mbps`

➡️ Minimum ensures **instant readiness**.  
➡️ Maximum helps **control cost**.  
➡️ Supported range: **10 Mbps to 8,000 Mbps**.

---

## 7. SSL Options
SSL ensures **encrypted communication** between client and backend.

### Types of SSL in OCI
1. **SSL Termination**
   - Client → Load Balancer: **Encrypted**
   - Load Balancer → Backend: **Unencrypted**
   - Load balancer decrypts before forwarding.

2. **Point-to-Point SSL**
   - Client → Load Balancer: **Encrypted**
   - Load Balancer → Backend: **Encrypted**
   - Load balancer re-initiates SSL to backend.

3. **SSL Tunneling**
   - Client → Backend: **End-to-end encrypted**
   - Load balancer passes traffic through without decryption.

---

## 8. Session Persistence
Ensures **all requests from a client go to the same backend server**.

### Use Cases
- Shopping carts  
- Login sessions  

### Methods
- **Application cookie stickiness**  
- **Load balancer cookie stickiness**

---

## 9. Certificates
- Required when creating an **HTTPS listener**.
- SSL server certificate is associated with the load balancer.
- Used to **terminate SSL connection** and decrypt traffic.

---

## Advanced Routing

### Path-Based Routing
- Routes traffic based on **URI path**.  
- Example:
  - `/app` → Backend Pool A
  - `/videos` → Backend Pool B
  - `/images` → Backend Pool C

### Host-Based Routing
- Routes traffic based on **hostname**.  
- Example:
  - `abc.example.com` → Backend Pool A
  - `xyz.example.com` → Backend Pool B

---

## Wrap-Up
This concludes the **whiteboarding discussion on OCI Load Balancers**.  
We covered:
- Load balancing policies
- Load balancer shapes
- SSL options
- Session persistence
- Certificates
- Path-based and host-based routing
