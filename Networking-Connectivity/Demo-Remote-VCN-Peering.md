# 🚀 Demonstration: Remote VCN Peering (Phoenix ↔ Mumbai)

We will connect **two regions**:

- **Phoenix Region** → `VCN-A` (CIDR: `10.0.0.0/16`)  
- **Mumbai Region** → `VCN-B` (CIDR: `192.168.0.0/16`)  

Each VCN has an **instance** running inside a **public subnet**:  
- Instance A (Phoenix)  
- Instance B (Mumbai)  

Our goal: **Enable private communication** between these two instances.  

---

## 🔧 Steps to Configure Remote Peering

### 1️⃣ Create Dynamic Routing Gateways (DRGs)
- **Phoenix**
  - Create DRG → Name: `DRG Phoenix`
- **Mumbai**
  - Create DRG → Name: `DRG Mumbai`

---

### 2️⃣ Attach DRGs to VCNs
- **Phoenix:** Attach `DRG Phoenix` to `VCN-A`  
- **Mumbai:** Attach `DRG Mumbai` to `VCN-B`  

---

### 3️⃣ Create Remote Peering Connections (RPCs)
- In **Phoenix** → Create RPC → Name: `DEMO-RPC1`  
- In **Mumbai** → Create RPC → Name: `DEMO-RPC2`  

---

### 4️⃣ Establish the Peering
- Copy **OCID** of `DEMO-RPC2` (Mumbai).  
- In **Phoenix**, open `DEMO-RPC1` → Select *Establish Connection*.  
- Enter:
  - **Peer Region:** `ap-mumbai-1`
  - **Peer RPC OCID:** `DEMO-RPC2`  

✅ Result: RPC status becomes **Peered** in both regions.  

---

### 5️⃣ Update Route Tables
- **Phoenix (`VCN-A`)**
  - Destination CIDR: `192.168.0.0/16`
  - Target: `DRG Phoenix`

- **Mumbai (`VCN-B`)**
  - Destination CIDR: `10.0.0.0/16`
  - Target: `DRG Mumbai`

---

### 6️⃣ Update Security Lists
- **Phoenix → VCN-A Security List**
  - Allow **Ingress**
    - Source: `192.168.0.0/16`
    - Protocol: `ICMP`

- **Mumbai → VCN-B Security List**
  - Allow **Ingress**
    - Source: `10.0.0.0/16`
    - Protocol: `ICMP`

---

## 🖥️ Testing the Setup

1. **From Phoenix (Instance A)**  
   ```bash
   ping <Private-IP-of-Instance-B>
   ```
   ✅ Success

2. From Mumbai (Instance B)
   ```bash
   ping <Private-IP-of-Instance-A>
   ```
   ✅ Success

---

### 🎯 Conclusion
- We successfully configured Remote VCN Peering between Phoenix and Mumbai.
- Instances in different regions can now communicate privately using private IPs.
