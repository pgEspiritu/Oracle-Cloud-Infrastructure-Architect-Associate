# Lesson: Managing Users in OCI IAM

Welcome to this lesson on managing users in **OCI IAM (Oracle Cloud Infrastructure Identity and Access Management)**. In this lesson, you'll learn about:

- The **user lifecycle stages**
- Who can **create and manage users**
- Various **methods for onboarding users**

---

## 1. User Lifecycle Stages

1. **Non-Existent**
   - The user profile does not exist yet.
   
2. **Created**
   - User account is created.
   - Can be kept in a **deactivated** state if the start date is in the future.

3. **Activated**
   - User has **active access** to OCI resources based on assigned groups and permissions.
   - Permissions or groups can be modified.
   - Admin roles can be assigned or removed.

4. **Deactivated**
   - Used for temporarily disabling access (e.g., sabbatical leave).
   - User cannot sign in or access resources.
   - Can be reactivated when needed.

5. **Deleted**
   - Final stage when a user retires or leaves the company.
   - The account is deleted and all access (groups, roles, applications) is revoked.

---

## 2. Who Can Manage Users?

- **Tenancy Admin**
  - Has permission to manage all resources across the tenancy, including users, groups, and identity components.

- **Domain Admin**
  - Part of the domain admin group.
  - Manages users and groups within a specific domain.
  - Can assign admin roles (e.g., *User Manager*) to other users.

- **Custom Policy-Based Access**
  - Permissions can be assigned via **IAM Policies**.
  - Example:
    ```text
    Allow group <group-name> to manage users in tenancy
    ```
  - This grants group members user management permissions for the entire tenancy.

> ⚠️ Policy syntax and structure will be covered in a future lesson.

---

## 3. Methods for Onboarding Users

- **OCI Console / API**
  - Quick way to manually create users.

- **CSV Import**
  - Ideal for bulk onboarding of users and groups.

- **IAM Self-Registration**
  - Allows **consumer users** to self-register.

- **Automation from External Sources**
  - Use various options depending on the system:
    - **App Catalog Integration** (e.g., Oracle HCM)
    - **Directories** like:
      - Oracle Unified Directory (OUD)
      - Oracle Internet Directory (OID)
    - **SCIM APIs** (for automated lifecycle management)
    - **Active Directory Bridge** (sync with on-prem AD)
    - **Provisioning Bridge** (local provisioning agent)

- **Federation (Just-In-Time Provisioning)**
  - User profiles are created automatically at first login via identity federation.

---

## ✅ Summary

- Learned about the **user lifecycle** in OCI IAM.
- Understood **who can manage users** based on roles and policies.
- Explored **multiple user onboarding methods**, from manual to automated provisioning.
