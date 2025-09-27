# Demonstration: Encrypting File Systems with Customer-Managed Keys


## Step 1: Check Current Encryption
- Inside the **OCI Console**, logged in as `storageadmin`.  
- Selected file system → **demofs**.  
- Under **File System Information**, encryption key = **Oracle-managed key**.  

---

## Step 2: Prepare Customer Vault and Keys
- Created a vault → **demovault**.  
- Inside the vault:  
  - `testkey` → **RSA algorithm** ❌ (not supported for file system encryption).  
  - `demokey` → **AES algorithm** ✅ (supported).  

⚡ **Note:** Only **AES (symmetric keys)** are supported for file system encryption.

---

## Step 3: Switch to Customer-Managed Key
1. Return to **File Systems** → **File System Information**.  
2. Under **Encryption Key**, click **Edit**.  
3. Select → **Encrypt Using Customer-Managed Keys**.  
4. Provide:  
   - Vault Compartment → *demovault*  
   - Master Encryption Key → *demokey* (AES)  
5. Save changes.  

➡️ Result: File system now uses **demokey** (customer-managed key).  

---

## Step 4: Add Required IAM Policy
To allow encryption with customer-managed keys, you must add a **policy**.  

Example policy statement:

```hcl
Allow service FssOcN to use keys in tenancy
```
- `N` → Realm number (depends on your region, e.g., `oc1`).
- The File Storage Service user pattern is:
```nginx
FssOcN
```
- Without this policy, encryption with customer-managed keys will not work.
