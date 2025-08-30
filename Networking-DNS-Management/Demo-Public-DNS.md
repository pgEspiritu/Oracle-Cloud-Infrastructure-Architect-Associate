# Demonstration: Creating and Managing a Public DNS Zone in OCI

## 1. Accessing DNS Zones in OCI
1. Log in to the **OCI Console**.  
2. Navigate to: **Menu → Networking → DNS Management → Zones**.  
   - Here you can view both **Public Zones** and **Private Zones**.  

---

## 2. Prerequisite: Domain Registration
- You must have a registered domain name (e.g., purchased from **BigRock**, **GoDaddy**, etc.).  
- Your domain registrar provides **default nameservers** (e.g., `dns1.bigrock.in`).  
- These will later be **replaced with OCI nameservers** during zone delegation.  

---

## 3. Creating a Public DNS Zone
1. In OCI Console, click **Create Zone**.  
2. Choose creation method:  
   - **Manual** (create records manually).  
   - **Import** (upload a valid BIND-format zone file).  
3. Select:  
   - **Zone Type** → `Primary`  
   - **Zone Name** → e.g., `samvit.site`  
4. Click **Create**.  

✅ The zone will be created and marked as **Active**.  
- Automatically generated records:  
  - **NS (Nameserver) Record**  
  - **SOA (Start of Authority) Record**  

---

## 4. (Optional) Downstream Servers
- For a **Primary Zone**, you can configure **secondary egress** to an external DNS provider.  
- Under **Manage Downstream Servers**, add the IP address of the external DNS server.  

*(This step is optional and not required for most setups.)*  

---

## 5. Delegating the Zone
Delegation makes the hosted zone accessible on the internet.

1. Copy the list of **OCI nameservers** generated when the zone was created.  
   - Example: `ns1.p68.dns.oraclecloud.net`  
2. Go to your **domain registrar’s DNS panel** (e.g., BigRock, GoDaddy).  
3. Replace the registrar’s default nameservers with the **OCI nameservers**.  
4. Save/Update settings.  

⏳ Note: Propagation usually takes **24–72 hours** to reflect globally.  

---

## 6. Adding DNS Records
1. In the zone view, click **Add Record**.  
2. Select record type (supported types include `A`, `AAAA`, `CNAME`, `MX`, `ALIAS`, etc.).  
3. Example: Add an **A Record**  
   - **Record Type** → `A`  
   - **TTL** → Time-to-live (in seconds)  
   - **Record Data** → Public IP address of your server/instance  
4. Click **Add Record**.  

👉 After adding records, click **Publish Changes** → **Confirm Publish Changes**.  

---

## Example: Adding an A Record
```text
Record Type: A
Name: (optional)
TTL: 3600
Record Data: 203.0.113.25   # Public IP of your instance
```

---

## 7. Summary
- Created a Public DNS Zone (samvit.site) in OCI.
- Delegated the zone by updating nameservers at the domain registrar.
- Added records (e.g., A record pointing to a public IP).
- Published changes to make DNS updates live.

🎉 Your domain is now managed by OCI DNS and accessible from the internet.
