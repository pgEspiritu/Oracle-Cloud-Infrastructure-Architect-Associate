# Lesson: FastConnect with an Oracle Partner

## 🏗️ Architecture Overview
- **OCI Region**:
  - Contains VCN with **Private Subnet** and **Public Subnet**.  
- **FastConnect Location**:
  - Oracle Cage with **FastConnect Edge Device**.  
- **Customer Side**:
  - Multiple data centers with **Customer Premises Equipment (CPEs)**.  
- **Partner Role**:
  - The Oracle Partner has already established **redundant cross-connects** with Oracle FastConnect edge.  
  - ✅ No **Letter of Authorization (LOA)** required in this model.  
- **Your Responsibility**:
  - Provision **physical connectivity** between your data center and the **partner edge device**.

---

## 🔹 Configuration Steps

### 1. Order Connection
- Request a connection from the **Oracle Partner**.  
- Lead time may vary depending on the partner.  

---

### 2. Plan for Virtual Circuits
- Two types of logical connections:
  - **Private Virtual Circuit (Private Peering)** → Extends your on-premises into a VCN. Requires a **Dynamic Routing Gateway (DRG)**.  
  - **Public Virtual Circuit (Public Peering)** → Access OCI public services without internet.  

---

### 3. Create Virtual Circuits in OCI
- Create one or more virtual circuits.  
- Each circuit gets an **OCID**.  

---

### 4. Share OCID with Partner
- Provide the **virtual circuit OCID(s)** to the Oracle Partner.  
- Partner configures circuits on their end to complete connectivity.  

---

### 5. Configure Your Edge (CPE)
- Establish **BGP sessions**. Two scenarios:  
  1. **Direct to Oracle** → BGP session goes directly from your CPE to Oracle edge.  
  2. **Via Partner Edge** → BGP session goes from your CPE to the Partner edge, then to Oracle.  

---

### 6. Validate Physical Connectivity
- Confirm **light levels** are within range.  
- Ensure **interfaces are up** for all physical connections.  

---

### 7. Validate BGP Peering
- If BGP session is **direct with Oracle**:
  - Ping the **Oracle BGP IP** and confirm session is established.  
- If BGP session is **via Oracle Partner**:
  - Ping the **Partner’s BGP IP**.  
  - Confirm BGP session with Partner is established.  
  - Then, confirm session with **Oracle BGP IP**.  

---

### 8. Test End-to-End Connectivity
- Perform ping tests to verify successful FastConnect setup.  

---

## ✅ Summary
- **FastConnect with Oracle Partner**:
  - Simplest and most flexible model.  
  - No LOA needed → Partner already connected to Oracle.  
  - Steps: Order → Create Virtual Circuits → Share OCID → Configure Edge (BGP) → Validate → Test.  
