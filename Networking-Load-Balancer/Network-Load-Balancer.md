# Network Load Balancer (OCI)

## Introduction
This lesson introduces the **Network Load Balancer (NLB)** in Oracle Cloud Infrastructure (OCI).  
It is a load balancing solution designed to handle **high throughput, low latency, and volatile traffic patterns**.

---

## What is a Network Load Balancer?
- Operates at the **connection level** (Layer 3 / Layer 4 of OSI model).
- Preserves:
  - Source IP
  - Destination IP
  - Source port
  - Destination port
- Designed for:
  - **Ultra-low latency**
  - **High throughput**
  - **Latency-sensitive workloads**

---

## Key Characteristics
- **Preserves source and destination addresses and ports**.
- Provides **high throughput** with **minimal latency**.
- **Elastically scalable**:
  - No need to manually configure bandwidth.
  - Automatically scales up and down with client traffic.
- Best suited for **volatile traffic patterns**.

---

## Load Balancing Policies
Network Load Balancer supports **three hashing policies**:

1. **5-tuple hash (default)**  
   Routes traffic based on:  
   - Source IP  
   - Source Port  
   - Destination IP  
   - Destination Port  
   - Protocol  

2. **3-tuple hash**  
   Routes traffic based on:  
   - Source IP  
   - Destination IP  
   - Protocol  

3. **2-tuple hash**  
   Routes traffic based on:  
   - Source IP  
   - Destination IP  

---

## Summary
- **Network Load Balancer** works at L3/L4, providing high throughput and ultra-low latency.  
- It **preserves IPs and ports**, making it suitable for scenarios requiring transparent traffic forwarding.  
- It is **elastically scalable** and ideal for **latency-sensitive and volatile workloads**.  
- Supported policies: **5-tuple, 3-tuple, 2-tuple hashing**.  


