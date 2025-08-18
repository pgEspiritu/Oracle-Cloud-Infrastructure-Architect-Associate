# 🛠️ Demonstration: Local VCN Peering

In this demonstration, we will configure **local peering** using:

1. **Local Peering Gateways (LPGs)**
2. **Dynamic Routing Gateway (DRG)**

---

## 📋 Resources Setup

We have created:

- **Two VCNs**: `VCN-A` and `VCN-B`
- **One Public Subnet** in each VCN
- **Internet Gateway** for each VCN
- **Route Table Entries**: `0.0.0.0/0` → Internet Gateway
- **Two Instances**:
  - Instance A → `VCN-A`
  - Instance B → `VCN-B`

---

## 🔹 Part 1: Local Peering Gateway (LPG)

### Step 1: Initial Check
From Instance A, try pinging the **private IP** of Instance B: `ping <InstanceB_Private_IP>`

Result: ❌ No connectivity.

---

### Step 2: Create LPGs
- **VCN-A** → Create `LPG1`
- **VCN-B** → Create `LPG2`

---

### Step 3: Establish Peering Connection
From `VCN-A`:
- Go to **LPG1** → **Establish Peering Connection**
- Select:
  - Peer VCN: `VCN-B`
  - Peer LPG: `LPG2`
- Status changes from **Pending** → **Peered** ✅

---

### Step 4: Configure Route Tables
- **VCN-A**:
  - Destination: `192.168.0.0/16`
  - Target: `LPG1`
- **VCN-B**:
  - Destination: `10.0.0.0/16`
  - Target: `LPG2`

---

### Step 5: Configure Security Lists
- **VCN-A**: Add ingress rule  
  - Source: `192.168.0.0/16`  
  - Protocol: ICMP
- **VCN-B**: Add ingress rule  
  - Source: `10.0.0.0/16`  
  - Protocol: ICMP

---

### Step 6: Test Connectivity
From Instance A: `ping <InstanceB_Private_IP>`

Result: ✅ Ping successful using **private IP**.

---

## 🔹 Part 2: Dynamic Routing Gateway (DRG)

### Step 1: Create DRG
- Name: `oci-aa-drg`
- Status: **Available**

---

### Step 2: Attach DRG to VCNs
- Attach to `VCN-A`
- Attach to `VCN-B`

---

### Step 3: Configure Route Tables
- **VCN-A**:
  - Destination: `192.168.0.0/16`
  - Target: DRG
- **VCN-B**:
  - Destination: `10.0.0.0/16`
  - Target: DRG

---

### Step 4: Test Connectivity
From Instance A: `ping <InstanceB_Private_IP>`

Result: ✅ Ping successful.

---

## 📌 Summary
We demonstrated **two approaches** for Local VCN Peering:

1. **Local Peering Gateways (LPGs)**
   - Requires **two LPGs** (one per VCN)
   - Direct LPG-to-LPG connection
   - Configure route tables + security lists

2. **Dynamic Routing Gateway (DRG)**
   - Requires **one DRG**
   - Attach DRG to both VCNs
   - Configure route tables + security lists

Both methods allow **private IP communication** between resources in different VCNs within the same region.


