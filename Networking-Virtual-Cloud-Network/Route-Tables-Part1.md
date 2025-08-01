# Route Tables in Oracle Cloud Infrastructure (OCI)

## 🧠 What is a Route Table?

A **Route Table** determines how the network traffic flows:
- **Inside the VCN**
- **From the VCN to external destinations**

Essentially, it defines **paths to destinations** via specified targets (next hops).

---

## 📘 Types of Route Tables

There are **two main types** of route tables in OCI:

### 1. Default Route Table
- Automatically created when you create a VCN.
- Comes with an **implicit local route**.
- Allows communication between subnets **without** adding any route rules manually.

💡 **Important**:  
Even though the local route exists, it is not visible in the route table UI. The table might appear "empty", but it's not — it allows all subnets within the VCN to communicate with each other by default.

### 2. Custom Route Table
- Created manually when specific routing requirements arise.
- Also contains the implicit local route.
- Allows greater control over routing, especially when:
  - Managing **public** and **private** subnets.
  - Configuring different types of traffic flow.

---

## 🧩 Use Case: Public and Private Subnets

To control routing:
- Public subnet ➝ associate with a **custom route table** containing an **Internet Gateway**.
- Private subnet ➝ associate with a **different custom route table** possibly using a **NAT Gateway** or **Service Gateway**.

---

## 📊 Structure of a Route Table

A Route Table consists of:

| Destination CIDR Block | Target (Next Hop)        |
|------------------------|--------------------------|
| 0.0.0.0/0              | Internet Gateway         |

### Example
A compute instance in Subnet A wants to access the internet:

- **Destination CIDR Block**: `0.0.0.0/0` (represents the internet)
- **Target**: Internet Gateway (the path to the internet)

---

## 🎯 Valid Route Rule Targets

You can specify several types of **next hop targets**, such as:

- **Internet Gateway**
- **NAT Gateway**
- **Service Gateway**
- **Dynamic Routing Gateway (DRG)**
- **Local Peering Gateway (LPG)**
- **Private IP (of a specific instance or service)**

---

## 📝 Summary

- A **Route Table** defines how traffic moves within or outside the VCN.
- **Default Route Table** has an implicit local route, enabling subnet communication.
- **Custom Route Tables** provide flexibility for routing needs.
- Each route rule includes a **destination CIDR** and a **target** (next hop).
