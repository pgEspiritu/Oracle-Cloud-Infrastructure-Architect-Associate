# Public DNS Zones

## What is a Public DNS Zone?
A **public DNS zone** is used to resolve hostnames on the **internet**.  
- It hosts **trusted DNS records** (e.g., A, AAAA, MX, CNAME).  
- Records are stored on **OCI nameservers**.  
- Public DNS zones make domains **accessible from the internet**.  

---

## Steps to Implement a Public DNS Zone

### 1. Create a Public DNS Zone
- When you create a zone in OCI:
  - A **Nameserver (NS) record** is automatically generated.  
  - A **Start of Authority (SOA) record** is automatically generated.  
- Example:  
  If your domain is `samvit.site`, create a public zone named `samvit.site`.

---

### 2. Delegate the Zone
Delegating makes the zone accessible on the internet.

- Copy the **NS records** created during step 1.  
- Update them in your **domain registrar’s DNS panel** (e.g., GoDaddy).  
- This replaces the registrar’s default nameservers with OCI’s nameservers.  
- Without delegation, the zone will not be publicly accessible.  

**Example Flow:**
1. Buy a domain (e.g., `samvit.site`) from a registrar like GoDaddy.  
2. Create a **Public DNS Zone** in OCI with the same name (`samvit.site`).  
3. Copy OCI’s **NS records** into GoDaddy’s DNS management panel.  

---

### 3. Add Records to the Zone
Once the zone is delegated, you can add DNS records.  
Each record contains **record data** depending on its type:  

- **A Record** → IPv4 address (e.g., `192.0.2.1`)  
- **AAAA Record** → IPv6 address  
- **MX Record** → Mail server for the domain  
- **CNAME Record** → Alias to another domain  

---

## Example: Setting Up a Public DNS Zone
1. Purchase a domain: `abc.com`  
2. Create a public zone in OCI named `abc.com`.  
3. Delegate the zone by updating registrar NS records with OCI NS records.  
4. Add DNS records (e.g., `A`, `MX`, `CNAME`) to the zone.  

---

## Summary
- **Public DNS Zones** resolve hostnames on the internet.  
- They host **trusted records** stored on **OCI nameservers**.  
- Setup involves 3 steps:  
  1. **Create** the zone (NS + SOA auto-generated).  
  2. **Delegate** the zone at the domain registrar.  
  3. **Add records** to the zone.  
