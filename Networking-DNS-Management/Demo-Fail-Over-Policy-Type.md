# Demonstration: Failover Policy Type

## Overview
This demonstration shows how to configure and test a **Failover Traffic Management Steering Policy** in Oracle Cloud Infrastructure (OCI).  
Failover ensures that DNS traffic is routed to a **primary endpoint** when healthy, and automatically rerouted to a **secondary endpoint** when the primary becomes unavailable.

---

## Setup

### Regions & Web Servers
- **Primary region:** Phoenix  
- **Secondary region:** Sydney  
- Web servers are running in both Phoenix and Sydney.

### Public DNS Zone
- DNS zone: `samvit.site`  
- Records present:  
  - **NS (Name Server)**  
  - **SOA (Start of Authority)**  

---

## Demonstration Steps

### 1. Verify Web Servers
- Phoenix web server: displays `Phoenix compute instance`.
- Sydney web server: displays `Sydney compute instance`.

### 2. Create a Failover Policy
1. Navigate to **Traffic Management → Steering Policies**.
2. Create a new policy:
   - **Name:** `failover-policy`  
   - **TTL:** 60 seconds  
3. Define **Answer Pools**:
   - **AP1 (Primary)**  
     - Name: Phoenix  
     - Type: A  
     - Value: Public IP of Phoenix web server  
   - **AP2 (Secondary)**  
     - Name: Sydney  
     - Type: A  
     - Value: Public IP of Sydney web server  
4. Set **Pool Priority**:  
   - Primary: AP1 (Phoenix)  
   - Secondary: AP2 (Sydney)  
5. Create a **Health Check**:
   - Name: `demo-health-check`  
   - Interval: 10–30 seconds  
   - Protocol: HTTP  
6. Attach domain `samvit.site` to the steering policy.  

---

## Behavior

### Normal Operation
- When both Phoenix and Sydney are **healthy**:
  - DNS queries for `samvit.site` resolve to **Phoenix** (primary).  
  - Browser shows **Phoenix compute instance**.  

### Failover Simulation
- Stop the Phoenix compute instance to simulate a failure.  
- Health check marks **AP1 (Phoenix)** as **unhealthy**.  
- DNS queries are now resolved to **AP2 (Sydney)**.  
- Browser shows **Sydney compute instance**.  

---

## Key Observations
- Failover policies ensure **high availability** by rerouting traffic when the primary endpoint fails.
- Health checks play a crucial role in detecting endpoint availability.
- DNS caching and TTL (60s here) affect how quickly changes propagate.

---

## Summary
- **Primary Region:** Phoenix  
- **Secondary Region:** Sydney  
- **Domain:** `samvit.site`  
- **Failover Behavior:**  
  - Normal: traffic → Phoenix  
  - On failure: traffic → Sydney  
