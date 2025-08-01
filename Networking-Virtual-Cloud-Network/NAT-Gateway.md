# NAT Gateway in OCI

## 📌 What is NAT?

**NAT** stands for **Network Address Translation**. The main purpose of a **NAT gateway** is to provide **instances in a private subnet access to the internet** without exposing them to inbound internet traffic.

---

## 🧠 Why Do We Need NAT Gateway?

- In a **VCN (Virtual Cloud Network)**, instances inside a **private subnet** do **not** have public IP addresses.
- As a result, they **cannot access the internet directly**.
- A **NAT gateway** helps these private instances **initiate outbound connections to the internet** and **receive responses**.
- However, they **cannot receive inbound connections** initiated from the internet.
- So, **NAT is unidirectional** – **outbound only**.

---

## 🖼 Visual Overview

Imagine the following:
```text
Internet <---|--- NAT Gateway ---|-- Private Subnet -- Instance
(outbound only) (no public IP)
```


- The instance can:
  - Initiate connections to the internet ✅
  - Receive responses to those connections ✅
  - **NOT receive** unsolicited inbound traffic from the internet ❌

---

## 🌐 Source IP for Outbound Traffic

- Since private instances lack public IPs, the **NAT gateway’s public IP** is used as the **source IP** for outbound traffic.
- The NAT gateway is automatically assigned a **public IP** when created:
  - **Ephemeral IP** (temporary, assigned by Oracle)
  - **Reserved IP** (user-assigned, persistent)

---

## 📡 Supported Traffic Types

The NAT gateway supports:

- ✅ **TCP**
- ✅ **UDP**
- ✅ **ICMP (ping)**

---

## 🚫 Blocking Traffic via NAT Gateway

- NAT gateways have an **optional feature** to **block all traffic**, regardless of:
  - Route tables
  - Security list rules
- When enabled, **all traffic through the NAT gateway is denied**.

---

## 🧱 Common Use Case

- **Database servers** in private subnets often need to **download patches or updates from the internet**.
- Using a NAT gateway allows them to do this **securely** without being exposed.

---

## 🧮 Data Points

- **Concurrent Connections Supported**: 20,000+
- **Public IP Options**:
  - **Ephemeral** (auto-assigned, temporary)
  - **Reserved** (user-assigned, permanent)

---

## 📍 Routing Considerations

- Instances in private subnet must be associated with a **route table** that directs traffic to the **NAT gateway** for internet-bound traffic.

**Important Limitation**:
- A NAT gateway can only be used by **resources in the same VCN**.
  - ❌ Resources in **peered VCNs** cannot use it.
  - ❌ Resources in **on-premises networks** connected to the VCN cannot use it.

---

## 🔒 Security Implication

- NAT gateway ensures **inbound traffic from the internet is blocked**.
- This makes it ideal for hosting **sensitive workloads** like databases that need outbound internet access (e.g., for patches) but should not be exposed.

---

## 🧭 Summary

- NAT Gateway enables **secure, outbound internet access** for private instances.
- It maintains **unidirectional connectivity** and enforces **strong security posture**.
- It is **highly available**, **managed**, and **supports key protocols** like TCP, UDP, and ICMP.

---

> ✅ **Key takeaway**: Use a NAT gateway when you need **outbound internet access** from private instances, without exposing them to inbound traffic.
