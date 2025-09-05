# Demonstration: Geolocation Steering Policy Type

## Overview
This demonstration shows how to configure and test a **Geolocation Steering Policy** in Oracle Cloud Infrastructure (OCI).  
With geolocation policies, DNS traffic is directed to different endpoints based on the **geographic location of the end user**.

---

## Setup

### Regions & Web Servers
- **Endpoint 1:** Phoenix (Compute Instance) → returns *Phoenix compute instance*  
- **Endpoint 2:** Sydney (Compute Instance) → returns *Sydney compute instance*  

### Test Clients
- **US-based client:** Windows instance in Phoenix  
- **Australia-based client:** Windows instance in Sydney  
- **India-based client:** Local test system  

### Public DNS Zone
- Domain: `samvit.site`  
- Records present:  
  - **NS (Name Server)**  
  - **SOA (Start of Authority)**  

---

## Demonstration Steps

### 1. Verify Web Servers
- Phoenix → accessible via public IP → displays *Phoenix compute instance*  
- Sydney → accessible via public IP → displays *Sydney compute instance*  

### 2. Create Geolocation Steering Policy
1. Navigate to **Traffic Management → Steering Policies**.  
2. Create a new policy:
   - **Name:** `GeoSteeringPolicy`  
   - **Policy Type:** Geolocation  
   - **TTL:** 60 seconds  
3. Define **Answer Pools**:
   - AP1 (Phoenix) → A record → Phoenix public IP  
   - AP2 (Sydney) → A record → Sydney public IP  
4. Define **Geolocation Rules**:
   - **Rule 1 (United States):** Priority → AP1 (Phoenix), then AP2  
   - **Rule 2 (Australia):** Priority → AP2 (Sydney), then AP1  
5. Add a **Global Catch-All Rule**:
   - Priority → AP1 (Phoenix), then AP2  
6. Attach existing **demo health check** and domain `samvit.site`.  
7. Click **Create Policy**.  

---

## Behavior

### United States Client
- Connected via Windows instance in Phoenix  
- Open `samvit.site` → Resolves to **Phoenix compute instance**  

### Australia Client
- Connected via Windows instance in Sydney  
- Open `samvit.site` → Resolves to **Sydney compute instance**  

### India Client
- Accessed from India (not covered by explicit rules)  
- Global catch-all applies:  
  - First priority AP1 (Phoenix)  
  - Result → **Phoenix compute instance**  

---

## Key Observations
- Geolocation steering policies route traffic **based on user’s geographic origin**.  
- Country-level or continent-level rules can be applied.  
- **Global catch-all** is required to handle unmatched queries consistently.  
- Health checks ensure traffic is sent only to **healthy endpoints**.  

---

## Summary
- **Policy Type:** Geolocation Steering  
- **Endpoints:** Phoenix & Sydney  
- **Domain:** `samvit.site`  
- **Rules:**  
  - US → Phoenix  
  - Australia → Sydney  
  - All others → Phoenix (via global catch-all)  

This demonstration confirms that **Geolocation Steering Policy Type** in OCI correctly directs DNS queries based on the end user’s physical location.
