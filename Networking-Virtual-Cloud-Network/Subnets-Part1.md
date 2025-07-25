# 🧩 Lesson: Subnets in OCI Part 1

## 📊 Subnet Basics

- A **VCN** can be divided into multiple **subnets**.
- Each subnet is represented in **CIDR notation**.
  - Example:
    - VCN: `10.0.0.0/16`
    - Subnet A: `10.0.1.0/24`
    - Subnet B: `10.0.2.0/24`

> ℹ️ **CIDR Reminder**:  
> Smaller prefix = larger network  
> `/16` is **larger** than `/24`

---

## 🔁 Subnet IP Range Rules

- Each subnet must have a **unique, non-overlapping CIDR range**.
- **Overlapping Example** (❌ Not Allowed):
  - Subnet A: `10.0.0.0/16`
  - Subnet B: `10.0.1.0/24` (Overlaps with A)
- **Non-overlapping Example** (✅ Allowed):
  - Subnet A: `10.0.1.0/24`
  - Subnet B: `10.0.2.0/24`

---

## 🔄 Changing Subnet CIDR

- You **can change the subnet CIDR block** after creation.
- **However**, overlapping ranges will still not be permitted.

---

## 🏙️ Subnets and Availability Domains

There are **two types of subnets** in OCI:

### 1. **AD-Specific Subnet**
- Tied to a **single Availability Domain**
- Example:
  - Subnet A → AD1
  - Subnet B → AD2

### 2. **Regional Subnet** (✅ Recommended)
- Spans **all Availability Domains** in a region
- Ideal for **high availability** and **flexibility**

> ℹ️ In single-AD regions, both types behave the same.

---

## 🧰 Subnet Configuration Scope

When creating a subnet, you specify:

- 📍 **Route Table**
- 🔐 **Security List**
- 🧾 **DHCP Options**

All instances within a subnet inherit these configurations.

### 🖥️ Instance-Level Effect

- Example: If Subnet A is associated with a default route table,
  - All instances (VMs) inside Subnet A will follow the routing defined in that table.

---

## 🌐 Public vs Private Subnets

### 🔓 Public Subnet
- Instances have:
  - **Private IP**
  - **Public IP**
- Typically used for:
  - Web Servers
  - Bastion Hosts

### 🔒 Private Subnet
- Instances have:
  - **Only Private IP**
- Typically used for:
  - Databases
  - Internal Services

> ⚠️ **Important:**  
> You **must decide** whether a subnet is public or private at **creation time**.  
> This **cannot be changed** later.

---

## ✅ Summary

| Feature                     | Description                                                 |
|-----------------------------|-------------------------------------------------------------|
| **Subnet**                  | A CIDR block inside a VCN                                   |
| **Non-overlapping CIDR**    | Required across all subnets in a VCN                        |
| **AD-specific**             | Subnet tied to one Availability Domain                      |
| **Regional subnet**         | Subnet spans all Availability Domains in a region           |
| **Public subnet**           | Allows both public & private IPs                            |
| **Private subnet**          | Only private IPs; used for internal workloads               |
| **Configurations inherited**| DHCP, Route Table, Security List are applied at subnet level |

