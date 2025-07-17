# 📘 OCI Default Domain Overview

When you create an OCI **tenancy**, a **default identity domain** is automatically created.

---

## 🔐 What is an Identity Domain?
An identity domain is a container used to:
- Manage **users** and their **roles**
- Enable **federation** and **user provisioning**
- Ensure secure application integration via **SSO**, **SAML**, or **OAuth**

---

## 🗂 Location and Characteristics
- Created in the **root compartment** of the tenancy
- Used for users, groups, or apps **within the root compartment**
- **Cannot be deactivated or deleted**
- **Cannot be hidden** from the Sign-In page
- **Replicates** to all subscribed OCI regions

---

## 👤 Default Domain Contents
- **1 user** (admin/super user)
- **2 groups**:
  - `Domain Users`
  - `Administrators`
- **Admin group**:
  - Cannot be deleted
  - Must always have **at least one user**
  - Granted **full access** to all OCI resources via a **default policy**
  - The policy **cannot be modified or deleted**

---

## 🧑‍💼 Admin User Responsibilities
- Initial **IAM user** for tenancy
- Sets up **additional administrators**
- **Key responsibilities**:
  - Assign/manage roles
  - Configure system and security settings
  - Perform **delegated administration** (e.g., domain/security administrator)
  - Enable and manage **multi-factor authentication (MFA)**
  - Create and manage **self-registration profiles**
  - Handle policy and application **approvals**

---

## ❗ Do's and Don'ts for Admin Users
### ✅ Do:
- Assign **specific roles** for tasks
- Use **delegated administration**
- Create **separate IAM users** with least-privilege permissions
- Use **multiple identity domains** for better isolation and control

### ❌ Don’t:
- Add unnecessary users to the **Admin group**
- Use admin/super user accounts for **routine tasks**

---

## 🧾 Summary
- The **default domain** is foundational in OCI.
- It ensures initial access control but has limitations.
- For better security and manageability, leverage **multiple identity domains** and **role-based access control**.
