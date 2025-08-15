# 🔗 OCI Local VCN Peering

## 1. What is VCN Peering?
**VCN Peering** allows two **Virtual Cloud Networks (VCNs)** to communicate with each other.

### Two Types of VCN Peering:
1. **Local VCN Peering** – Both VCNs are in the **same region**.
2. **Remote VCN Peering** – VCNs are in **different regions**.

---

## 2. Communication Options Between VCNs
When two VCNs (e.g., **VCN A** and **VCN B**) want to communicate:

### Option 1 – Public Internet
- Each VM instance has a **public IP**.
- Communication occurs **over the internet** using public IPs.

### Option 2 – Private Direct Access (Local Peering)
- Communication uses **private IPs**.
- **Benefit:** Private communication = more secure + reduced latency.

---

## 3. Gateways in Local Peering
Local VCN Peering relies on **virtual routers** (gateways):

| Gateway Type | Description | Limits |
|--------------|-------------|--------|
| **Local Peering Gateway (LPG)** | Dedicated for local VCN peering. | Up to **10 LPGs** per VCN. |
| **Dynamic Routing Gateway (DRG)** | Used for flexible routing and both local & remote peering. | 1 DRG per VCN, **up to 300** VCN attachments. |

> Similar to other OCI gateways (Internet Gateway, NAT Gateway, Service Gateway), LPG and DRG are **connectivity gateways**.

---

## 4. Two Types of Local VCN Peering

### 4.1 Using Local Peering Gateway (LPG)
- **Original method** before DRG v2 existed.
- **Advantages:**
  - Extremely **high bandwidth**.
  - **Low latency**.
- **Limitations:** Max 10 LPGs per VCN.

---

### 4.2 Using Upgraded Dynamic Routing Gateway (DRG v2)
- **Modern approach** for local peering.
- **Advantages:**
  - Flexible routing (attach up to 300 VCNs to a single DRG).
  - Supports both local and remote peering.
- **Ideal for:** Large-scale multi-VCN topologies.

---

## 5. Why Two Types?
- **Before DRG v2:** Only LPG-based peering was available.
- **Now:** DRG v2 offers **more flexibility** but LPG still offers **ultra-low latency** for specific workloads.

---

## 6. Key Benefits
| Method | Bandwidth | Latency | Routing Flexibility |
|--------|-----------|---------|---------------------|
| LPG    | High      | Very Low| Limited (10 LPGs/VCN)|
| DRG v2 | High      | Low     | High (300 VCNs/DRG)  |

---

✅ **Summary:**  
Local VCN Peering enables private communication between VCNs in the same region using either **LPG** or **DRG v2**. LPG offers maximum speed for direct connections, while DRG v2 provides scalable routing flexibility.
