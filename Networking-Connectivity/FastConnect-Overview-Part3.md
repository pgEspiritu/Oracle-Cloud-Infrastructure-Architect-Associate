# Lesson: FastConnect Overview

## 🌐 What is FastConnect?
- **FastConnect** is a **dedicated and private connection** between your **on-premises network** and **OCI**.  
- Provides:
  - High bandwidth  
  - Low latency → suitable for latency-sensitive applications  
- **No egress data transfer charges** when using FastConnect.  
- Unlike VPN/IPSec, traffic does **not traverse the internet**.

**Architecture Concept:**
```mermaid
flowchart LR
    dc["On-Premises Data Center"]
    fc["FastConnect"]
    oci["OCI"]

    dc <--> fc <--> oci
```


---

## 🔹 FastConnect Connectivity Models
There are **three models** to establish FastConnect:

1. **With an Oracle Partner**  
   - Pre-established connectivity with OCI.  
   - You only connect your on-premises network to the **partner edge** in the FastConnect location.  
   - 💡 **Least expensive** and **most flexible** option.  

2. **Direct Colocation with Oracle**  
   - You already have a **cage** in the same FastConnect location.  
   - Establish a **direct cross-connect** between **your cage** and **Oracle’s cage**.  
   - Best suited if you already have presence in the facility.  

3. **Direct with a Third-Party Provider**  
   - Work with a **carrier of your choice**.  
   - Carrier provisions the dedicated physical circuit to the Oracle FastConnect location.  
   - Ideal if:
     - You already use a specific carrier.  
     - Your data center isn’t served by Oracle partners.  

---

## 🔀 FastConnect Peering Types
FastConnect supports two **peering models** (logical connectivity via virtual circuits):

1. **Private Peering**
   - Extends your **on-premises network into a VCN**.  
   - Requires a **Dynamic Routing Gateway (DRG)**.  
   - Example: Accessing compute instances in private subnets.  

2. **Public Peering**
   - Connects your on-premises network to **OCI public services** (e.g., Object Storage, APIs).  
   - **Without traversing the internet**.  

---

## 📖 Key Terms Recap
- **FastConnect Location** → Physical facility where Oracle hosts connectivity.  
- **Metro Area** → Grouping of multiple FastConnect locations.  
- **Oracle Partner** → Pre-integrated provider with Oracle edge.  
- **Third-Party Provider** → Independent carrier chosen by customer.  
- **Colocation** → Customer already present in Oracle FastConnect location.  
- **Cross-Connect** → Physical fiber connection between cages.  
- **Virtual Circuit** → Logical connection for peering (private/public).  
- **LOA (Letter of Authorization)** → Document required for some connectivity models (third-party & colocation).  

---

## ✅ Summary
- **FastConnect** offers **secure, dedicated, private connectivity** to OCI.  
- **Three connectivity models**: Oracle Partner, Direct Colocation, Third-Party Provider.  
- **Two peering types**: Private Peering (to VCNs) and Public Peering (to OCI services).  
- **No egress costs** make it cost-effective for large-scale data transfer.  
