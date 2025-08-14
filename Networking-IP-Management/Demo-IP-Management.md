# 🖥️ Demo - IP Management

## 1. Compute Instance and VNIC Overview
- Navigate to **Compute → Instances**.
- Select your instance (e.g., `OCI-AA`).
- Under **Primary VNIC**:
  - You can see the **Public IPv4 address** and **Private IPv4 address**.
  - Click **Attached VNICs** → view **Primary VNIC details**.
- Under **Resources → IPv4 Addresses**:
  - Primary private IP is displayed.
  - Option to **assign secondary private IPs**:
    - Can specify manually or let OCI assign automatically.
  - Map private IPs to public IPs if needed.

---

## 2. Secondary Private IP Assignment
- Click **Assign** under IPv4 Addresses.
- OCI creates a **Secondary Private IP**.
- Observe:
  - Primary IP → Ephemeral public IP (default)
  - Secondary IP → Public IP can be **ephemeral or reserved**

---

## 3. Creating a Reserved Public IP
1. Navigate to **Networking → IP Management → Reserved Public IP**.
2. Click **Reserve Public IP Address**:
   - Choose **IP address source**: Oracle
   - Enter a **name**
3. Reserved public IP is now available.

### Using Reserved Public IP:
- While creating resources like **NAT Gateway**:
  - Choose **Reserved Public IP Address**
  - Select existing reserved IP (e.g., `test reserved public IP`)
  - Complete resource creation

- Reserved IP states:
  - **Assigned** → Associated with a resource
  - **Available** → Not yet assigned

---

## 4. Bring Your Own IP (BYOIP)
1. Navigate to **IP Management → Import BYOIP CIDR Block/Prefix**
2. Provide:
   - Name
   - Compartment
   - IPv4/IPv6 CIDR block
3. OCI generates **Validation Token**:
   - Register token with your **Regional Internet Registry (RIR)**
4. Create **Route Origin Authorization (ROA)**:
   - Authorizes Oracle to advertise your CIDR block
   - Provide Oracle BGP ASN
5. Click **Finish Import** (after completing previous steps)
6. Advertise the CIDR ranges if required.

> Note: This step is essential to bring your own IP into OCI and manage it.

---

## 5. Public IP Pools
- Navigate to **IP Management → Public IP Pools → Create Public Pool**
- Only works after **BYOIP**:
  - Use portion or entire BYOIP CIDR block.
- Options for using public IP pool:
  1. **Reserve Public IP** → Attach to resources
  2. **Direct Launch from Pool** → Automatically allocate IP to resource
- If no CIDR block is associated yet → pool shows empty.

---

## 6. Key Notes
- Reserved public IPs:
  - Can be associated with VNIC or NAT Gateway.
  - Differentiated by **state**: Assigned vs Available.
- Public IP Pool becomes selectable as **IP Address Source** after BYOIP import.
- Demonstration covers:
  - Primary/Secondary VNICs
  - Ephemeral vs Reserved Public IP
  - BYOIP workflow
  - Public IP Pool creation

---

✅ **Conclusion:**  
You now know how to:
- Manage primary/secondary VNIC IPs
- Assign ephemeral or reserved public IPs
- Import your own IP addresses (BYOIP)
- Create and use Public IP Pools
