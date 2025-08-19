# 🌐 Border Gateway Protocol (BGP) Basics

## 📖 What is BGP?
- **BGP** stands for **Border Gateway Protocol**.  
- It is the **routing protocol of the Internet**.  
- BGP determines the **best network routes** for data transmission.  

When data flows from a **source** to a **destination**, it often passes through **multiple networks** (e.g., Network 1 → Network 2 → Network 3).  
👉 BGP evaluates all available paths and selects the **best route**.

---

## 🏛️ Autonomous Systems (AS)
- An **Autonomous System (AS)** = a collection of connected IP networks under a **single administrative control**.  
- Each AS has a unique **Autonomous System Number (ASN)**.  

### 🔗 BGP Peers
- A **BGP peer** is a router/device at the **edge of an AS**.  
- BGP peers exchange routing information between **neighboring ASes**.  
- This allows BGP to:
  - Perform **route discovery**  
  - Perform **path selection**

---

## 🗺️ Layman’s Example
- Think of BGP like **Google Maps for the Internet**:  
  - Maps → chooses the fastest/optimized route.  
  - BGP → chooses the best route for data packets.  

---

## 🛤️ Example: Route Selection
Suppose we want to send traffic from **AS1 → AS3**:  

- **Path 1**: `AS1 → AS2 → AS3` (2 hops)  
- **Path 2**: `AS1 → AS6 → AS5 → AS4 → AS3` (4 hops)  

✅ BGP will prefer **Path 1** because it has fewer hops.  

---

## ⚡ Why is BGP Important in OCI?
In **Oracle Cloud Infrastructure (OCI)**, you can connect to your **on-premises network** in two ways:  

1. **Site-to-Site VPN**  
   - Supports **BGP**, **static routing**, or a **combination of both**.  

2. **FastConnect**  
   - Always uses **BGP** for **route advertisements**.  

👉 Therefore, understanding BGP is **critical** when configuring **Site-to-Site VPN** or **FastConnect virtual circuits**.  

---

## 📝 Summary
- **BGP** = Routing protocol of the Internet.  
- Selects **best possible routes** across multiple networks.  
- Works with **Autonomous Systems (AS)** and **BGP peers**.  
- Essential for **OCI networking** (VPN + FastConnect).  
