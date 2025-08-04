# 🔐 Network Security Groups (NSG) – Recap & Deep Dive

## 🔁 What Is a Network Security Group (NSG)?

An NSG acts as a **virtual firewall** at the **VNIC level**, allowing you to define:

- **Ingress rules** (inbound)
- **Egress rules** (outbound)

It applies to multiple OCI resources such as:

- Compute Instances
- Load Balancers
- Mount Targets
- API Gateways

---

## 🔧 NSG Core Components

An NSG consists of:

1. A **set of VNICs** (resources it applies to)
2. A **set of security rules** (ingress/egress)

> ⚠️ All resources using the same NSG **must be in the same Virtual Cloud Network (VCN).**

---

## 🏗 Example Architecture

- VCN with **2 subnets**
- **2 VMs** in **Subnet A**
- **1 VM** in **Subnet B**

### NSG Setup

| NSG     | Rule Type | Direction | Source      | Protocol | Destination Port |
|---------|-----------|-----------|-------------|----------|------------------|
| NSG-A   | Stateful  | Ingress   | `0.0.0.0/0` | TCP      | 80 (HTTP)        |
| NSG-B   | Stateful  | Ingress   | `0.0.0.0/0` | TCP      | 22 (SSH)         |

- NSG-A is associated with **VM 1** and **VM 2**
- NSG-B is associated with **VM 3**

### 💡 Implication:

- Anyone on the internet can **SSH into VM 3** (port 22).
- **Web traffic** on port 80 is allowed to **VM 1 and VM 2**.

---

## 📝 Default vs. Custom NSGs

- When a VCN is created:
  - ✅ A **default route table** is created.
  - ✅ A **default security list** is created.
  - ❌ A **default NSG is *not*** created.

If you want to use NSGs:
> You must explicitly **create** them and **define rules**.

---

## 🎯 NSG Rules: Source/Destination Types

You can define **source** (ingress) or **destination** (egress) as:

- **CIDR Block**
- **OCI Service** (e.g., Object Storage)
- **Another NSG** (must be in same VCN)

> ✅ This allows **tier-to-tier communication** (e.g., Web Tier ↔ App Tier) using NSGs.

---

## ⚖️ Stateful vs. Stateless Rules

| Type      | Behavior |
|-----------|----------|
| **Stateful** | Response traffic is **automatically allowed** (connection tracking enabled). |
| **Stateless** | Response traffic **must be explicitly allowed** via separate rule. |

### 🔄 Example Comparison

#### 1. **Stateful Rule**
- **Ingress Rule**: Allow TCP traffic on port 80 from `0.0.0.0/0`
- ✔️ Response traffic **automatically allowed**
- 📌 Good for general inbound communication

#### 2. **Stateless Rule**
- **Ingress Rule**: Same as above (TCP port 80)
- ❌ Response traffic **blocked** unless...
- **Egress Rule**: Must be defined (e.g., TCP from port 80 to `0.0.0.0/0`)
- 📌 Good for **high-volume, stateless** services like web servers

---

## 💡 When to Use Stateless Rules?

Use stateless rules for **high-throughput, internet-facing services**, such as:

- Public-facing **HTTP/HTTPS** services
- Situations where **connection tracking overhead** should be avoided

---

## ✅ Summary

- NSGs are **fine-grained, instance-level firewalls**
- Ideal for tiered app architectures (Web/App/DB)
- Use **stateful rules** for simplicity and **stateless rules** for performance optimization
- Must be in the **same VCN** to reference other NSGs
