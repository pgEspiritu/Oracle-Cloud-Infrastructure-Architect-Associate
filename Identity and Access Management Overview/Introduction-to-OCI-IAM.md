# 🔐 OCI Identity and Access Management (IAM)

**Core Concepts Covered:**

- Authentication and Authorization
- Identity domains
- Compartments
- Users, Groups, and Policies
- Role-Based Access Control (RBAC)

---

## 📘 What is OCI IAM?

**OCI IAM** is a **cloud-native identity and access management service** in Oracle Cloud Infrastructure. It enables you to:

- Manage **identities** (users, groups, federated identities)
- Control **access** to OCI resources through **policies**
- Securely **authenticate and authorize** users, applications, and services

OCI IAM consists of two main functions:

### 1. Identity (Authentication)
Ensures that the **right person or system** is attempting to access OCI resources. It supports:
- Inbound authentication (users/applications accessing OCI)
- Outbound authentication (OCI services accessing other services)
- Single Sign-On (SSO)

OCI IAM supports **integration with external identity stores**, such as:
- Microsoft Active Directory
- Identity Providers (IdPs) via **SAML 2.0**
- Third-party apps and custom solutions

### 2. Access Management (Authorization)
Defines **what actions** authenticated entities can perform using **IAM policies**.

This is where **Role-Based Access Control (RBAC)** comes in:
- Define **fine-grained permissions** per user/group/service
- Grant only the required privileges (least privilege principle)
- Apply policies at **tenancy or compartment level**

---

## 🔑 Authentication in OCI (AuthN)

**Authentication** is the process of verifying who the user or system is.

OCI IAM supports multiple authentication methods:

- **Username and Password**: Traditional login credentials.
- **Passwordless Authentication**: Using methods such as device trust or biometrics.
- **API Signing Keys**: Public/private key pair used for SDK and CLI access.
- **OAuth 2.0 Tokens**: Allows delegated access to OCI resources via applications.
- **Instance Principals**: Allows a compute instance to access OCI services **without credentials**.
- **Federated Identity**: Enables access using external IdPs (e.g., Azure AD, Okta) via **SAML 2.0**.
- **Multi-Factor Authentication (MFA)**: Adds a second layer of authentication using OTP or authentication apps.

These authentication methods are part of **identity lifecycle management**, which includes provisioning, updating, and deleting user accounts.

---

## 🛂 Authorization in OCI (AuthZ)

**Authorization** is the process of determining what an authenticated user is allowed to do.

OCI IAM uses **policies** written in a simple, readable syntax:
`Allow group <group-name> to <verb> <resource-type> in <compartment-name>`


### Example Scenario:
- **User-A** can start, stop, and terminate **compute instances**
- **User-B** can only **read object storage buckets**
- **User-C** has full **management access to databases**

When any of these users attempt an action:
- IAM checks the **associated policy**
- If permitted, the action proceeds
- If not permitted, access is **denied**

This process ensures **secure and auditable access** to all OCI services.

---

## 🧱 Key Components of OCI IAM

| Component           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **Identity Domain** | Logical container for managing **users, groups, apps, and authentication methods**. Great for separating environments like dev, test, prod. |
| **User**            | Represents a human or application identity that can access OCI resources.   |
| **Group**           | A collection of users with **shared policies**. Policies are assigned to groups, not individual users. |
| **Policy**          | A document that specifies **who can do what** on which resources.           |
| **Compartment**     | Logical container that helps **isolate and organize** OCI resources. Policies can be scoped to compartments. |

---

## ⚙️ Typical IAM Workflow

1. **Create Identity Domain**: Establish separate environments for managing identities.
2. **Create Users and Groups**: Assign users to groups with similar access needs.
3. **Write and Apply Policies**: Define access control using human-readable rules.
4. **Assign Scope**: Policies can apply to an entire **tenancy** or a specific **compartment**.
5. **Deploy Resources**: All OCI resources reside in compartments with controlled access.

This structure enables **modular, secure, and scalable access control** for cloud deployments.

---

## 🧾 Summary

- **OCI IAM** provides robust **identity and access management** for Oracle Cloud users.
- **Authentication (AuthN)**: Confirms who is accessing OCI using credentials or tokens.
- **Authorization (AuthZ)**: Defines what the authenticated entity can do via policies.
- Core components include:
  - **Identity Domains** – for organizing identities and apps
  - **Users and Groups** – for assigning roles and permissions
  - **Compartments** – for organizing OCI resources
  - **Policies** – for implementing RBAC

