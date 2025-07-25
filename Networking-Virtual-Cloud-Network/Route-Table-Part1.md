# 📘 Route Tables in Oracle Cloud Infrastructure (OCI)

## 🛣️ What is a Route Table?

A **Route Table** determines how traffic flows within a **Virtual Cloud Network (VCN)** and how traffic exits the VCN to reach external destinations. It defines the path for outgoing traffic based on destination CIDR blocks.

---

## 🧰 Types of Route Tables

1. ### **Default Route Table**
   - Automatically created when you create a VCN.
   - Associated by default with all subnets inside the VCN.
   - Includes an **implicit local route** to allow communication between subnets in the same VCN.
   - Even if no route rules are visible in the console, the local route exists behind the scenes.

2. ### **Custom Route Table**
   - Manually created by the user.
   - Also contains the **implicit local route**.
   - Used to define different routing rules for **public** and **private** subnets.
   - Public and private subnets often require **separate route tables** due to different routing requirements.

---

## 🧭 Default Local Route Explained

- Subnets (e.g., Subnet A, Subnet B, Subnet C) within a VCN can communicate with each other by default.
- This is made possible by the **local route** in the route table.
- This **local route is implicit** and not visible in the route table UI, but it enables internal communication within the VCN.

---

## 🧱 Route Table Structure

A route table has two key columns:

| **Destination CIDR Block** | **Target (Next Hop)**     |
|----------------------------|---------------------------|
| e.g., `0.0.0.0/0`          | e.g., `Internet Gateway`  |

---

### Example:

- **VCN** with a **public subnet (Subnet A)**
- An **Instance in Subnet A** wants to reach the **Internet**
- **Route Rule Configuration:**
  - **Destination CIDR Block:** `0.0.0.0/0` (represents the entire internet)
  - **Target:** `Internet Gateway`

---

## 🎯 Other Target Types in Route Tables

Besides the Internet Gateway, route rules can target:

- 🔁 **NAT Gateway**
- 🌐 **Service Gateway**
- 🔄 **Dynamic Routing Gateway (DRG)**
- 🔗 **Local Peering Gateway (LPG)**
- 📍 **Private IP**

---

## ✅ Summary

- A **Route Table** controls traffic flow **within** and **outside** the VCN.
- It contains rules that map **destination CIDR blocks** to **target gateways**.
- **Default** and **Custom** route tables both contain an **implicit local route** for internal communication.
- Custom route tables are useful for separating **public** and **private** subnet routing needs.
