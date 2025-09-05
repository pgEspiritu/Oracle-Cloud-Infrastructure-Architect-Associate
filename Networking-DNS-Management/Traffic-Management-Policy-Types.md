# Traffic Management Steering Policy Types

## Overview
OCI Traffic Management supports multiple **steering policies** that define how DNS queries are answered.  
These policies enable intelligent routing decisions based on **priority, load, geography, network, or IP prefixes**.

---

## Policy Types

### 1. Failover Policy
- **Purpose:** Provide high availability by routing traffic to a secondary endpoint when the primary becomes unhealthy.
- **How it works:**
  - Endpoints are prioritized (e.g., Primary → Secondary).
  - OCI **Health Checks** monitor the endpoints.
  - Traffic is routed to the primary when healthy; otherwise, to the secondary.

---

### 2. Load Balancer Policy
- **Purpose:** Distribute DNS traffic across multiple endpoints.
- **Features:**
  - Support for **weighted distribution**:
    - Example: `50/50` split evenly.
    - Example: `10/90` custom distribution.
  - If one endpoint becomes unhealthy, traffic is automatically shifted to healthy endpoints.

---

### 3. Geolocation Steering Policy
- **Purpose:** Route DNS traffic based on the **end user’s physical location**.
- **Example:**
  - Users in **Australia** → Endpoint A.
  - Users in **North America** → Endpoint B.

---

### 4. ASN (Autonomous System Number) Steering Policy
- **Purpose:** Route DNS traffic based on the **network/ISP** identified by ASN.
- **Example:** Queries from a specific ASN can be directed to a designated endpoint.

---

### 5. IP Prefix Steering Policy
- **Purpose:** Route DNS traffic based on the **IP prefix** of the originating query.
- **Use case:** Differentiate responses between **internal vs. external users**.

---

## Common Use Cases

1. **Automated Failover**
   - Seamlessly switch traffic between primary and secondary servers.  

2. **Cloud Migration**
   - Use **weighted load balancing** to gradually migrate traffic:
     - Start with 10% traffic to the new resource.
     - Increase gradually until 100% migration is complete.

3. **Load Balancing & Scale**
   - Distribute traffic across multiple servers, regardless of location.

4. **Multi-Cloud / Hybrid**
   - Traffic can be routed to OCI, other cloud providers, or **on-premises data centers**.
   - Requirement: endpoints must be **publicly resolvable**.

5. **Worldwide Geolocation Steering**
   - Partition global users into regions (e.g., country-level routing).
   - Direct users to region-specific infrastructure.

6. **Canary Testing**
   - Use **IP Prefix Steering** to test new features with specific user groups.

7. **Zero-Rating Services**
   - Use **ASN Steering** to provide free resources to certain ISPs or enterprises, while directing others to paid resources.

---

## Summary
- OCI Traffic Management offers **five policy types**:
  - Failover
  - Load Balancer
  - Geolocation
  - ASN
  - IP Prefix
- These enable **resiliency, controlled migration, global routing, testing, and differentiated service delivery**.
- Policies are flexible and can steer traffic to OCI, other clouds, or on-prem environments, as long as endpoints are public.

---
