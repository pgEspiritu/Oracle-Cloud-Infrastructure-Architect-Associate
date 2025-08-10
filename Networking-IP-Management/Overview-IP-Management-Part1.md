# 🌐 Overview of IP Management in OCI

## 📌 1. Private IP Addresses

A **Private IP** is used for internal communication within OCI or with on-premises networks.

### **Use Cases**
1. **Instance-to-instance communication** within the **same VCN**  
   - Can be in the same or different subnets  
   - Must be in the **same VCN**
2. **VCN Peering**  
   - Connects two different VCNs (same region or different regions)  
   - Communication happens using **private IPs**
3. **On-Premises Connectivity**  
   - Via **Site-to-Site VPN** or **FastConnect**  
   - Uses private IPs for communication

---

### **VNIC and Private IP Structure**

- **Primary VNIC**  
  - **1 Primary Private IP**
  - Up to **32 Secondary Private IPs**
- **Secondary VNIC**  
  - **1 Primary Private IP**
  - Up to **32 Secondary Private IPs**

📌 **Maximum** = `1 primary + 32 secondary = 33 IPv4 private IPs per VNIC`

> Note: Any private IP (primary or secondary) can optionally have a **public IP** assigned.

---

## 📌 2. Public IP Addresses

A **Public IP** allows a resource to be reachable from the **internet**.

**Example:**  
- **NAT Gateway**: Always associated with a public IP for internet access.

---

### **Types of Public IPs in OCI**

| Feature | Ephemeral Public IP | Reserved Public IP |
|---------|---------------------|--------------------|
| **Persistence** | Exists only for the **lifetime of the instance** | Exists **independently** of the instance |
| **Reassignment** | Lost if instance is terminated | Can be reassigned to another instance |
| **Assignment Scope** | Only to a **primary private IP** | Can be assigned to **primary** or **secondary private IP** |
| **Use Case** | Temporary external connectivity | Persistent public endpoint for resources |

---

### **Key Differences**

- **Ephemeral** = Temporary, tied to the instance's lifecycle  
- **Reserved** = Persistent, reusable across instances  
- **Assignment flexibility**: Reserved public IPs can also be linked to **secondary private IPs**

---

## 🎯 Summary

- **Private IPs**: Internal communication within VCNs, peered VCNs, or on-premises via VPN/FastConnect  
- **Public IPs**: Internet-facing, available as **Ephemeral** or **Reserved**  
- **VNICs**: Each can have **1 primary** + **32 secondary** private IPs (IPv4)  
- **Reserved public IPs** offer **flexibility** and **persistence**

---
