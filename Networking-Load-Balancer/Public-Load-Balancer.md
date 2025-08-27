# Public Load Balancers (OCI)

## Availability Domains and VCN
- Example assumes a **multi-AD region** (3 Availability Domains):
  - AD1
  - AD2
  - AD3
- A **VCN spans across multiple Availability Domains**.
- Subnets in OCI can be of two types:
  1. **AD-specific subnets** (e.g., Subnet1, Subnet2, Subnet3)
  2. **Regional subnet** (e.g., Subnet4) → spans across multiple ADs.

---

## Placement of Public Load Balancers
- A **public load balancer must be created in a public subnet**.
- It **cannot** be created in a private subnet.
- Public load balancer is assigned a **public IP address**, allowing it to:
  - Receive traffic directly from the internet.

### Scope
- The scope of a public load balancer is **regional**.
- Requirements:
  - **Preferred:** A regional subnet (e.g., Subnet4).
  - **Alternative:** Two AD-specific subnets (e.g., Subnet1 & Subnet2).

---

## Load Balancer Architecture

### Regional Subnet Case
- OCI provisions:
  - **Primary load balancer** in one AD.
  - **Standby load balancer** in another AD.
- Benefit: Survives AD outage → service remains accessible.
- Traffic handling:
  - Normal case → traffic distributed via active (primary) load balancer.
  - AD outage → traffic routed via standby load balancer.
- A **floating public IP** is attached to the active load balancer, and switches to standby in case of failover.

### AD-Specific Subnet Case
- If using two AD-specific subnets:
  - One hosts the **primary load balancer**.
  - Another hosts the **standby load balancer**.
- Behavior:
  - Normal case → traffic flows via primary.
  - AD outage → traffic flows via standby.
- **Note:** From OCI’s perspective, both load balancers are equivalent.  
  You **cannot specify** which is primary or standby.

---

## IP Address Requirements
- Each load balancer requires:
  - **1 private IP address** from its host subnet.
  - **1 public IP address** for internet access.
- Since there are primary and standby load balancers:
  - Both require private IPs in addition to the shared floating public IP.

---

## Key Takeaways
- Public load balancer **must be in a public subnet**.
- **Scope is regional**.
- Requires either:
  - A **regional subnet**, or
  - Two **AD-specific subnets**.
- OCI provisions **active + standby load balancers** for redundancy.
- A **floating public IP** ensures failover between them.
- **Primary vs. standby** is only conceptual; both are equivalent in OCI’s architecture.

---

## Summary
Public load balancers in OCI are designed for **high availability** across availability domains.  
They ensure that even if an AD experiences an outage, traffic can still be routed seamlessly through the standby load balancer using the floating public IP.
