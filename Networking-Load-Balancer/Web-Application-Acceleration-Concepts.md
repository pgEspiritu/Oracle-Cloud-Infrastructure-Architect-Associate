# Web Application Acceleration Concepts

## Caching
When enabled on a load balancer:
- The **response from backend servers** can be cached.
- Future requests may be served **directly from the load balancer**, without querying the backend servers again.

### Benefits of Caching
1. **Reduced backend load** – fewer requests reach the servers.  
2. **Reduced latency** – responses are delivered faster since they come from the cache.

---

## Compression
Compression reduces the size of responses **before sending them to clients**.

- Currently, only **gzip compression** is supported.
- The response is compressed by the load balancer before delivery.

### Benefits of Compression
1. **Lower bandwidth usage** – smaller response sizes.  
2. **Faster transmission speed** – quicker delivery to clients.  

---

## Acceleration
- **Acceleration** = Binding a **Web Application Acceleration Policy** to a **Load Balancer**.  
- Policies may include **caching** or a combination of **caching + compression**.  
- Once bound, the load balancer applies the policy to incoming requests.

---

## Cache Purge
- **Cache Purge** = Removing cached content from the load balancer.  
- After purge, requests are served **from backend servers** instead of cache.  
- **Irreversible action** – once purged, cached data cannot be restored.  

---

## Considerations for Caching & Compression
- Only **HTTP 200 responses** are cached.  
- Works only for **GET** and **HEAD** requests.  
- Maximum cache size: **100 MB**.  
  - Least frequently used resources are removed first.  
- Default cache duration: **10 minutes** (configurable).  

### Guidelines
- **Static content** → Cache for longer periods.  
- **Dynamic content** → Cache for shorter periods (or avoid caching).  
- Responses with `Set-Cookie` headers are **not cached**.  
- Avoid caching sensitive or dynamic pages (e.g., OAuth states, secrets).  

---

## Key Outcomes of Web Application Acceleration
- **Caching** → Reduces backend bytes sent (fewer requests hit backend).  
- **Compression** → Reduces bytes received by client and bytes sent by load balancer.  
- Combined effect → **Lower latency, reduced server load, improved client experience**.  

---

## Summary
- **Caching** improves latency and reduces backend load.  
- **Compression** reduces bandwidth usage and speeds up responses.  
- **Policies** define whether caching or compression (or both) are applied.  
- **Accelerations** bind these policies to specific load balancers.  
- Proper configuration helps optimize performance and reduce latency.  
