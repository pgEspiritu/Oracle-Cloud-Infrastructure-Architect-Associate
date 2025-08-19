# 🚦 Dynamic Routing Gateway (DRG) – Overview

## 🔹 What is a Dynamic Routing Gateway?
- A **virtual router** that facilitates communication between:
  - On-premises networks
  - Virtual Cloud Networks (VCNs)

---

## 🔗 Attachments
A **DRG can have multiple types of attachments**, each with its own associated route table.  

### Types of Attachments:
- **VCN (Virtual Cloud Network) Attachments**  
- **Remote Peering Connections (RPCs)**  
- **Site-to-Site VPN (IPsec tunnels)**  
- **FastConnect Virtual Circuits**  
- **Cross-Tenancy Attachments**  
- **Loopback Attachments**  

📌 **Diagram (conceptual)**  

```text
      ┌────────────┐
      │   VCNs     │
      └─────┬──────┘
            │
    ┌───────▼───────┐
    │     DRG       │
    └───────▲───────┘
            │
┌──────────────┼──────────────┐
│              │              │
▼              ▼              ▼
 RPCs      IPsec Tunnels   FastConnect
```


---

## 🛣️ DRG Route Tables & Route Distributions
- When you create a DRG, **two default route tables** are created:
  1. One for **VCN attachments**  
  2. One for **all other attachments**  

- You can also:
  - Create additional DRG route tables  
  - Associate them with **specific attachments**  
  - Define **import route distributions** (dynamic routes)  
  - Add **static routes** manually  

### Equal Cost Multi-Path (ECMP)
- **Optional** feature (disabled by default)  
- Allows **load balancing** of traffic across multiple:
  - FastConnect virtual circuits  
  - IPsec tunnels  

---

## 🎯 Use Cases of DRG

### 1. Simplified Configuration
- A single DRG can connect **multiple VCNs**.  
- VCNs can belong to the **same tenancy** or **different tenancies**.  
- Eliminates the need for multiple **Local Peering Gateways (LPGs)**.  

### 2. High Availability
- Use **FastConnect** in one region to communicate with VCNs in **another region**.  

### 3. Increased Scale
- A single DRG supports **up to 300 local VCN attachments**.  

### 4. Transit Routing (Hub-and-Spoke)
- DRG enables **hub-and-spoke architectures**.  
- Supports use of **Network Virtual Appliances (NVAs)** for:
  - Filtering traffic  
  - Inspecting packets between on-premises and VCNs  

### 5. Complex Routing
- Each attachment can have its **own unique route table**.  
- Routing + import policies provide **fine-grained control**.  

---

## ⚙️ DRG Routing Engine – How It Works
1. A **packet arrives** at DRG via an attachment.  
2. A **route lookup** occurs in the **route table associated with that ingress attachment**.  
3. Based on the **next-hop information** in the route table:  
   - The packet is **forwarded** to the correct destination.  

---

## ✅ Summary
- DRG acts as a **central routing hub** for on-premises, VCNs, and cross-region connectivity.  
- Supports **multiple attachment types**, each with a **route table**.  
- Routes can be:
  - **Static** (manual)  
  - **Dynamic** (via import distributions)  
- Enables **hub-and-spoke**, **high availability**, and **scalable networking**.  


