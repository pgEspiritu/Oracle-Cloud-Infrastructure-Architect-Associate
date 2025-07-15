# 🔐 OCI IAM - Identity Domain

Welcome to this lesson on **OCI Identity and Access Management (IAM)** focused on **Identity Domains**. In this module, we'll explore what identity domains are, how they function, their capabilities, and use cases.

---

## 📌 What is an Identity Domain?

An **Identity Domain** in OCI is a **self-contained IAM environment** that represents a user population along with its associated **security settings, configurations, roles, and policies**.

Think of it as a **container** that allows you to:
- Manage **users**, **groups**, and **dynamic groups**
- Integrate with **external directories** (e.g., Active Directory)
- Enable **Single Sign-On (SSO)** and authentication using **OAuth** or **SAML**
- Define **identity lifecycle processes**
- Isolate access management for different environments, apps, or users

Each identity domain is an OCI **resource**—this means it can be managed through policies, compartments, and OCI tenancy.

---

## 🧰 Core Capabilities of Identity Domains

OCI IAM with Identity Domains provides four **key capabilities**:

### 1. ✅ Inbound Authentication and SSO

This handles **how users log in** to OCI or associated applications. Features include:
- **Username/password** or **passwordless logins**
- **Social login** (e.g., Google, Facebook)
- **Federated login** with external identity providers (e.g., Azure AD) via **SAML 2.0**
- **Delegated Authentication** using **AD Bridge** (Active Directory)
- **Multi-Factor Authentication (MFA)** and **Adaptive Security** for enhanced login protection

> 💡 *Example: Enable MFA for admin users accessing sensitive applications.*

---

### 2. 📦 Identity Store and Lifecycle Management

This capability allows you to manage **user provisioning, roles, and groups** within your identity domain:

- Onboard users via:
  - **OCI Console**
  - **Command Line Interface (CLI)**
  - **REST APIs**
- Use **AD Bridge** or **Provisioning Bridge** to import users from:
  - Microsoft Active Directory
  - Other on-prem or cloud directories
- Features include:
  - **Self-service registration**
  - **Automated account provisioning**
  - **Synchronization** of user data between OCI and external systems
  - **Application catalog** with 400+ preconfigured templates for apps

> 🔄 *Supports provisioning, de-provisioning, and role assignments for users and apps.*

---

### 3. 🔄 Outbound Authentication and SSO

Once users are authenticated, Identity Domains allow **Single Sign-On** to **external or internal applications**, such as:

- SaaS applications (e.g., Salesforce, Office 365)
- Enterprise tools
- Linux hosts
- VPN clients
- Custom web apps

> 🌐 *Enable seamless login to multiple systems without repeated credential prompts.*

---

### 4. 🔐 OCI Authorization Using IAM Policies

This is where **IAM Policies** control access to OCI resources like:
- Compute
- Block/Object Storage
- Networking
- Databases

Policies are written in a **simple syntax** and can be scoped to:
- **Compartments** (logical OCI containers)
- **Tenancy** (entire OCI environment)

> 📝 *Example policy:*
```text
Allow group DevTeam to manage compute-instances in compartment Development
```

## 🧪 Use Cases for Identity Domains

Here are some common scenarios where **Identity Domains** are useful:

### 🧑‍💼 Employee Access Management
- Create a domain to manage employee identities across **on-premises and cloud applications**.
- Simplifies **authentication** and enables **unified access control**.

### 🤝 Partner / Business Vendor Access
- Set up a **separate domain** for business partners who need access to systems such as **supply chain** or **ordering platforms**.
- Keeps vendor users **isolated from internal employee accounts** and policies.

### 🌐 Consumer Access for Public Apps
- Use an identity domain to manage **consumer logins** for **public-facing web applications**.
- Configure unique **multi-factor authentication (MFA)** and **security settings** for end users.

### 🏢 Directory Integration (AD or LDAP)
Integrate OCI IAM with your enterprise directory:
- Use **AD Bridge** for synchronizing users and groups from Microsoft Active Directory.
- Enable **Delegated Authentication** for secure sign-ins, without migrating credentials to the cloud.

### 🛡️ Security Controls
Identity domains support:
- **SSO** using protocols like **SAML**, **OAuth**, and **OpenID Connect**.
- **Adaptive Security** that applies context-aware policies (e.g., location, device).
- **Multi-Factor Authentication (MFA)** options:
  - One-time passcodes (OTP)
  - Security questions
  - Device trust
  - Email verification codes
- Support for **passwordless authentication** for enhanced usability and security.

---

## 🗂️ Identity Domain as a Resource

Identity Domains are **first-class OCI resources**, which means:
- They can be **created, modified, and deleted** like any OCI resource.
- **Access control** is handled through **IAM policies**.
- Domains can be **scoped to compartments**, allowing for **organizational segregation**.

> 🏢 This supports **multi-tenancy** within a single OCI tenancy—useful for large organizations with diverse teams and security needs.

---

## 🧾 Summary

| **Capability**                  | **Description**                                                       |
|----------------------------------|------------------------------------------------------------------------|
| **Inbound Authentication & SSO** | Authenticate users via multiple secure methods and protocols           |
| **Identity Lifecycle Management**| Manage user provisioning, synchronization, and self-service            |
| **Outbound Authentication & SSO**| Provide seamless access to internal/external apps                      |
| **Authorization (IAM Policies)** | Define and enforce fine-grained access control                         |

### 🔑 Key Takeaways

- An **Identity Domain** is a **logical IAM boundary** in OCI for managing identities, roles, and policies.
- You can create **multiple identity domains** for different:
  - Business units
  - Customer groups
  - Environments (Dev, Test, Prod)
- Each domain supports:
  - Separate **authentication methods**
  - Customized **access policies**
  - Integration with **external directories**
  - Features like **SSO**, **MFA**, and **federated login**

---

## 🚀 What’s Next?

In the next lessons, we will:
- ✅ Create and configure an **Identity Domain**
- 👥 Add **users and groups**
- 🔐 Set up **authentication methods and federation**
- 📜 Apply **IAM policies** for secure OCI resource access

