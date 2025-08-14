# 🌐 Bring Your Own IP Address (BYOIP)

## Overview
Normally, public IP addresses in Oracle Cloud Infrastructure (OCI) are **owned by Oracle**.  
With **Bring Your Own IP (BYOIP)**, you can migrate your **own IPv4 CIDR block** or **IPv6 prefix** from your **on-premises environment** to OCI.

### Why Use BYOIP?
- **Smooth migration** when applications have **hard-coded IP addresses**.
- **Solution continuity** without having to change existing IPs.
- Useful for services that rely on **specific IP reputation** or **contiguous IP space**.

---

## 📏 Requirements & Limits

- **Ownership validation**:  
  - The IPv4 CIDR or IPv6 prefix must be **registered with a supported Regional Internet Registry (RIR)**.
  - Oracle validates your ownership before import.
  
- **IPv4**:
  - Minimum: `/24`
  - Maximum: `/8`
  
- **IPv6**:
  - Minimum: `/48` or larger

---

## 🔹 High-Level Process

1. **Request Import**
   - You request to import a **public IPv4 CIDR** or **IPv6 prefix** that you own.

2. **Verification Token**
   - Oracle issues a **verification token**.
   - You add this token to the RIR record for your IP address space.

3. **Create ROA (Route Origin Authorization)**
   - ROA is created with your **RIR**.
   - You provide Oracle's **BGP ASN** for the commercial cloud.
   - ROA authorizes Oracle to **advertise your CIDR block**.

4. **Oracle Validation**
   - Oracle contacts the RIR to verify:
     - Ownership of the CIDR/prefix.
     - Presence of the verification token.
   - Token update typically takes **~1 day**.

5. **Provisioning**
   - Oracle provisions your BYOIP range into your **tenancy compartment**.
   - You can then **manage these IPs** through **IP pools** (IPv4 only).

---

## 📅 Timeline
- **Verification token update**: ~1 day
- **Full import process**: Up to **10 business days**

---

## 📌 Benefits of BYOIP
- **Smooth migration** for workloads with fixed IP addresses.
- **Summarize** IPv4 addresses into pools for deployment (e.g., load balancers).
- **IP reputation** retention for trusted address ranges.
- **Flexibility** to advertise your IP range to the internet.

---

## 🔄 Workflow Diagram (Text Version)

```mermaid
flowchart LR
    A[Request Import] --> B[Receive Token]
    B --> C[Add Token to RIR]
    C --> D[Create ROA with RIR using Oracle BGP ASN]
    D --> E[Oracle Validates Ownership]
    E --> F[Provision to Compartment]
```

✅ Once provisioned, you can **assign** these IPs to your OCI resources just like Oracle-assigned addresses.
