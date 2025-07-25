# 🌐 Virtual Cloud Network (VCN) in OCI

## 📘 What is a VCN?

A **Virtual Cloud Network (VCN)** is a virtual, private, and isolated network in Oracle Cloud Infrastructure (OCI). It is the **core networking construct** and acts like a traditional data center network, but in the cloud.

### 🏢 Analogy:
Think of a VCN like a **private auditorium** inside your company premises — isolated, secure, and dedicated for internal communication.

---

## 🧱 Key Properties of VCN

- Created inside a single **OCI region**
- Can span across **multiple Availability Domains (ADs)** within that region
- Defined using **CIDR blocks**
- Acts as a **software-defined network**

---

## 🧮 CIDR and IP Addressing in VCN

### 📏 CIDR Block Rules:
- **Minimum one CIDR block required**
- Supports up to:
  - **5 IPv4 CIDR blocks**
  - **5 IPv6 CIDR blocks** (if enabled)
- CIDR blocks must be **non-overlapping**
- Can be **resized** after creation

### ✅ CIDR Block Size Range:
- IPv4 VCNs can range from **/16 to /30**

---

## 🧠 Reserved IP Addresses

For a CIDR block like `192.168.0.0/24`, the following IPs are **reserved**:

| IP Address               | Purpose                    |
|--------------------------|----------------------------|
| `192.168.0.0`            | Network Address            |
| `192.168.0.1`            | Subnet Default Gateway     |
| `192.168.0.255`          | Broadcast Address          |

These **cannot** be assigned to compute resources or hosts.

---

## 🏗️ VCN Scope and Regions

- VCNs are **regional constructs**
  - ❌ Cannot span multiple regions
  - ✅ Can span multiple ADs within the same region
- Example:
  - A VCN created in Region 1 cannot extend into Region 2
  - But it can span AD1, AD2, and AD3 **within** Region 1

---

## 🌍 IPv6 Support in VCN

- You can choose:
  - **Oracle-allocated IPv6 prefix** (default is `/56`)
  - **Bring Your Own IPv6 prefix**
- IPv6 support must be **enabled explicitly**

---

## 🔁 Summary

- A **VCN** is a **virtual private network** in OCI.
- Requires at least **one CIDR block** (`/16` to `/30`)
- Supports **IPv4 and IPv6**, up to 5 blocks each
- First two and last IPs in any CIDR block are **reserved**
- VCNs are **regional**, but span across **multiple ADs**

