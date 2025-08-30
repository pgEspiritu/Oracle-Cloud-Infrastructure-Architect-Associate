# DNS Zones

## What is a Zone?
A **DNS zone** is a portion of the DNS namespace managed by a specific organization or administrator.  
It acts as an **administrative space** that provides granular control of DNS components, especially authoritative nameservers.

- Zones contain **trusted DNS records** (e.g., `A`, `AAAA`, `MX`, `CNAME`).
- These records are stored on **OCI nameservers**.
- When a zone is created, the following records are automatically added:
  - **Nameserver (NS) Record**
  - **Start of Authority (SOA) Record**

---

## Types of Zones in OCI

### 1. Public Zone
- Holds trusted DNS records.
- Records reside on **OCI nameservers**.
- Accessible from the **public internet**.

### 2. Private Zone
- Contains domain names that resolve DNS queries for **private addresses**.
- Used within a **Virtual Cloud Network (VCN)**.
- Provides internal DNS resolution not visible on the public internet.

---

## Summary
- A **zone** = portion of DNS namespace controlled by an organization/administrator.  
- Each zone automatically includes **NS** and **SOA** records.  
- **Public Zones** handle public-facing DNS records.  
- **Private Zones** resolve DNS queries inside a **VCN**.  
