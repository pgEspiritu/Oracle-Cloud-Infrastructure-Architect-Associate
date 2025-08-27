# Web Application Acceleration Demonstration

## Setup Overview

- **Instances:** 2 instances running in a **private subnet** (no public IP).
- **Load Balancer:** A **public load balancer** with a public IP address.
- **Traffic Flow:**  
  - Accessing the load balancer IP alternates requests between **instance-1** and **instance-2**.  

Currently, the load balancer has **no acceleration policy** associated.

---

## Creating a Web Application Acceleration Policy

1. Go to **OCI Console** → **Navigation Menu** → **Networking** → **Web Application Acceleration**.
2. Create a **Web Application Acceleration Policy**:
   - Choose **policy name** and **compartment** (default is fine).
   - Options available:
     - **Caching only**
     - **Caching + Compression**  
       *(Note: compression cannot be enabled without caching).*
3. Enable both **caching** and **compression**.
4. The policy status shows as **Active**.

⚠️ **Note:** The policy will not take effect until it has an **acceleration** attached.

---

## Creating an Acceleration

1. Select **Create Acceleration**.
2. Choose the **compartment** and select the existing **load balancer**.
3. Optionally, create additional accelerations if there are multiple load balancers.
4. Click **Create Acceleration**.  
   - Status changes from **Creating** → **Active**.  
   - The acceleration is now attached to the selected load balancer.

---

## Enabling Logs

1. Enable logs for the acceleration.
   - Choose a **log group** and **log name**.
2. Access the logs to verify activity.

---

## Verifying Web Application Acceleration

- In the logs, observe the **cache status**:
  - `HIT` → request served from **cache**.
  - `MISS` → request served from **backend server**.
- Compression details are also visible in the logs.
- The **cache key** format is displayed within the request logs.

---

## Summary

- Configured a **web application acceleration policy** with **caching + compression**.
- Created an **acceleration** and attached it to a load balancer.
- Verified functionality through logs (`HIT` / `MISS` cache status and compression info).
