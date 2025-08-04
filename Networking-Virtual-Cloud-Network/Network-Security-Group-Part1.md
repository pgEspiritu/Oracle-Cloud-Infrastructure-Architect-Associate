# 🔐 Lesson: Network Security Group (NSG)

## 📘 What is a Network Security Group?

A **Network Security Group (NSG)** is a **virtual firewall** that allows you to define:

1. **Ingress (Inbound)** and **Egress (Outbound)** security rules
2. The **VNICs** (Virtual Network Interface Cards) the rules apply to

While commonly associated with **Compute instances**, NSGs also support other OCI resources, including:

- Load Balancers  
- Mount Targets  
- API Gateways  

---

## 🔁 Ingress vs. Egress Rules

### 📥 Ingress Rule (Traffic **into** the instance)
Associated with:
- **Source Type** (CIDR, Service, NSG)
- **Source** (based on source type)
- **IP Protocol** (e.g., TCP, ICMP, UDP, etc.)
- **Source Port Range** *(optional)*
- **Destination Port Range** *(auto-filled based on protocol)*

### 📤 Egress Rule (Traffic **out of** the instance)
Associated with:
- **Destination Type** (CIDR, Service, NSG)
- **Destination** (based on destination type)
- **IP Protocol**
- **Source Port Range** *(optional)*
- **Destination Port Range** *(optional)*

---

## 🧱 NSG Association

Once you've defined your NSG and its rules:
- You can **associate** the NSG to one or more **VNICs**.
- This makes it easy to manage rules at the instance or service level.

---

## ⚖️ Stateful vs Stateless Rules

| Rule Type  | Behavior |
|------------|----------|
| **Stateful**  | Responses are **automatically tracked and allowed**. No separate egress/ingress rule required for return traffic. |
| **Stateless** | Responses are **not automatically allowed**. You must define **both ingress and egress** rules. |

### 🧠 Example:
If an ingress rule allows HTTP (`port 80`) access from `0.0.0.0/0`:
- **Stateful**: The response is automatically allowed.
- **Stateless**: You must create a separate **egress** rule to allow the response.

---

## 🧩 Use Case: NSG for Tiered Architecture

Imagine your VCN has different **tiers**:
- **Web Tier**: 3 instances
- **App Tier**: 2 instances

You can:
- Assign all **Web Tier** instances to **NSG-1**
- Assign all **App Tier** instances to **NSG-2**

Then configure NSG rules like:
- NSG-2 allows ingress **from** NSG-1
  - This enables **Web Tier → App Tier** communication.
  - Source type: `NSG`
  - Source: `NSG-1`

---

## ✅ Summary

- NSG is a flexible firewall construct in OCI.
- Rules can be applied to VNICs and grouped by role or tier.
- Supports **CIDR**, **Service**, and **NSG** as source/destination types.
- Helps in building secure, modular network architectures.
