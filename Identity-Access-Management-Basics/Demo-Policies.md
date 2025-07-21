# 🛡️ OCI Policy Demo: Granting Access to VCN

In this demo, we’ll:

- Learn how to write OCI policy statements
- Grant users access to OCI resources (specifically, the Virtual Cloud Network or VCN)

---

## 🔐 Login and Setup

1. **Logged in as:** Tenancy Admin (not Domain Admin)
2. **Domains:**
   - Default Domain (created with OCI account)
   - `production` domain (custom-created)
3. **Groups in `production`:**
   - `Network Admin`
   - `Vault Admin`
4. **Users added to groups** (e.g., `John Roos` is in `Network Admin`)

---

## ❌ Access Denied (Before Policy)

Logged in as `John Roos`:

- Navigated to **Networking → Virtual Cloud Network**
- Selected **Root Compartment**
- ❗ Got error: `Authorization Failed`

Tried **Storage → Bucket**:
- ❗ Got similar error: No authorization to perform request

💡 This confirms that **no permissions** are currently granted.

---

## 🛠️ Writing the Policy

Switched back to **admin account**:

### ➕ Create Policy

- **Name:** `Network Admin Policy`
- **Group:** `Network Admin`
- **Compartment:** `production`

### ✅ Using Policy Builder:

- **Use Case:** Network Management
- **Template:** Allow group to manage cloud networks
- **Domain:** `production`
- **Group:** `Network Admin`
- **Scope:** `production` compartment

📜 **Generated Policy Statement:**

```text
Allow group 'Production'/'NetworkAdmin' to manage virtual-network-family in compartment Production
```

✏️ You can edit this manually in the Manual Editor to add more statements if needed.

---

# 🔄 Verifying Access to OCI Resources

## 👤 Switched to John Roos Account
- ✅ Refreshed console
- ✅ Navigated to **Virtual Cloud Network**
- ✅ Now sees **production** compartment
- ✅ No error when accessing VCN in **production**
- ❌ Still **no access to root** (as expected)

---

## ➕ Created a VCN
- **Name:** `Demo`
- **Configuration:** All default values
- ✅ **Successfully created!**

---

## ✅ Summary
OCI **policies** define:

- **Who** (subject)  
- **What** (verb + resource)  
- **Where** (compartment)  

We granted `manage` access on `virtual-network-family` to the **Network Admin** group in the `production` compartment.

Access was verified by logging in as a user and confirming access to VCN resources.

---

## 📝 Policy Recap
```text
Allow group 'Production'/'NetworkAdmin' to manage virtual-network-family in compartment Production
```
