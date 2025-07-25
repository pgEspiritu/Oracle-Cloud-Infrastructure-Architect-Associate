# 🔍 Overview: VCN Components in OCI

## 🧭 VCN and Subnets

- A **VCN** is a larger network (e.g., `10.0.0.0/16`) that can be subdivided into smaller networks called **Subnets** (e.g., `/24` blocks).
- Example:
  - VCN: `10.0.0.0/16`
  - Subnets:
    - `10.0.1.0/24`
    - `10.0.2.0/24`
    - `10.0.3.0/24`

### 📦 Subnets

- A **subnet** is the basic **unit of configuration** inside a VCN.
- Each subnet:
  - Hosts virtual machine instances (VMs)
  - Is associated with:
    - Route Table
    - Security List
    - DHCP Options

#### 🔑 Types of Subnets

- **Public Subnet** – Instances can access the internet (via Internet Gateway)
- **Private Subnet** – Instances do not have direct access to the internet

---

## 🚦 Route Table

- Think of a route table as the **traffic police** for your VCN.
- It determines **how traffic flows** from subnet to destination.
- Always includes a **default route table**.
- Defines routes based on destination CIDRs and target gateways.

---

## 🧰 DHCP Options

- DHCP = **Dynamic Host Configuration Protocol**
- Used to automatically provide **config settings** (e.g., DNS servers) to VMs when they boot.
- Applied at the **subnet level**.

---

## 🔐 VCN Security Components

### 1. **Security List**
- Acts like a firewall.
- Defines **Ingress** (incoming) and **Egress** (outgoing) rules.
- Associated with **subnets**

### 2. **Network Security Group (NSG)**
- Similar to Security Lists but more flexible.
- Associated with **individual VNICs** (Virtual Network Interface Cards)
- Enables **fine-grained control** over traffic per resource

---

## 🌉 VCN Gateways

Just like you need a **gate** to leave your house, VCN requires gateways to route traffic out of (or into) the VCN.

### 🧩 Types of Gateways:

| Gateway Type       | Purpose                                                        |
|--------------------|----------------------------------------------------------------|
| **Internet Gateway** | Allows public subnet instances to access the internet         |
| **NAT Gateway**      | Allows private subnet instances to access the internet **outbound only** |
| **Service Gateway**  | Allows access to **OCI services** (e.g., Object Storage) **without using the internet** |

---

## 🗺️ Architecture Snapshot

- Region → VCN → Subnets (Public & Private)
- VCN components:
  - 🗂️ Subnets (unit of configuration)
  - 🧭 Route Tables (traffic flow control)
  - 🧰 DHCP Options (boot-time config)
  - 🔐 Security List & NSG (firewall & security)
  - 🌉 Gateways (external/internal access)

---

## 📌 Summary

| Component            | Purpose                                       | Scope             |
|----------------------|-----------------------------------------------|-------------------|
| **Subnet**           | Divides VCN into smaller networks              | VCN               |
| **Route Table**      | Controls routing of traffic                    | Subnet            |
| **DHCP Options**     | Provides auto-configuration to VMs             | Subnet            |
| **Security List**    | Ingress/Egress rules                           | Subnet            |
| **Network Security Group (NSG)** | Fine-grained security rules              | VNIC              |
| **Internet Gateway** | Public internet access                         | VCN               |
| **NAT Gateway**      | Outbound access for private instances          | VCN               |
| **Service Gateway**  | Access to OCI services like Object Storage     | VCN               |

