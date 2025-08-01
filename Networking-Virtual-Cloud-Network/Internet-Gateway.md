# Internet Gateway in Oracle Cloud Infrastructure (OCI)

## Introduction

## Whiteboarding the Concept

Let's visualize the relationship between a **Virtual Cloud Network (VCN)** and the **Internet**.

```plaintext
Internet → VCN    (Ingress Traffic)
VCN → Internet    (Egress Traffic)
```

- Ingress: Traffic coming into the VCN from the internet.
- Egress: Traffic going out of the VCN to the internet.

An Internet Gateway (IG) supports both ingress and egress traffic.

---

## 🧠 Key Concepts

- An **Internet Gateway** enables **direct, bidirectional communication** between your VCN and the internet.
- Only **one Internet Gateway** is needed (and allowed) per VCN.
- It is a **fully managed service** by OCI — no need to worry about:
  - Scalability  
  - Fault tolerance  
  - High availability  

---

## 📋 Requirements for Internet Access

To allow an instance in your VCN to access the internet via an Internet Gateway, the following must be true:

1. The **instance must be in a public subnet**
2. The **instance must have a public IP address**
3. The **subnet's route table** must include a valid rule with the Internet Gateway as the **target**

> ⚠️ **Note**: You also need to **open the appropriate ports** using **Security Lists** or **Network Security Groups** (not covered here).

---

## 🛣️ Route Table Example

For instances in a public subnet, here's how a route table entry for internet access would look:

| Destination CIDR | Target           |
|------------------|------------------|
| `0.0.0.0/0`      | Internet Gateway |

This rule allows **all traffic** to be routed to the Internet Gateway.

---

## ✅ Summary

- Internet Gateway enables **direct internet access** for instances in a VCN.
- It supports **bidirectional traffic**: both ingress and egress.
- Only **one IG per VCN** is allowed.

### Key Requirements

- Public Subnet  
- Public IP Address  
- Route Table with Internet Gateway as target  
- Security Rules allowing traffic  

> ☑️ Be sure to configure **security rules** correctly to allow traffic to flow **in and out** of your instances.

