# 🖥️ Dedicated Virtual Machine Host (DVH) – Capacity Type

This lesson explains the concept of **Dedicated Virtual Machine Hosts (DVH)** in Oracle Cloud Infrastructure.

---

## 📌 What is a Dedicated Virtual Machine Host?
- A **dedicated host** lets you run VM instances on a **single-tenant server**.  
- **Not shared** with other customers.  
- **Billing**:
  - Charged as soon as the **host** is created.  
  - ✅ **No charge** for individual VM instances placed on it.  

---

## ⚙️ Host Shapes & Capacity
- When creating a DVH, you **select a host shape**.  
- The shape determines:
  - **Capacity available**  
  - **Types of VMs** that can be launched  
- ⚠️ Some OCPUs are **reserved for VM management** → Available OCPUs < Billed OCPUs.  

**Example**:  
- `DVH.Standard3.64` → **60 usable OCPUs** & **960 GB usable memory**.  

---

## 🎯 Use Cases
- ✅ Compliance & regulatory isolation (dedicated hardware).  
- ✅ Host-based licensing (entire server must be licensed).  

---

## 🧩 Supported VM Shapes
- Each DVH shape supports specific VM series.  
- Example:  
  - `DVH.Standard2.52` supports **VM.Standard2** series.  

---

## 🚫 Limitations
Most VM compute features are supported, but **these are not**:  
- ❌ Autoscaling  
- ❌ Capacity reservations  
- ❌ Instance configurations  
- ❌ Instance pools  
- ❌ Burstable instances  
- ❌ Remote migration  

---

## ✅ Summary
- DVHs provide **isolation, compliance, and licensing flexibility**.  
- Shape determines **usable OCPUs & memory**.  
- Some features are **unsupported**.  
