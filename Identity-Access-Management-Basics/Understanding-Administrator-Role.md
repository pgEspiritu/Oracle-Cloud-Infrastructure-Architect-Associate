# Understanding Administrator Roles in OCI IAM

## 🧑‍💼 What Is a Domain Administrator?

When you create an identity domain in OCI, a **domain admin** is also created. This admin is essentially a **superuser** for your domain and holds all superuser privileges. This includes the ability to manage:

- Users and Groups
- Applications
- System Configuration
- Security Settings
- Audit and Notification Actions

---

## 🎯 Why Delegate Admin Roles?

As a domain admin, you may want to **share responsibilities**. For example:

- Allow another user to manage users or groups
- Assign a dedicated user to handle security configurations

To support this, OCI provides **predefined administrator roles** that can be assigned without writing complex policies.

---

## 🔐 Predefined Administrator Roles and Their Permissions

| Role | Description |
|------|-------------|
| **Identity Domain Administrator** | Full access to all domain capabilities and can delegate roles to others |
| **Security Administrator** | Manages system/security settings, password/sign-in policies, MFA, identity providers |
| **Application Administrator** | Manages applications and access for users/groups |
| **User Administrator** | Manages users, groups, and memberships (create, delete, update) |
| **User Manager** | More limited than User Admin; can be scoped to specific users/groups and handle updates, activations, password resets |
| **Help-Desk Administrator** | Supports users by unlocking accounts, resetting passwords, managing auth factors |
| **Audit Administrator** | Can generate/run audit reports to monitor activities in the domain |

---

## 🔄 Domain vs. Compartment Permissions

- These roles **apply only within the identity domain**.
- They do **not extend to OCI compartments**, making them different from IAM policies.

---

## ✅ Key Benefits of Using Administrator Roles

- **Simplified Management**: No need for complex policy definitions
- **Scoped Access**: Roles are relevant and limited to the identity domain context
- **Ease of Delegation**: Tasks can be delegated without deep IAM knowledge
- **Aligned with Cloud Security Best Practices**: Improves security and operational efficiency

---

## 🧾 Conclusion

Administrator roles in OCI IAM provide an effective method for managing and delegating responsibilities within your domain. They simplify access management and follow cloud security best practices.
