# Identity Domain Types in OCI

A high-level overview of different **Identity Domain Types** in Oracle Cloud Infrastructure (OCI), their features, and their limitations.

> 📌 **Note:** Always refer to the [official OCI documentation](https://docs.oracle.com/en-us/iaas/Content/Identity/home.htm) for the most up-to-date details.

---

## 🆓 1. Free Domain Type (Default Identity Domain)
- **Included** by default when an OCI account is created.
- **Purpose:** Manage access to OCI resources.
- **Authentication Methods:** Supported.
- **Limitations:**
  - Maximum **2,000 users**.
  - Not suitable for **enterprise-level** access management.
- **Use Case:** Best for basic access needs without additional integrations.

---

## 🟠 2. Oracle Apps Domain Type
- **Tied to Oracle services** such as SaaS, PaaS, GBU applications, and VBCs.
- **Creation:** Not user-selectable via console; comes bundled with services.
- **Features:** 
  - Can support hybrid IAM (e.g., proxies, gateways, bridges).
  - Integrates with **OCI-hosted** or **on-premises** Oracle apps (e.g., E-Business, PeopleSoft).
  - Allows addition of **up to 6 non-Oracle apps**.

---

## 🟢 3. Premium Domain Type
- **Fully featured**, enterprise-grade domain type.
- **High Limits:** For users, groups, applications.
- **Use Case:** Suitable for large organizations and hybrid scenarios.
- **Features:**
  - Full support for **hybrid IAM** environments.
  - Can manage both **on-premises** and **cloud-based** identities.
  - Acts as the primary **Identity and Access Management (IAM)** provider.

---

## 🔵 4. External User Domain Type
- **Target Users:** Non-employees (e.g., contractors, consumers).
- **Use Case:** Ideal for public-facing apps with high user scale.
- **Features:**
  - Social login support.
  - Self-service capabilities.
  - Password management.
  - Hybrid features supported.

---

## 🔚 Summary
- OCI accounts come with a **Free Default Domain**.
- Upgrade to **Premium** or **External User** domain types for:
  - Higher user limits.
  - Advanced integrations.
  - Enterprise or consumer scenarios.
- Always review the official documentation for limits and capabilities per domain type.

---

**Happy Learning!**
