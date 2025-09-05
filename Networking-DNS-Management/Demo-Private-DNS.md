# Private DNS Zone Demonstration (OCI)

## Navigation
- Go to **OCI Console → Networking → DNS Management → Zones**.  
- You will see both **Public Zones** and **Private Zones**.  

---

## Automatic Private Views and Zones
- When you create a **VCN**, OCI automatically creates:
  - A **Private View**  
  - Default **Private Zones** associated with it  
- Example:  
  - `demovcn` → private view + zones  
  - `testvcn` → private view + zones  

---

## Default DNS Behavior in a VCN
- DNS type in DHCP Options: **Internet and VCN Resolver** (default).  
- Example domain structure:  
  - VCN: `testvcn.oraclevcn.com`  
  - Subnet: `publicsubnet.testvcn.oraclevcn.com`  
  - Instance: `instancea.publicsubnet.testvcn.oraclevcn.com`  

These FQDNs are long → motivates use of **Private DNS Zones**.

---

## Private DNS Resolver
- Handles DNS queries within a VCN using **views** and **zones**.  
- Resolver query order:
  1. Custom private views  
  2. Default private view  
  3. Rules  
  4. Internet DNS  

---

## Creating a Private Zone and View
1. Go to **DNS Management → Zones → Private Zones**.  
2. Create a zone (e.g., `samvit.com`).  
3. Create a private view (e.g., `samvitprivateview`).  
4. Associate the view with a resolver in your VCN.  
   - `Networking → VCN → DNS Resolver → Manage Private Views`  

Result:  
- Resolver → View (`samvitprivateview`) → Zone (`samvit.com`) → Records  

---

## Resolver Endpoints
- **Listener Endpoint** → Listens to queries from outside the VCN/OCI.  
- **Forwarder Endpoint** → Forwards queries to external/custom DNS servers.  
- Endpoints consume **private IPs** within the subnet.  

---

## Resolver Rules
- Up to **10 rules per resolver**.  
- Rules can define:
  - Condition  
  - Client  
  - Source endpoint  
  - Destination IP address  

---

## Cross-VCN Name Resolution
- By default, **VCN1 cannot resolve hostnames in VCN2**, even if peered.  
- Fix:  
  - In the resolver for VCN1, **add the private view from VCN2**.  
  - Now instances in VCN1 can resolve hostnames of VCN2 resources.  

---

## Key Takeaways
- Private DNS Zones are **automatically created** with each VCN.  
- You can create **custom private views** and associate them with resolvers.  
- Resolver checks: **Custom View → Default View → Rules → Internet DNS**.  
- **Endpoints** enable forwarding and listening across networks.  
- For **cross-VCN resolution**, associate views from one VCN to another.  
