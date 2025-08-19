# 🚦 Dynamic Routing Gateway (DRG) – Part 2


## 🔗 DRG Attachments Recap
A DRG can have multiple types of attachments:
- **VCN Attachments**
- **IPsec Attachments** (Site-to-Site VPN)
- **Virtual Circuit Attachments** (FastConnect)
- **Remote Peering Connection (RPC) Attachments**
- **Loopback Attachments**

---

## 🛤️ Routing Between Attachments
Traffic between attachments is routed using:
1. **DRG Route Tables**
2. **DRG Route Distributions**

Together, these entities define **routing policies** inside the DRG.  

📌 Example:  
If traffic enters DRG through a VCN attachment → the DRG route table assigned to that attachment decides **the next hop**.

---

## 📑 Types of Routes in DRG
There are **two types of routes** inside a DRG:

1. **Static Routes**  
   - Created manually.  
   - Useful for fixed paths.  

2. **Dynamic Routes**  
   - Imported automatically into DRG route tables.  
   - Controlled by **Import Route Distributions**.  

---

## 🗂️ DRG Route Tables and Attachments
- Every **attachment** (VCN, RPC, IPsec, Virtual Circuit, etc.) can have an **associated DRG route table**.  
- This route table decides **where packets go next** after entering DRG through that attachment.  

### ✅ Key Points
- By default, **two DRG route tables** are created:
  1. One for **VCN attachments**  
  2. One for **all other attachment types**  

- You can:
  - Assign **dedicated route tables per attachment**  
  - Or use the **same route table for multiple attachments**  

---

## 🔀 DRG Route Table vs. VCN Route Table
It’s important to distinguish between the two:

| Feature | **DRG Route Table** | **VCN Route Table** |
|---------|---------------------|----------------------|
| **Purpose** | Routes packets **entering the DRG** through an attachment | Routes packets **inside the VCN** |
| **Scope** | Decides next hop *within DRG* | Decides routing for traffic *inside the VCN* |
| **Entry Point** | Packets arrive via **DRG attachments** | Packets arrive via **VCN subnets** |

📌 Example:  
- **VCN Route Table**: governs how traffic flows **inside VCN**.  
- **DRG Route Table**: governs how traffic is forwarded **once it enters DRG**.  

---

## ✅ Summary
- DRG attachments = VCN, RPC, IPsec, Virtual Circuits, Loopback.  
- Routing is controlled by **DRG route tables + route distributions**.  
- **Two types of routes**: Static (manual) and Dynamic (imported).  
- Every attachment can have its **own DRG route table**, or share one.  
- **VCN Route Tables** ≠ **DRG Route Tables**:  
  - VCN route tables = routing inside the VCN.  
  - DRG route tables = routing at the DRG level.  
