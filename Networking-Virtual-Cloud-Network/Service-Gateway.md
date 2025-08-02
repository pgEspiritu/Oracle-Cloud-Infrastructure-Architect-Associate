
---

## Best Practice: Use Service Gateway for Private Access

Rather than using the internet to reach Oracle Services, use **Service Gateway**:
- Ensures **secure, private traffic** routing.
- Traffic travels only via Oracle’s internal network infrastructure.

---

## Why It Matters

- You **don’t need public IP addresses** on instances.
- You **don’t need Internet Gateway** or **NAT Gateway**.
- Just the **Service Gateway** is enough for private access.

---

## Architecture Example

### Scenario:
- Instances are deployed in a **private subnet** (no public IP).
- They need access to **Object Storage (OSN service)**.

### Configuration:
- A **Service Gateway** is deployed.
- The **Route Table** is updated accordingly:
  - For **internet access**, the next hop is the **NAT Gateway**.
  - For **Object Storage access**, the next hop is the **Service Gateway**.

#### Route Table Entry:
| Destination CIDR        | Target          |
|-------------------------|-----------------|
| `oci-phx-objectstorage` | Service Gateway |

> ⚠️ Instead of using IP ranges like `0.0.0.0/0`, use the **services CIDR level string** for Oracle Services.

---

## Final Notes

- **Service Gateway is regional**.
- It enables access to **supported Oracle services within the same region**.
- Promotes secure and private networking within Oracle Cloud Infrastructure (OCI).
