# 🔗 OCI Local VCN Peering – Part 2

## 1. Local VCN Peering Using Local Peering Gateways (LPG)

### Architecture
- **Two VCNs in the same region** (e.g., `VCN1` and `VCN2`).
- **Requirement 1:** Non-overlapping CIDR blocks.
  - Example:
    - `VCN1`: `10.0.0.0/16`
    - `VCN2`: `192.168.0.0/16`
- **Requirement 2:** One **Local Peering Gateway** per VCN.
  - `LPG1` on `VCN1`
  - `LPG2` on `VCN2`
- **Requirement 3:** Establish a **connection** between `LPG1` and `LPG2`.

---

### Additional Configuration
1. **Route Tables**
   - Add route rules so each VCN knows how to reach the other.
   - Example:
     - In `VCN1` Route Table:
       - **Destination:** `192.168.0.0/16` (VCN2 CIDR)
       - **Target:** `LPG1`
     - In `VCN2` Route Table:
       - **Destination:** `10.0.0.0/16` (VCN1 CIDR)
       - **Target:** `LPG2`
2. **Security Rules**
   - Configure **Security Lists** or **Network Security Groups (NSGs)** to allow required traffic.

---

## 2. Local VCN Peering Using Upgraded Dynamic Routing Gateway (DRG v2)

### Architecture
- **Two VCNs in the same region** (e.g., `VCN1` and `VCN2`).
- **Requirement 1:** Non-overlapping CIDR blocks.
  - Example:
    - `VCN1`: `10.0.0.0/16`
    - `VCN2`: `192.168.0.0/16`
- **Requirement 2:** **One** Dynamic Routing Gateway.
  - Attach **the same DRG** to both `VCN1` and `VCN2`.

---

### Additional Configuration
1. **Route Tables**
   - In `VCN1` Route Table:
     - **Destination:** `192.168.0.0/16` (VCN2 CIDR)
     - **Target:** DRG
   - In `VCN2` Route Table:
     - **Destination:** `10.0.0.0/16` (VCN1 CIDR)
     - **Target:** DRG
2. **Security Rules**
   - Allow required private traffic between the two VCNs.

---

## 3. Without Peering
If peering is **not** configured:
- Communication between VCNs requires:
  - **Internet Gateway** in each VCN.
  - **Public IP addresses** on instances.

---

## 4. Internet Gateway Considerations in Peering
- **Scenario:** Two VCNs peered via LPG, `VCN2` has an Internet Gateway, `VCN1` does not.
- **Result:**
  - Instances in `VCN1` **cannot** send outbound traffic to the internet via `VCN2`’s Internet Gateway.
  - However, they **can receive inbound traffic** from the internet via `VCN2` (if allowed by routing & security rules).

---

## 5. Summary Table

| Method | Gateways Needed | CIDR Requirement | Routing | Pros | Cons |
|--------|----------------|------------------|---------|------|------|
| **LPG** | 2 LPGs (1 per VCN) | Non-overlapping | Manual route rules & security rules | High bandwidth, low latency | Limited to 10 LPGs/VCN |
| **DRG v2** | 1 DRG (shared) | Non-overlapping | Manual route rules & security rules | Flexible routing (300 VCNs/DRG) | Slightly higher latency than LPG |

---

✅ **Key Takeaway:**  
- Use **LPG** when you need **ultra-low latency** between a small number of VCNs.  
- Use **DRG v2** when you need **scalability** and **flexible routing** across many VCNs.
