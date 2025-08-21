# Lesson: FastConnect with a Third-Party Provider

## 🏗️ Architecture Overview
- **OCI Region**:
  - VCN with **Private Subnet** and **Public Subnet**.  
- **FastConnect Location**:
  - **Oracle Cage** with FastConnect Edge Devices.  
- **Customer Side**:
  - On-premises data center with **Customer Premises Equipment (CPE)**.  
- **Third-Party Provider**:
  - Acts as the **network carrier**.  
  - Responsible for establishing **physical connectivity** between customer data center and the Oracle FastConnect Edge.  

**Connections involved**:
1. From **Customer Data Center → Third-Party Provider**.  
2. From **Third-Party Provider → Oracle FastConnect Edge (fiber cross-connect)**.  

---

## 🔑 Key Points
- Unlike Oracle Partner model, here you need to work with an **independent network carrier**.  
- Oracle issues a **Letter of Authorization (LOA)** → You forward it to the provider.  
- The provider provisions the **cross-connect** on your behalf.  
- Suitable when:
  - You already have an existing contract with a network carrier.  
  - Oracle partners don’t serve your data center.  

---

## 🔹 Configuration Steps

### 1. Set Up a DRG (if Private Peering)
- For **Private Virtual Circuit**, create and configure a **Dynamic Routing Gateway (DRG)**.  

---

### 2. Create Cross-Connect Group and Cross-Connect
- Set up **Cross-Connect Group** and **Cross-Connect** in OCI Console.  
- Oracle generates a **Letter of Authorization (LOA)**.  

---

### 3. Forward LOA to Third-Party Provider
- Share the **LOA** with your provider.  
- Provider provisions the **fiber cross-connect** at the FastConnect location.  

---

### 4. Provider Completes Cabling
- Third-party provider requests cabling at FastConnect location.  
- They complete the setup of physical cross-connects.  

---

### 5. Validate Physical Connectivity
- Confirm **light levels** are within acceptable range.  
- Ensure **interfaces are up** for each cross-connect.  

---

### 6. Activate Cross-Connect
- In OCI Console, activate the cross-connect(s).  
- This informs Oracle that the **fiber is ready**.  

---

### 7. Create Virtual Circuits
- Set up **one or more virtual circuits** for the FastConnect connection.  

---

### 8. Configure Edge (CPE) with BGP
- Configure **BGP session** between your edge router and Oracle.  
- Ping **Oracle BGP IP address** to confirm session establishment.  

---

### 9. Test Connectivity
- Perform ping and routing tests to validate end-to-end connectivity.  

---

## ✅ Summary
- **FastConnect with Third-Party Provider**:
  - Requires **Letter of Authorization (LOA)** from Oracle.  
  - Third-party carrier handles **physical cross-connect**.  
  - Steps: DRG (if private) → Cross-Connect + LOA → Provider Cabling → Activate → Virtual Circuits → BGP → Test.  
