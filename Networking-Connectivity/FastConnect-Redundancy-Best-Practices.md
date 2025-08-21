# Lesson: Physical Overview of a FastConnect Location

## 🔹 FastConnect Location Architecture

- On the right, you see the **OCI region**.  
- There are **two FastConnect locations** (Location 1 and Location 2).  
- Each FastConnect location has **two edge devices** (routers).  

### Example Cross-Connects:
- **Blue Line** → First cross-connect (Location 1).  
- **Red Line** → Second cross-connect, but in a different FastConnect location (Location 2).  
- **Green Dotted Line** → Second cross-connect to another edge device within the same location, if Location 2 is not available.  

This design ensures **redundancy and high availability**.

---

## 🔹 Responsibilities

### ✅ Oracle Handles:
- Redundancy of physical connections **between partner and Oracle network**.  
- Redundancy of **routers** in FastConnect locations (two routers per location).  

### ✅ Customer Handles:
- Ensuring **redundant physical connection** between their network and the **Oracle Partner network** (or directly to Oracle in case of Direct).  

---

## 🔹 FastConnect Partner Model

FastConnect Partner comes in **two flavors**:

### 1. **Layer 2 Connection**
- BGP session is directly **between Customer Edge (CE) and Oracle**.  
- Each partner provides **at least two separate physical connections** to Oracle.  
- Each **Virtual Circuit (VC)** should terminate on a different Oracle physical router.  
- Example:
  - **VC1 → Edge Router 1**  
  - **VC2 → Edge Router 2**  

### 2. **Layer 3 Connection**
- BGP session is **between Customer Edge and Oracle Partner**.  
- Oracle Partner manages redundant BGP sessions with Oracle.  
- **Automatically redundant and diverse**.  
- Customer only needs to ensure redundancy **between CE and the Provider**.  

---

## 🔹 FastConnect Direct (Third-Party Provider or Co-Location)

- Oracle handles **router redundancy** inside the FastConnect locations.  
- Customer is responsible for making the **physical connection to Oracle redundant**.  

### Redundant Virtual Circuits:
- Two Virtual Circuits (VCs) are created:  
  - **VC1 → First Physical Connection**  
  - **VC2 → Second Physical Connection**  
- Each VC connects to a different Oracle Edge Device.  

---

## 🔹 VPN as a Backup

- A **Site-to-Site IPSec VPN** can be configured as a **backup** for FastConnect.  
- Example:
  - **Blue Line** → FastConnect Private Peering.  
  - **Red Dotted Line** → IPSec VPN tunnel (backup).  

- You can configure:
  - At least one available VPN tunnel.  
  - **ECMP (Equal-Cost Multi-Path)** across multiple VPN tunnels for additional bandwidth.  

- **Routing Behavior**:
  - FastConnect (blue line) is **preferred** over VPN if the same route and routing attributes are advertised across both connections.  

---

## ✅ Summary

- **FastConnect Partner**: Oracle + Partner manage redundancy; customer ensures redundant link to partner.  
- **FastConnect Direct (Third-Party or Co-Location)**: Oracle manages router redundancy; customer manages physical connection redundancy.  
- **Redundancy Options**:
  - Use **multiple FastConnect locations**.  
  - Use **multiple edge devices**.  
  - Configure **VPN backup** for failover.  
