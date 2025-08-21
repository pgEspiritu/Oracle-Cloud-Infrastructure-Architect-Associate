# Lesson: FastConnect Co-Location with Oracle

## 🏗️ What is Co-Location with Oracle?
- **FastConnect Data Center Location**:
  - Contains the **Oracle Cage** with FastConnect edge devices.
- **Customer Presence**:
  - Customer already has a **cage** or **Customer Premises Equipment (CPE)** in the same FastConnect data center.
- **Connectivity**:
  - A **direct cross-connect** is established between your CPE and Oracle’s FastConnect edge device.  
  - Redundant connections are typically configured for reliability.

### 🔑 Key Point
- Requires a **Letter of Authorization (LOA)** from Oracle, which you hand over to the **data center provider** for cabling setup.  
- **Best suited for customers who already have presence in the FastConnect location.**

---

## 🔹 Steps to Configure FastConnect Co-Location

### 1. Set Up a DRG (if Private Peering)
- If using **private virtual circuit**, create and configure a **Dynamic Routing Gateway (DRG)**.  

---

### 2. Create Cross-Connect Group and Cross-Connect
- Create:
  - **Cross-Connect Group** (logical grouping).  
  - **Cross-Connect** (physical connection).  
- One or more cross-connects can be added to the group.  

---

### 3. Submit LOA and Request Cabling
- Oracle issues a **Letter of Authorization (LOA)**.  
- Provide the LOA to the **data center provider** to request cabling for each cross-connect.  

---

### 4. Validate Physical Connectivity
- Check **light levels** for each cross-connect.  
- Confirm that the **interfaces are up**.  

---

### 5. Activate Cross-Connect
- In OCI Console, **activate** each cross-connect once cables are ready.  
- Activation informs Oracle that the **fiber is ready to use**.  

---

### 6. Create Virtual Circuits
- Create **private or public virtual circuits** on top of the physical cross-connect.  

---

### 7. Configure Edge (CPE) with BGP
- Configure your **edge routers** with **BGP information** for the virtual circuit.  
- Ping Oracle’s **BGP IP address** to confirm session establishment.  

---

### 8. Test Connectivity
- Perform ping and routing tests between on-prem and OCI.  

---

## ✅ Summary
- **Co-Location with Oracle**:
  - Requires **customer presence** in a FastConnect data center.  
  - Uses a **direct cross-connect** between customer CPE and Oracle Edge.  
  - Steps: DRG (if private) → Cross-Connect Group + LOA → Cabling → Validate → Activate → Virtual Circuits → BGP → Test.  
