# OCI IAM Demo: Assigning Administrator Roles

## 🔐 Initial Login as Regular User

I have logged in as one of the users we created in the previous demo. You will notice that this user does **not have access** to any cloud services or resources.

### ❌ Access Denied Examples:

- **VCN under Networking**  
  - Result: *Authorization failed* – no permission to perform any action.
- **Compute Instances**  
  - Result: Access denied.
- **Vault Service**  
  - Result: No access.
- **Identity Domain Capabilities**
  - Navigate to: `Domains > Production Domain > Users`
    - Result: Not allowed to perform any action.
  - Try accessing `Groups` or `Security`
    - Result: No permissions granted.

---

## ✅ Assigning Administrator Role

Now, let’s assign an **administrator role** to this user.

### Step-by-Step:

1. **Log out** from the current user.
2. **Log in** as the **Domain Admin**.
3. Navigate to:

```text
Domains > Production Domain > Security > Administrators
```


4. Select the role: **User Administrator**
- This role allows:
  - Managing users
  - Managing groups
  - Managing group membership

5. Click **Add User**
6. Select the user `Saurabh Patil`
7. Click **Add User** again to confirm

✅ Now, `Saurabh Patil` has been assigned the **User Administrator** role for the **Production Domain**.

---

## 🔍 Verifying Access After Role Assignment

Let’s go back and log in as `Saurabh Patil` to verify the access:

1. Go to: `Domains > Production Domain`
2. Click on:
- **Users** → Access granted
- **Groups** → Access granted
- **Group Memberships** → Can assign and revoke

❗ However, user still does **not** have access to:
- **Security**
- **Notifications**

This is because only the **User Administrator** role was assigned, and permissions are **limited to user/group management** only.

---

## 💡 Summary

With this quick demo, we have:

- Shown how a regular user initially had **no access** to services.
- Assigned the **User Administrator** role using the Console (no policies needed).
- Verified the **limited permissions** granted by the role.
- Explained that admin roles are **domain-scoped**.
