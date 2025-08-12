# 📚 OCI IP Management – Deck Summary

This deck reinforces the concepts from the **IP Management Overview** lesson, focusing on **Private IPs** and **Public IPs**.

---

## 🔹 Private IP Address

- **Definition**: Internal IP address used for communication within OCI networks or with on-premises resources.
- **Assignment**:
  - Every **instance** has **at least one Primary Private IP**.
  - This Primary Private IP **may** have an **optional Public IP** assigned.
- **Public Subnet Scenario**:
  - Instance in public subnet: Has both **Private IP** + **Public IP**.
- **VNIC Structure**:
  - **Primary VNIC**:
    - 1 Primary Private IP
    - Up to 32 Secondary Private IPs
  - **Secondary VNIC**:
    - 1 Primary Private IP
    - Up to 32 Secondary Private IPs
- **Total Capacity**:
  - Per VNIC = `1 primary + 32 secondary = 33 private IPv4 addresses`
  - Multiple VNICs = More IP capacity

---

## 🔹 Public IP Address

- **Definition**: An IP address reachable from the **internet**, always assigned to a **Private IP object**.
- **Internet Reachability Requirements**:
  1. **Internet Gateway** must exist in the VCN
  2. **Public Subnet** must have a route table with a route to the Internet Gateway
  3. **Security Lists / NSGs** must allow required inbound/outbound traffic

---

## 🔹 Multiple Public IPs

- Each **VNIC** can have:
  - 1 Primary Private IP
  - Up to 32 Secondary Private IPs
- **Each private IP** can have an **associated Public IP**
- Multiple VNICs per instance allow **multiple public IP addresses** for the same instance

---

## 🔹 Types of Public IPs

| Feature | Ephemeral Public IP | Reserved Public IP |
|---------|---------------------|--------------------|
| **Persistence** | Exists for lifetime of instance | Exists beyond instance lifetime |
| **Reassignment** | Lost when instance is terminated | Can be reassigned to another resource |
| **Assignment Scope** | Only to a primary private IP | Can be assigned to primary or secondary private IP |
| **Cost** | Free | Free (even if unassociated) |

---

## 💡 Key Takeaways

- **Private IP** = Internal communication within VCNs, peered VCNs, and on-premises networks  
- **Public IP** = Internet-facing, available as **Ephemeral** (temporary) or **Reserved** (persistent)  
- **VNIC Capacity** = Up to 33 private IPv4 addresses, each optionally with a public IP  
- **Cost** = No charge for public IPs, even unassociated reserved IPs  

---
