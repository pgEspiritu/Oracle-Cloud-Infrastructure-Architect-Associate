# Demonstration: Load Balancer Policy Type

## Overview
This demonstration shows how to configure and test a **Load Balancer Traffic Management Steering Policy** in Oracle Cloud Infrastructure (OCI).  
Load balancer policies distribute DNS traffic across multiple endpoints based on **weights** that you define.

---

## Setup

### Regions & Web Servers
- **Endpoint 1:** Phoenix (Compute Instance)  
- **Endpoint 2:** Sydney (Compute Instance)  

### Public DNS Zone
- DNS zone: `samvit.site`  
- Records present:  
  - **NS (Name Server)**  
  - **SOA (Start of Authority)**  

---

## Demonstration Steps

### 1. Verify Web Servers
- Phoenix web server: `Phoenix compute instance`  
- Sydney web server: `Sydney compute instance`  

### 2. Create a Load Balancer Policy
1. Navigate to **Traffic Management → Steering Policies**.
2. Create a new policy:
   - **Name:** `LBPolicy`  
   - **TTL:** 60 seconds  
   - **Max Answer Count:** Default  
3. Define **Answer Pools**:
   - Phoenix (A record, public IP of Phoenix instance) → Weight: **10**  
   - Sydney (A record, public IP of Sydney instance) → Weight: **90**  
4. Create a **Health Check**:
   - Name: `demo-health-check`  
   - Interval: 10 seconds  
   - Protocol: HTTP  
5. Attach domain `samvit.site` to this policy.  

---

## Behavior

### Normal Operation
- Both Phoenix and Sydney endpoints are **healthy**.  
- DNS traffic is distributed according to the assigned weights:  
  - **10%** of traffic → Phoenix  
  - **90%** of traffic → Sydney  

### Testing
- Open `samvit.site` in the browser:  
  - Most requests resolve to **Sydney compute instance** (90%).  
  - Some requests resolve to **Phoenix compute instance** (10%).  
- Refreshing the page repeatedly demonstrates weighted distribution.  

---

## Key Observations
- Load balancer policies provide **weighted DNS traffic distribution**.  
- Weights can be adjusted (e.g., **50/50**, **60/40**) to match requirements.  
- If one endpoint becomes **unhealthy**, all traffic is routed to the healthy endpoint.  

---

## Summary
- **Endpoints:** Phoenix & Sydney  
- **Domain:** `samvit.site`  
- **Policy Type:** Load Balancer  
- **Traffic Split (Demo):** Phoenix 10% / Sydney 90%  
- **Failover Behavior:** Traffic automatically shifts if an endpoint is unhealthy  

This demonstration confirms that **Load Balancer Policy Type** in OCI Traffic Management distributes DNS queries across endpoints based on weighted policies.
