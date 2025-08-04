# 🔐 Lesson: Security List in OCI

## 📘 What is a Security List?

A **Security List** in Oracle Cloud Infrastructure (OCI) is a virtual firewall construct that:

- Contains **Ingress** (inbound) and **Egress** (outbound) rules
- Applies **at the subnet level**
- Is **enforced at the VNIC level**

---

## 🔄 Comparison: Security List vs. Network Security Group

| Feature | Security List | Network Security Group (NSG) |
|--------|----------------|-------------------------------|
| **Association** | Subnet-wide | Per-VNIC |
| **Granularity** | Broad | Fine-grained |
| **Enforcement** | At the VNIC | At the VNIC |
| **Source Types** | CIDR, Service | CIDR, Service, NSG |
| **Use Case** | Apply uniform rules to all instances in a subnet | Apply custom rules to specific instances/VNICs |

---

## 🛡️ Rule Types in Security List

- **Ingress Rules**: Define what traffic is allowed *into* the subnet
- **Egress Rules**: Define what traffic is allowed *out* of the subnet
- Both support **stateful** or **stateless** types

📌 *Stateful means return traffic is automatically allowed.*

---

## 🧱 Security List Architecture Example

Imagine a **VCN** with three subnets: A, B, and C.

All three subnets are associated with a **common Security List** which contains:

- ✅ An **Ingress rule** (e.g., allow port 22 for SSH)
- ✅ An **Egress rule** (e.g., allow all outbound traffic)

This means:
- All **instances in all three subnets** follow the same security rules
- It's a **centralized way to enforce policy**

---

## 🔀 Using Security List and NSG Together

You can:

- Use **only Security List**
- Use **only NSG**
- Use **both** — and when you do, the **effective rule set is a UNION**

✅ **Guiding Principle:**  
> If either the NSG or Security List **allows** a packet, it is allowed.

---

## 🎯 Use Case for Security List

If you want **all instances across subnets** to follow the same security policy, you can:

1. Define rules in a **Security List**
2. Associate that list with **every subnet** in the VCN

---

## 🚫 Security List Limitation

Unlike NSGs, **Security Lists cannot reference another Security List** as a source/destination.

| Rule Property | Security List | NSG |
|---------------|----------------|-----|
| CIDR | ✅ | ✅ |
| Service | ✅ | ✅ |
| NSG | ❌ | ✅ |

---

## 🧠 Key Takeaways

- Security Lists offer **subnet-level control**
- NSGs offer **VNIC-level granularity**
- Both use **ingress/egress** rules to manage traffic
- Use them **together** for layered security
- Rule evaluation is **allow-based**; if one rule allows, the traffic is permitted
