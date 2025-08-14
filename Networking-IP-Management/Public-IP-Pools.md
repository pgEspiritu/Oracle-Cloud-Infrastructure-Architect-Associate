# 🌐 Public IP Pools in Oracle Cloud Infrastructure

## Overview
A **Public IP Pool** is a **set of IPv4 CIDR blocks** allocated to a tenancy.  
These can be **entire "Bring Your Own IP" (BYOIP) CIDR blocks** or **parts of them**.

### Key Points:
- **Allocated to a tenancy** → Only your tenancy can use these IPs.
- **IPv6 addresses** do **not** use IP pools functionality.
- You must first **import your BYOIP CIDR blocks** before creating a public IP pool.

---

## 🔹 Benefits of a Public IP Pool
1. **Create Reserved Public IPs**
   - Reserve an IP from the pool.
   - Attach it to resources such as:
     - NAT Gateway
     - Load Balancer
     - Compute Instance

2. **Direct Launch from Pool**
   - Launch resources directly.
   - IP addresses are automatically allocated from the public IP pool.
   - No need to reserve IPs beforehand.

---

## ⚡ Workflow
1. Import your BYOIP CIDR block(s) to OCI.
2. Create a **Public IP Pool** using the entire or part of your BYOIP CIDR block.
3. Choose one of the following options:
   - **Create Reserved IP** → Attach to resources
   - **Direct Launch from Pool** → Automatically allocate IP to resources

---

## 📏 Limits and Quotas
- A Public IP Pool can contain **zero or more IPv4 CIDR ranges**.
- **Minimum CIDR range:** `/28`
- **Maximum CIDR range:** `/24`

---

✅ Public IP Pools allow flexible management of BYOIP addresses while keeping them **exclusive to your tenancy**.
