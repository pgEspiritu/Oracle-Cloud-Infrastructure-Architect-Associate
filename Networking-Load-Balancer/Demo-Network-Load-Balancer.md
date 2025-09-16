# Demonstration: Network Load Balancer in OCI

## Overview
In this demonstration, we configure a **Network Load Balancer (NLB)** in Oracle Cloud Infrastructure (OCI), register backend servers, and verify connectivity by performing SSH connections through the NLB.

---

## Setup
- **Instances**
  - `instance-A`
  - `instance-B`
- Both instances:
  - Run inside a **VCN**.
  - Have **only private IP addresses** (no public IPs).

---

## Steps to Create a Network Load Balancer

### 1. Navigate to Network Load Balancer Service
1. Go to **Navigation Menu → Networking → Load Balancers → Network Load Balancer**.
2. Click **Create Network Load Balancer**.
3. Enter a name (default is fine).
4. **Visibility**: `Public`.
5. **IP Address**: Ephemeral IPv4.
6. **VCN & Subnet**: Select the **public subnet**.

Click **Next**.

---

### 2. Listener Configuration
- **Protocol**: TCP  
- **Port**: 22 (SSH)

---

### 3. Backend Configuration
1. Add backends:
   - `instance-A` (port 22, TCP)
   - `instance-B` (port 22, TCP)
2. **Health Check Policy**:
   - Protocol: TCP
   - Port: 22

Click **Next → Create Network Load Balancer**.

---

## Verification

- Once provisioning completes:
  - Load balancer status: **Active**  
  - Backend set health: **OK**  

- Under **Resources → Backend Sets**, confirm both backends are healthy.

---

## Testing the NLB
1. Copy the **public IP address** of the NLB.  
2. Attempt SSH connection:

   ```bash
   ssh -i <private-key-file> opc@<NLB-public-IP>
