# HTTP Redirects in OCI DNS

## Overview
The **DNS Service** in OCI supports **HTTP redirects**, allowing you to forward traffic from one domain or subdomain to another URL.  

---

## Scenarios for HTTP Redirects

1. **Redirect an entire domain**  
   - Example: Redirect all traffic from `test.net` → `test.com`.

2. **Redirect a specific subdomain**  
   - Example: Redirect `blog.test.net` → `http://news.test.com`.

3. **Redirect a subdomain to a URL with a port number**  
   - Example: Redirect `example.test.net` → `http://sample.test.net:8080`.

4. **Permanent redirect (301)**  
   - Example: If a domain is deprecated, redirect it permanently to a new domain.  
   - Informs **search engines and browsers** to update their references.

---

## How It Works
- When creating an HTTP redirect:
  - **Specify**:
    - Zone (domain/subdomain to redirect)
    - Target (protocol, host, optional port, path, query)
  - **Choose Response Code**:
    - `301` → Moved Permanently
    - `302` → Temporary Redirect

---

## DNS Record Requirement
- After creating an HTTP redirect, you must add a **CNAME record** in the DNS zone for it to function.  
- Example:
  ```dns
  example.test.net.   CNAME   sample.test.net.
  ```

---

## Benefits
- Simplifies domain management when owning multiple domains.
- Handles subdomain-level redirects easily.
- Properly informs clients and search engines about permanent or temporary changes.
