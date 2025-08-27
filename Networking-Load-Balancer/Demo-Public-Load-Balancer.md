# Demonstration: Public Load Balancer in OCI

## Overview
In this demonstration, we configure a **public load balancer** in Oracle Cloud Infrastructure (OCI) and test its functionality with two backend instances running in different Availability Domains.

---

## Setup
- **Instances**
  - `private-instance-1`  
    - Runs in **AD-1**  
    - Assigned a private IP address
  - `private-instance-2`  
    - Runs in **AD-2**  
    - Assigned a private IP address
- Both instances are deployed in a **private subnet** within the same VCN.

---

## Steps to Create a Public Load Balancer

### 1. Navigate to Load Balancer Service
1. Go to **Networking → Load Balancers**.
2. Select **Load Balancer** (not Network Load Balancer).
3. Click **Create Load Balancer**.

---

### 2. Basic Configuration
- **Name**: (default is fine)
- **Visibility**: `Public`  
  - Ensures a public IP address is assigned (reachable over the internet).
- **IP Address**: Ephemeral (default).
- **Bandwidth**: Minimum 10, Maximum 10 (default).
- **VCN & Subnet**:  
  - Select the **public subnet** (only public subnet is shown when creating a public LB).
- **Advanced Options** (optional):
  - Security → Associate a **Web Application Firewall (WAF) policy**.
  - Acceleration → Enable **Web Application Acceleration**.
  - Management & Tagging → Apply tags if needed.

---

### 3. Backend Configuration
1. **Policy**: Select **Weighted Round Robin**.
2. **Backends**: Add:
   - `private-instance-1`
   - `private-instance-2`
   - *(These instances are in a private subnet, but accessible through the load balancer in the public subnet).*
3. **Health Check Policy**:
   - Protocol: HTTP  
   - Port: 80  
   - Default settings accepted.
4. **Advanced Options**:
   - Session persistence options:  
     - *Application cookie persistence*  
     - *Load balancer cookie persistence*  
   - Enable *auto security list rules* for backend communication.

---

### 4. Listener Configuration
- **Name**: (default is fine)
- **Protocol**: HTTP
- **Port**: 80
- Logging: Disable error and access logs (default).

Click **Next → Submit** to create the load balancer.

---

## Verification

- Once provisioning completes:
  - Load balancer status: **Active**  
  - Backend set health: **OK**  

- **Public IP** is assigned to the load balancer.  
  - Accessing this IP in a browser routes traffic to backends.  
  - With **Round Robin** policy:
    - Refreshing alternates responses between `private-instance-1` and `private-instance-2`.

---

## Load Balancer Details
- **Backend Set**:
  - Contains 2 backend instances.
  - Shows **weight** and **health status**.
- **Listener**:
  - Port: 80
  - Protocol: HTTP
- **Routing Options**:
  - Path route sets are available but **Oracle recommends using routing policies** instead.

---

## Conclusion
- A **public load balancer** was successfully created in a **public subnet**.  
- Backend servers in private subnets were registered and load balanced using **weighted round robin**.  
- The public IP correctly alternated traffic between the two backend instances.
