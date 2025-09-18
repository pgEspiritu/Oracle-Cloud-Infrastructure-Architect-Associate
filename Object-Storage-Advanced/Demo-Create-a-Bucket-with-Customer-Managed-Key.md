# 🔐 OCI Object Storage – Buckets with Customer-Managed Keys  

Hello and welcome. In this demonstration, I will show you how you can create a bucket with **customer-managed keys** (CMKs).  

---

## 📌 Default Behavior
- By default, **Object Storage** encrypts all data using **Oracle-managed keys**.  
- You can change this to **customer-managed keys**, meaning you’ll use keys stored inside **OCI Vault**.  

---

## 📝 Updating an Existing Bucket
- Go to your bucket.  
- Under **Encryption Key**, you’ll see **Oracle-managed key** by default.  
- Click **Assign**, then specify a **Vault** and a **Master Encryption Key**.  

---

## 👤 Required IAM Policy
Here’s the sample policy created for the **storage admin** group (for demo purposes, but ideally handled by security admins):  

```text
Allow group storage-admins to manage vaults in tenancy
Allow group storage-admins to manage keys in tenancy
```

Additionally, to let Object Storage service use keys:

```text
Allow service objectstorage-us-phoenix-1 to use keys in tenancy
```

## 🏗️ Steps to Create Vault & Key

1. Create a Vault
  - Navigate to Vaults → Create Vault.
  - Provide a name (optionally make it a virtual private vault).
2. Create a Master Encryption Key
  - Inside the vault → Create Key.
  - Protection Mode: Software (or HSM).
  - Algorithm: AES with desired key length.
  - Example: Name → demokey.
3. Enable Policy for Object Storage Service
  - Add policy:
    ```text
    Allow service objectstorage-us-phoenix-1 to use keys in tenancy
    ```

---

## 🔑 Assigning the Customer-Managed Key
- Go to Object Storage → Bucket.
- Under Encryption Key, click Assign.
- Select the Vault → choose the Master Encryption Key (demokey).

---

## ❓ Why Use Customer-Managed Keys?
 - 🔄 Control over lifecycle – rotate keys on demand.
 - 🛡️ Compliance & security – enhanced governance.
 - 🔍 Audit & transparency – full visibility into key usage.

---

## ✅ Final Policies Recap
```text
Allow group storage-admins to manage vaults in tenancy
Allow group storage-admins to manage keys in tenancy
Allow service objectstorage-us-phoenix-1 to use keys in tenancy
Allow service objectstorage-us-phoenix-1 to encrypt and decrypt objects in tenancy
```

🎯 That’s it! We have successfully created a bucket with Customer-Managed Keys (CMKs) in OCI Object Storage.
