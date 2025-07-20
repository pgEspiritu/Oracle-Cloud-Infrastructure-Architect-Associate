# 👥 Managing Groups in OCI Identity Domains

This lesson covers:
- What groups are in IAM
- Why we need them
- Default groups in identity domains
- A preview of how to create groups in the OCI Console

---

## 🧩 What is a Group in IAM?

A **Group** is a collection of users with common roles, permissions, and access policies.

### ✅ Benefits of Using Groups:
- **Simplified access management**  
  Assign permissions to a group instead of managing them per user.
  
- **Improved security and compliance**  
  Easier to **audit and track** who has access to what.

### 📌 Example Use Cases:
- `NetworkAdmins` – for managing networks
- `ComputeOps` – for handling compute instances
- `CertManagers` – for managing certificates

---

## 🛠 How Groups Work in Identity Domains

After an identity domain is created, the **domain admin** can:
1. **Create groups** (e.g., Engineering, Marketing, Finance)
2. **Add users** to those groups based on their roles
3. **Attach policies** to define what each group can do

> Policies will be discussed in a separate lesson.

---

## 🏷️ Default Groups in Every Domain

OCI automatically creates **two default groups** in each identity domain:

### 1. 🔧 `Domain Administrators`
- Created when the domain is created
- Includes the **domain admin user** by default
- **Cannot be deleted**
- **Must contain at least one user**
- Users in this group have **full control** over the identity domain

### 2. 👤 `All Identity Domain Users`
- Includes **all newly created users by default**
- **Does not appear** in the Groups tab
- Can be assigned to applications (meaning all users can access the app)
- **Cannot be deleted**

---

## 🧾 Summary

| Group Name                | Created By | Editable | Notes                                                                 |
|--------------------------|------------|----------|-----------------------------------------------------------------------|
| `Domain Administrators`  | IAM        | ❌       | Full control over the domain; at least one user required              |
| `All Identity Domain Users` | IAM     | ❌       | All users belong to this by default; hidden from Groups tab          |
| Custom Groups (e.g., `Engineering`, `Finance`) | Admin | ✅ | Created as needed to align with organizational structure & access needs |

