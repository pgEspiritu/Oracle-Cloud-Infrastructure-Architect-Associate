# 🧩 Lesson: Subnets in OCI Part 2

### 📍 Oracle Cloud Region Visualization

You can now visualize it better:

- **Oracle Cloud Region**
  - 🌐 Contains **3 Availability Domains**
  - 🌐 A **VCN** spans multiple availability domains
- **Subnets:**
  - 🔹 Subnet A, B, C → **AD-specific subnets**
  - 🔸 Subnet D → **Regional subnet**

---

### 🧠 Key Concepts

- A **VCN** (Virtual Cloud Network) can be subdivided into **subnets**, meaning a large network can be divided into smaller networks.
- A **subnet** is:
  - A **contiguous range of IPs**
  - Represented using **CIDR notation**
- Subnet CIDRs **must not overlap**
- We explored various **scenarios** demonstrating overlapping behavior

---

### 🛠️ Subnet Creation Options

When creating a subnet, you configure:

- **DHCP Options**
- **Subnet Access Type** (Public / Private)
- **Route Table**
- **Security List**

🧩 **Why is a subnet a unit of configuration?**
- When an instance is created, it is **placed in a subnet**
- The instance **inherits network settings** from the subnet

---

### 🔄 Types of Subnets

- **Public Subnet**
  - Has internet access
  - Used for resources that require external access
- **Private Subnet**
  - No direct internet access
  - Used for backend or secure workloads

⚠️ **Important:**  
While creating a subnet, you must choose whether it's **public or private**.  
**You cannot change this later**, so decide carefully at creation time.

---

## ✅ Summary

We discussed:

- The structure of a VCN and its subnets
- How CIDR blocks define and separate networks
- Configuration options tied to subnets
- Differences between public and private subnets

---

**🎓 That's a wrap on this lesson on subnets.**  
Hope you enjoyed it.  
**Thanks for watching!**
