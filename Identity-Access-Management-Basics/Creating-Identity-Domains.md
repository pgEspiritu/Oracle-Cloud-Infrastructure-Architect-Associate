# 🏗️ Creating Identity Domains in OCI

This lesson explains **why** and **how** to create multiple identity domains in OCI, even when a default domain exists.

---

## ❓ Why Create Multiple Identity Domains?

### 1. 🔐 **Isolation of Administrative Control**
- Enables **separation** between departments, teams, or environments (e.g., Production vs Development).
- Prevents **unauthorized access** and interference.
- Provides **compartmentalized identity** management.

### 2. 🛡️ **Security & Compliance**
- Each domain can have **custom access policies**, **security settings**, and **compliance rules**.
- Example: Production users may have stricter policies than Development users.

### 3. 🧩 **Simplified Identity Management**
- Helps structure and organize identities.
- Easier to manage users and apps in **large-scale organizations**.
- Analogy: Like organizing files into folders.

### 4. 🎛️ **Granular Administrative Control**
- Each domain can have its own **admin** or set of **domain-specific roles**:
  - **Domain Administrator**
  - **Security Administrator**
  - **Application Administrator**

---

## 🧑‍💼 What Happens When You Create an Identity Domain?

- OCI creates:
  - A **default administrator group**
  - An **admin user** (Domain Administrator)
- This admin can:
  - Manage **users, groups, applications**
  - Assign other **admin roles**
  - Configure **MFA, password, and sign-in policies**
  - Create **self-registration profiles** (for consumer user groups)

---

## 🌍 Domain Home Region

- The **region selected during domain creation** becomes the **home region**.
- Example: If selected region is `US East (Ashburn)`, the domain's home region is **Ashburn**.
- ⚠️ **Important:**
  - **Unlike the default domain**, **additional identity domains are NOT auto-replicated** across all subscribed regions.
  - To allow users to access OCI resources in **other regions**, you must **manually enable replication**.

---

## 🧾 Summary

- Multiple identity domains provide:
  - Better **administrative isolation**
  - Enhanced **security and compliance**
  - Structured **identity management**
  - Role-based **delegation of responsibilities**
- When creating domains, remember:
  - A new admin user and group is created.
  - Set the correct **home region**.
  - **Manually enable replication** if cross-region access is needed.
