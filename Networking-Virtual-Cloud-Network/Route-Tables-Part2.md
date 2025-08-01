# 📘 OCI Route Tables – Deep Dive

## 🧠 Route Table Basics

- A **Route Table** defines the **path for outbound traffic** from a VCN.
- Local traffic (i.e., between subnets in the same VCN) is handled via the **implicit local route**.
- Each **subnet must be associated with exactly one route table**.
- A single **route table can be associated with multiple subnets**.

### ❗ Important Rule:
> **One subnet ➡️ One route table**  
> **One route table ➡️ Many subnets** ✅  
> **One subnet ➡️ Many route tables** ❌

---

## 🔁 Implicit Local Routing

- Every route table (default or custom) contains an **implicit local route**.
- This allows **communication between subnets within the same VCN**.
- This **local route is not visible** in the console (you'll see “0 rules” even though it's functioning).

---

## 📐 Specificity in Routing Rules

> **Most specific route wins** in case of overlapping route rules.

### Example:

| Destination CIDR | Target            |
|------------------|-------------------|
| `0.0.0.0/0`      | Internet Gateway  |
| `123.45.67.0/24` | Service Gateway   |

- If traffic is destined to `123.45.67.10` (part of both ranges), it will go to the **Service Gateway**, because `/24` is more specific than `/0`.

### Key Concept:
- **Smaller CIDR range** = **More specific**
- If **no matching route** is found → traffic is **dropped**

---

## 🧱 Route Table Structure

Each route rule contains:

| Field                | Description                   |
|----------------------|-------------------------------|
| **Destination CIDR** | IP range for the destination  |
| **Target**           | Next hop (gateway, IP, etc.)  |

### Example for Public Subnet:
| Destination CIDR     | Target            |
|----------------------|-------------------|
| `0.0.0.0/0`          | Internet Gateway  |

### Example for Private Subnet:
| Destination CIDR     | Target            |
|----------------------|-------------------|
| `0.0.0.0/0`          | NAT Gateway       |
| `object_storage_cidr`| Service Gateway   |

---

## 🧭 Supported Route Targets

| Target Type              | Use Case                                                                 |
|--------------------------|--------------------------------------------------------------------------|
| **Internet Gateway**     | Public subnet internet access                                            |
| **NAT Gateway**          | Outbound internet access for private subnet (unidirectional)             |
| **Service Gateway**      | Private access to Oracle services (e.g., Object Storage)                 |
| **Local Peering Gateway**| Access between VCNs in same region                                       |
| **Dynamic Routing Gateway** | Access to/from on-premise via FastConnect or VPN                       |
| **Private IP**           | Route directly to a specific private IP (e.g., for virtual appliances)   |

---

## 📊 Visual: Routing Example

### Setup:

- **VCN**
  - **Public Subnet**
    - Uses **Internet Gateway**
  - **Private Subnet**
    - Uses **NAT Gateway** for internet-bound patch downloads
    - Uses **Service Gateway** for Oracle service access (e.g., Object Storage)

### Private Subnet Route Table:

| Destination CIDR     | Target            |
|----------------------|-------------------|
| `0.0.0.0/0`          | NAT Gateway       |
| `object_storage_cidr`| Service Gateway   |

> In case of overlap, **Service Gateway** is chosen due to specificity.

---

## ✅ Summary

- Route tables determine how **outbound traffic** flows.
- Each **subnet** can have only **one associated route table**.
- **Implicit local routes** allow intra-VCN subnet communication.
- **Most specific CIDR match** wins in case of overlapping rules.
- Various **targets** enable internet access, Oracle service access, peering, and on-prem connectivity.
