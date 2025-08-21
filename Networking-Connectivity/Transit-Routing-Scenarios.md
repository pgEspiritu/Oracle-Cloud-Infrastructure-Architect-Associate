# 🚦 Transit Routing in OCI

## 📌 What is Transit Routing?
Transit routing allows an **on-premises network** to connect to multiple VCNs in OCI through a **single VPN or FastConnect connection**, instead of creating multiple connections for each VCN.

### ❌ Problem Without Transit Routing
- Organization has 3 departments: **A, B, C**
- Each department has its own VCN (**VCN A, VCN B, VCN C**)
- On-premises environment needs connectivity to all three VCNs
- Without transit routing → you’d need **3 separate VPN or FastConnect connections**
  - Increased **cost**
  - Increased **administration overhead**

### ✅ Solution With Transit Routing
- A **hub VCN** is created
- A **single site-to-site VPN or FastConnect** is established between the **on-premises network** and the **hub VCN**
- Other VCNs (**spokes**) are connected to the hub via **local peering gateways (LPGs)**
- **Traffic transits through the hub VCN** to reach spoke VCNs
- **Requirement**: Hub and spokes must be in the **same region** (can be in different tenancies)

---

## 🏗️ Hub and Spoke Topology
- **Hub VCN**: Centralized VCN connected to on-prem
- **Spoke VCNs**: Connected to the hub using LPGs
- On-prem ↔ Hub (via VPN/FastConnect) ↔ Spokes (via LPGs)

---

## 📘 Example Architecture

### Components
- **On-premises environment**
  - CPE (Customer Premises Equipment)
- **Hub VCN** – CIDR: `10.0.0.0/16`
  - Subnet H
  - DRG (Dynamic Routing Gateway)
  - Local Peering Gateways: `LPG-H1`, `LPG-H2`
- **Spoke VCN 1** – CIDR: `192.168.0.0/24`
  - Subnet 1
  - LPG1
- **Spoke VCN 2** – CIDR: `192.168.1.0/24`
  - Subnet 2
  - LPG2

---

## 📋 Routing Configuration

### 1. Subnet 1 (Spoke VCN 1)
- `172.16.0.0/12` → Next Hop: `LPG1`
- `10.0.0.0/16` → Next Hop: `LPG1`

### 2. Subnet 2 (Spoke VCN 2)
- `172.16.0.0/12` → Next Hop: `LPG2`
- `10.0.0.0/16` → Next Hop: `LPG2`

### 3. DRG (Hub VCN)
- `192.168.0.0/24` → Next Hop: `LPG-H1`
- `192.168.1.0/24` → Next Hop: `LPG-H2`

### 4. Subnet H (Hub VCN)
- `172.16.0.0/12` → Next Hop: `DRG`
- `192.168.0.0/24` → Next Hop: `LPG-H1`
- `192.168.1.0/24` → Next Hop: `LPG-H2`

### 5. LPG-H1 (Hub VCN LPG to Spoke 1)
- `172.16.0.0/12` → Next Hop: `DRG`

### 6. LPG-H2 (Hub VCN LPG to Spoke 2)
- `172.16.0.0/12` → Next Hop: `DRG`

---

## ⚙️ Advanced Configurations

### Attaching Route Table to DRG
1. Go to **DRG → VCN Attachments**
2. Edit the attachment
3. Under **Show Advanced Options**, select a **VCN Route Table**
   - Required for **transit routing**

### Attaching Route Table to LPG
1. Create an LPG
2. Use **Show Advanced Options**
3. Associate a **VCN Route Table**
   - Must use **DRG** or **Private IP** as next hop

---

## ✅ Key Takeaways
- Transit routing reduces **cost** and **complexity**
- **Hub and spoke topology** is used
- Route tables must be carefully configured across:
  - Subnets
  - DRG
  - LPGs
- Advanced options in OCI console allow attaching route tables to **DRGs** and **LPGs**
