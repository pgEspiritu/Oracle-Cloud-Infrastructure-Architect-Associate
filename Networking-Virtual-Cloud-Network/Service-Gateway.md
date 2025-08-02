# Lesson: Service Gateway

## What is a Service Gateway?

To understand the Service Gateway, let’s first discuss a construct known as the **Oracle Services Network (OSN)**.

### Oracle Services Network (OSN)
- The OSN is reserved for **Oracle services**.
- These services typically have **public IP addresses**.
- When you access Oracle services, communication usually happens **over the internet**.

---

## The Role of the Service Gateway

With a **Service Gateway**, **cloud resources without public IP addresses** (i.e., with only private IPs) can **still access Oracle services**—**privately**.

### Key Benefits:
- Enables **private access** to Oracle services.
- Traffic **does not traverse the internet**.
- Communication happens over **Oracle's network fabric**.

This is important for **data security**, as private communication ensures that traffic isn’t exposed over the internet.

---

## Services CIDR Level

### What is Services CIDR Level?
- A **string** that represents **all regional public IP address ranges** of Oracle services.
- Two options to route traffic to Oracle services:
  1. **Manual entry** of public IP address ranges (not recommended).
  2. **Use of services CIDR string** (recommended).

### Why Use Services CIDR Level?
- Public IP ranges of Oracle services can **change**.
- Manual updates to:
  - **Route tables**
  - **Security rules**
  - Can be error-prone and require maintenance.

Using the **services CIDR level string** simplifies the configuration and removes the need to manually update values.

### Example:
For **Object Storage in OCI Phoenix**, the services CIDR string might look like:
```text
oci-phx-objectstorage
```

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
