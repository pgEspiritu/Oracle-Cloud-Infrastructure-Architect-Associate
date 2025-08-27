# Web Application Acceleration (OCI)

## What is Web Application Acceleration?
- A service that **enhances application performance** by:
  1. **Caching** responses.  
  2. **Compression** of data.  

- Benefits:
  - Reduces **application latency**.
  - Reduces **load on backend servers**.
  - Improves **customer experience**.

---

## How It Works
1. **Create a Web Application Acceleration Policy**:
   - Option 1: Caching only.  
   - Option 2: Caching + Compression.

2. **Create an Acceleration Resource**:
   - A policy alone is not enough.  
   - You must bind the policy to a **specific load balancer** via an **acceleration resource**.

3. **Policy Reuse**:
   - One WAA policy can be applied to **multiple load balancers**.  
   - Each load balancer requires its **own acceleration resource** referencing the same policy.

---

## Example Scenario
- **Application Hosting Tenancy** with remote users (from on-premises or internet).  
- Users access the application via a **Layer 7 HTTP load balancer**.  
- **Web Application Acceleration enabled** on the load balancer.

### Outcomes
- **Improved customer experience** by reducing latency.  
- **Reduced backend server load** via caching.  
- **Reduced network load** via compression.

---

## Key Scenarios
1. **Improve application performance & decrease server load**  
   - Achieved through **caching**.

2. **Reduce network load & decrease latency**  
   - Achieved through **compression**.

---

## Summary
- Web Application Acceleration is designed to **speed up traffic on Layer 7 (HTTP) load balancers**.  
- Works through a combination of **caching and compression**.  
- Requires:
  - A **policy** (defines caching/compression).  
  - An **acceleration resource** (binds policy to a load balancer).  
- One policy can serve multiple load balancers, each with its own acceleration resource.

