# OCI Identity and Access Management (IAM) - Lesson Summary

## 📌 What is OCI IAM?

OCI IAM is a **cloud-native service** in Oracle Cloud Infrastructure that manages:

- **Identities** (users, groups) – who can access
- **Access** (policies, permissions) – what they can access

It provides:
- Identity lifecycle management
- Fine-grained, role-based access control (RBAC)
- Integration with external identity providers

---

## 🔐 Identity vs. Access Management

### 🧍 Identity (Authentication / AuthN)

Ensures that only **verified identities** can access resources.

Authentication methods include:
- **Username/Password** or **passwordless authentication**
- **API Keys** – public/private key pair used in SDK/CLI
- **OAuth 2.0 Tokens** – for delegated access by applications
- **Instance Principals** – for compute instance access without credentials
- **Federated Identity** – using external IdPs with SAML 2.0
- **Multi-Factor Authentication (MFA)** – for enhanced security

### ✅ Access Management (Authorization / AuthZ)

Controls **what actions** authenticated identities can perform.

Authorization is managed through:
- **IAM Policies** written in a simple syntax
- Permissions assigned to **users**, **groups**, or **resources**
- **Example**:
  - User-A can start/stop/terminate compute instances
  - User-B can only read from object storage
  - User-C can manage databases

OCI IAM checks policies during every access attempt to allow or deny actions.

---

## 🧱 Core Components of OCI IAM

| Component           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **Identity Domain** | Logical container for users, groups, and apps (e.g., Dev, Prod environments)|
| **User**            | Represents a person or system that interacts with OCI                       |
| **Group**           | Collection of users with shared access policies                             |
| **Policy**          | Text-based rules that grant permissions to groups/users                     |
| **Compartment**     | Logical container to isolate OCI resources within a tenancy                 |

---

## 🛠️ OCI IAM in Practice

Typical setup steps:

1. **Create Identity Domain**
2. **Create Users and Groups** within the domain
3. **Write IAM Policies** to define permissions
4. **Assign Policies** to compartments or tenancy
5. **Control Resources** using access rules

Example IAM policy scope:
- Tenancy-wide
- Specific compartments

---

## 🧾 Summary

- **Authentication** (AuthN): Verifies the identity (who).
- **Authorization** (AuthZ): Controls access using policies (what).
- OCI IAM provides secure, role-based access to cloud resources.
- Key components: identity domains, users, groups, compartments, policies.
- Each component will be explored in detail in future lessons.

