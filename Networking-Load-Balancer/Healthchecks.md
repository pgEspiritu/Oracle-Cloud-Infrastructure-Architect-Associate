# Lesson on Load Balancer Health Checks

## Introduction
In a load balancer setup, client requests are distributed to multiple backend servers.  
But what happens if one backend server fails?  

👉 To prevent traffic from being sent to an unhealthy server, **Load Balancer Health Checks** are used.  

Think of it like a personal health check:  
- If you’re sick, your manager won’t assign you tasks.  
- Similarly, if a backend server is unhealthy, the load balancer temporarily removes it from rotation.  

---

## What is a Health Check?
A **health check** continuously monitors the status of backend servers and ensures that only healthy servers receive traffic.  
- If a server fails, the load balancer **stops sending traffic** to it.  
- When the server recovers, the load balancer can put it back into rotation.  

---

## Types of Health Checks
Health checks can be configured at different levels:
- **Backend**
- **Backend Set**
- **Overall Load Balancer**

Two main methods are available:

1. **TCP Health Check**  
   - Creates a **connection attempt** at the TCP level.  

2. **HTTP Health Check**  
   - Sends an **HTTP request** and evaluates the response.  

⚠️ Always choose the health check protocol that matches your application or service.  

---

## Health Check Configuration Options

When creating a health check, you specify several parameters:

- **Protocol**  
  - `HTTP` or `TCP`  

- **Interval (milliseconds)**  
  - Frequency of checks.  
  - Default = **10,000 ms (10 seconds)**  

- **Timeout (milliseconds)**  
  - Maximum time to wait for a response from the backend.  
  - If no response within the timeout → check considered failed.  

- **Number of Retries**  
  - Number of failed checks before a backend is marked **unhealthy**.  
  - Also applies when determining if a backend has recovered.  
  - Default = **3 retries**  

---

## Example Flow
1. Load balancer sends a health check request.  
2. Backend server responds within timeout → **Healthy**.  
3. Backend fails to respond three times (default retries) → **Unhealthy**.  
4. Load balancer removes it from rotation until it recovers.  

---

## Conclusion
- Health checks ensure **high availability and reliability** of services.  
- They work at **TCP or HTTP levels**, based on protocol selection.  
- Parameters like **interval, timeout, and retries** help fine-tune monitoring.  
