# Lesson: Route Tables in OCI

## 🔄 What Is a Route Table?

A **Route Table** determines:

- How traffic flows **within** a VCN.
- How traffic originating from the VCN **reaches other destinations**.

In essence, it **defines the path** for outbound and inter-subnet traffic.

---

## 🧾 Types of Route Tables

There are **two types** of Route Tables:

### 1. Default Route Table
- **Automatically created** when a VCN is created.
- Includes an **implicit local route**, allowing **communication between subnets**.
- This **local route is not visible** in the console UI.
- Example:
```text
Subnet A <--> Subnet B <--> Subnet C
(All can talk to each other through implicit local route)
```


### 2. Custom Route Table
- **Manually created** by users.
- Also includes the **implicit local route**.
- Typically used to define **specific routing for public and private subnets**.
- Each subnet can be associated with **only one route table**.

---

## 📋 Route Table Format

Each route rule in a route table has **two columns**:

| Destination CIDR Block | Target (Next Hop)          |
|------------------------|----------------------------|
| e.g. `0.0.0.0/0`       | e.g. Internet Gateway (IGW) |

### Example:
Suppose you have an instance in **Subnet A** that needs to access the **internet**.

- **Destination CIDR Block**: `0.0.0.0/0` (represents "anywhere on the internet")
- **Target**: Internet Gateway (IGW)

This allows internet-bound traffic to flow through the IGW.

---

## 🏁 Supported Route Targets

A route rule’s **target** (i.e., next hop) can be:

- **Internet Gateway (IGW)**
- **NAT Gateway**
- **Service Gateway**
- **Dynamic Routing Gateway (DRG)**
- **Local Peering Gateway (LPG)**
- **Private IP (e.g., of a virtual appliance)**

Each has a use case depending on whether you're routing to:

- The public internet
- Oracle services
- Peered VCNs
- On-prem networks
- Virtual firewalls, etc.

---

## ✅ Summary

- A **Route Table** controls traffic flow **out of a subnet**.
- Each subnet must be associated with **one route table**.
- **Default route table** includes a **local route** for inter-subnet communication.
- **Custom route tables** allow finer control over traffic paths for public/private subnet configurations.
