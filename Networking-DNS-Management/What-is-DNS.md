# DNS Overview

## What is DNS?
The **Domain Name System (DNS)** plays an important role on the internet. Its main functionality is to translate human-friendly **domain names** into **IP addresses** that machines understand.

- **Analogy**: Just like saving a phone number under a contact name in your phone, DNS maps a **domain name** to a numerical **IP address**.
- Example: `www.oracle.com` → `IP address`

---

## How DNS Works
When you visit a website (e.g., `www.example.com`):

1. **Browser Request**
   - Your computer sends a query to the DNS server.
   
2. **Recursive DNS Server**
   - The recursive DNS server queries other servers to find the IP address.

3. **Root Servers**
   - The recursive DNS server first asks the **root servers** (`.`) where to find the `.com` domain.

4. **Top-Level Domain (TLD) Servers**
   - The root server responds with information about the **TLD server** for `.com`.
   - The recursive DNS server then asks the `.com` TLD servers for `www.example.com`.

5. **Authoritative DNS Server**
   - The TLD server points the query to the **authoritative DNS server** for `example.com`.
   - The authoritative server returns the actual **IP address**.

6. **Response**
   - The recursive DNS server returns the IP address to your browser.
   - The browser can now connect to the web server and display the website.

---

## Types of DNS Servers
- **Recursive (Non-Authoritative)**  
  Performs lookups by querying multiple servers until it finds the IP address.  

- **Authoritative**  
  Holds the actual DNS records for a domain and provides the final answer.

---

## DNS in Oracle Cloud Infrastructure (OCI)
Oracle Cloud Infrastructure (OCI) provides a managed DNS service that allows you to:

- Create and manage **DNS zones** (e.g., `PublicZone` with records like **NS** and **SOA**).
- Add and update **DNS records** within zones.
- Import zone files in **BIND format** (industry standard).
- Use OCI’s **edge network** to handle domain queries.

### Benefits of OCI Public DNS
- **Low Query Latency**: Queries are served via anycast from OCI’s global regions.
- **Built-in DDoS Protection**: Resilient against outages and attacks.
- **High Availability**: Designed for fault tolerance.
- **Fast Propagation**: Industry-leading propagation time for DNS changes.

---

## Summary
- DNS translates **domain names** into **IP addresses**.
- Uses a hierarchy: **Root → TLD → Authoritative servers**.
- OCI DNS provides **fast, secure, and reliable DNS management** for enterprises.
