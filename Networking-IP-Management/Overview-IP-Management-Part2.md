# 🌐 Overview of IP Management in OCI

## 📌 1. Private IP Addresses

A **Private IP** is used for internal communication within OCI or with on-premises networks.

### **Use Cases**
1. **Instance-to-instance communication** within the **same VCN**  
   - Can be in different subnets but must be in the same VCN
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
📌 Multiple VNICs mean **more private IP capacity** across the instance.

> Any private IP (primary or secondary) can optionally have a **public IP** assigned.

---

## 📌 2. Public IP Addresses

A **Public IP** allows a resource to be reachable from the **internet**.  
It is always assigned to a **private IP object** on the resource.

---

### **Internet Reachability Requirements**
To make a public IP reachable over the internet:
1. **Internet Gateway** must exist in the VCN
2. **Public Subnet** must have route table configured with a route to the internet gateway
3. **Security Lists / NSGs** must allow the required inbound/outbound traffic

---

### **Multiple Public IPs per Resource**
- An instance can have **multiple VNICs**
- Each VNIC: `1 primary private IP + up to 32 secondary private IPs`
- Each private IP can have an **associated public IP**
- This allows **multiple public IPs** on the same instance

---

### **Types of Public IPs in OCI**

| Feature | Ephemeral Public IP | Reserved Public IP |
|---------|---------------------|--------------------|
| **Persistence** | Exists only for the **lifetime of the instance** | Exists **independently** of the instance |
| **Reassignment** | Lost if instance is terminated | Can be reassigned to another resource |
| **Assignment Scope** | Only to a **primary private IP** | Can be assigned to **primary** or **secondary private IP** |
| **Use Case** | Temporary external connectivity | Persistent public endpoint for resources |
| **Cost** | Free | Free (even if unassociated) |

---

### **Key Points**
- **Ephemeral** = Temporary, tied to the instance's lifecycle  
- **Reserved** = Persistent, reusable across resources  
- **No charge** for public IPs, even reserved and unused

---

## 🎯 Summary

- **Private IPs**: Internal communication within VCNs, peered VCNs, or on-premises networks  
- **Public IPs**: Internet-facing, available as **Ephemeral** or **Reserved**  
- **Multiple VNICs** = More private/public IP capacity  
- **Reserved Public IPs**: Persistent, flexible, and free
