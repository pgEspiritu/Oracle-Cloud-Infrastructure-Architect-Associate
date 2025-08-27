# Demonstration: Private Load Balancer in OCI

## Overview
In this demonstration, we configure a **private load balancer** in Oracle Cloud Infrastructure (OCI), register backend servers, and test traffic routing using a test instance.

---

## Setup
- **Backend Instances**
  - `private-instance-1`  
  - `private-instance-2`  
  - Both run in a **private subnet** and have **only private IP addresses**.

- **Test Instance**
  - Runs in a **public subnet** inside the same VCN.
  - Has both a **public IP** (for external SSH/browser access) and a **private IP** (for VCN-internal communication).

---

## Steps to Create a Private Load Balancer

### 1. Navigate to Load Balancer Service
1. Go to **Navigation Menu → Networking → Load Balancers**.
2. Select **Load Balancer → Create Load Balancer**.
3. Enter a name (default is fine).

---

### 2. Basic Configuration
- **Visibility**: `Private`  
  - Load balancer gets a **private IP address** only.
- **Bandwidth**: Default (minimum 10, maximum 10).
- **VCN & Subnet**: Select the **private subnet**.

Click **Next**.

---

### 3. Backend Configuration
- **Policy**: Weighted Round Robin.
- **Backends**: Add:
  - `private-instance-1`
  - `private-instance-2`
- **Health Check Policy**: Default (HTTP, port 80).

Click **Next**.

---

### 4. Listener Configuration
- Provide a listener name.
- **Protocol**: HTTP.
- **Port**: 80.
- Disable error/access logs (optional).  
Click **Submit**.

---

## Verification

- Load balancer status: **Active**.  
- Backend set health: **OK**.  
- Assigned only a **private IP address**.

> Note: Copying this private IP into a browser will not work, since it is **not internet-accessible**.

---

## Testing
1. Connect to the **test instance** in the public subnet (via its public IP).  
2. From within the test instance, use the **private IP of the load balancer**.  
3. Observe the responses:
   - Request alternates between `private-instance-1` and `private-instance-2`.
   - Confirms **round robin policy** is working correctly.

---

## Conclusion
- A **private load balancer** was successfully created in a **private subnet**.  
- Backend servers were registered and verified as healthy.  
- Traffic was load balanced between the two backend servers using **weighted round robin**.  
- Testing confirmed that the private load balancer is **only accessible inside the VCN** via its private IP.
