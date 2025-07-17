# OCI IAM Identity Domain

It covers what an identity domain is and its core capabilities.

---

## 🧠 What is an Identity Domain?

An **Identity Domain** in OCI represents a user population and their associated configurations and security settings. Think of it as a **self-contained IAM service** that acts as a **container** for:

- Managing users, groups, and dynamic groups  
- Assigning roles  
- Federating users  
- Provisioning users from other directories

### Core Features:

- Secure app integration through **SSO (Single Sign-On)**
- Support for **SAML** and **OAuth** protocols
- **Multifactor Authentication (MFA)** and **adaptive security**
- Integration with external directories using:
  - **AD Bridge** (for Active Directory)
  - **Provisioning Bridge** (for other directories)
- Support for **PAM and RADIUS Proxy**
- Configuration for apps that don’t support SAML/OAuth
- Like any OCI resource, domains support **policy scoping** in compartments

---

## 💼 Use Cases for Identity Domains

Here are some common scenarios where Identity Domains are useful:

### 🧑‍💼 Employee Access Management
Create a domain to manage employee identities across on-prem and cloud apps. Simplifies authentication and enables unified access control.

### 🤝 Partner/Business Vendor Access
Set up a separate domain for business partners needing access to supply chain or ordering systems. Keeps them isolated from internal users.

### 🌐 Consumer Access for Public Apps
Use an identity domain to manage consumer identities and their access to public-facing applications.

---

## ⚙️ Identity Store & Lifecycle Management

Identity domains offer:

- Onboarding via **Console**, **API**, or **CLI**
- Self-service registration
- Automated account provisioning
- Account synchronization between **cloud** and **on-premises** apps

Supports:

- External directory integration (e.g., **Microsoft Active Directory**)
- Delegated authentication between **AD** and **IAM**
- Adding applications from:
  - **Application Catalog** (400+ preconfigured templates)
  - Standard protocols (SAML, OpenID Connect)
  - **Proxy Gateways** and **Bridges** for SaaS, PaaS, and enterprise apps

---

## 🔐 Enhanced Security Features

You can enable:

- **Single Sign-On (SSO)**
- **Multifactor Authentication (MFA)** using:
  - Email
  - Mobile passcodes
  - Security questions
  - Passwordless options
- **Adaptive Security Controls**

---

## 🔑 Core Capabilities of OCI IAM with Identity Domain

### 1. Inbound Authentication & SSO
- Authenticates users accessing OCI
- Supports:
  - Social logins
  - Federated logins (e.g., from Active Directory)
  - Delegated authentication using **AD Bridge**
  - MFA and adaptive security

### 2. Identity Store & Lifecycle Management
- Onboard users from various systems via:
  - **AD Bridge**
  - **Provisioning Bridge**
  - **Console, CLI, or API**
- Manage:
  - User roles & group memberships
  - Permissions
  - Provisioning/de-provisioning
  - Sync and policy automation

### 3. Outbound Authentication & SSO
- Enables SSO for target applications like:
  - SaaS apps
  - Enterprise apps
  - Linux hosts
  - VPN clients

### 4. OCI Authorization with Access Policies
- Control access to OCI resources like:
  - Compute
  - Storage
  - Networking
- Managed via **IAM Policies**

---

## ✅ Summary

To wrap up:

- An **Identity Domain** is a **logical container** in OCI for managing:
  - Users
  - Roles
  - Security settings
  - Application integrations
- It supports different **authentication**, **authorization**, and **security configurations** tailored to various organizational needs.
- The **4 core capabilities** are:
  1. Inbound Authentication & SSO  
  2. Identity Lifecycle Management  
  3. Outbound Authentication & SSO  
  4. OCI Access Policies
