# Traffic Management in OCI DNS

## Overview
**Traffic Management** in OCI DNS provides **intelligent responses** to DNS queries based on defined conditions.  
Instead of always returning a static record from a public DNS zone, traffic management allows routing decisions depending on **geography, endpoint health, or policies**.

---

## How It Works
1. A user queries a domain (e.g., `abc.com`).
2. The query passes through the **Traffic Management Service**.
3. Based on predefined **conditions**, the service routes traffic to the appropriate endpoint:
   - Endpoint 1
   - Endpoint 2
   - Endpoint 3

### Example Conditions
- **Geolocation** of the requester  
- **Health checks** on endpoints  
- **Load balancing** requirements  
- **Failover policies** (fallback to another endpoint if the primary is down)  

---

## Components of Traffic Management

### 1. **Steering Policies**
- Framework to define the **logic** for DNS responses.
- Types of steering policies:
  - **Failover** – direct traffic to a primary endpoint; fallback if unavailable.
  - **Load Balancer** – distribute queries across multiple endpoints.
  - **Geolocation** – route based on user’s location.
  - **ASN (Autonomous System Number)** – route based on the network/ISP.
  - **IP Prefix** – route based on IP address range.

---

### 2. **Attachment**
- Links a **Steering Policy** to a **Public DNS Zone**.  
- Once attached, the **DNS response is constructed from the steering policy**, not the static records in the zone.  

---

### 3. **Rules**
- Define **guidelines** steering policies use to filter DNS answers.
- Examples:
  - Route based on **geolocation**.
  - Route based on **endpoint health**.

---

### 4. **Answers**
- **Answer Pools** contain the DNS records that can be served as responses.
- Example:
  - Endpoint 1: `192.0.2.1`
  - Endpoint 2: `192.0.2.2`
  - Endpoint 3: `192.0.2.3`

---

## Summary
- Traffic Management = Intelligent DNS query responses.  
- Built around **Steering Policies** that define logic for routing traffic.  
- Supports **failover, load balancing, geolocation, ASN, and IP prefix** steering.  
- Uses **attachments** to link policies with zones.  
- Responses are selected from **answer pools** instead of static zone records.  
