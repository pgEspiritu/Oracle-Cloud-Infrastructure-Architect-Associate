# 🔐 OCI Object Storage – Re-Encryption of Buckets & Objects  


## 📦 1. Re-Encrypting a Bucket
- The bucket is encrypted using a **Customer-Managed Key (CMK)**.  
- Click on **Re-encrypt** under the bucket’s encryption settings.  
- OCI generates a **Work Request** to re-encrypt all **Data Encryption Keys (DEKs)** using the **latest version** of the Master Encryption Key (MEK).  
- Once complete, the bucket and its contents are protected with the updated key.  

---

## 📄 2. Re-Encrypting an Object – Oracle-Managed Keys
When a bucket is encrypted with **Oracle-Managed Keys**:  
- Select an object → **Re-encrypt**.  
- Two options appear:  
  1. **Use the Key Assigned to the Bucket** → re-encrypts with the latest Oracle-managed key.  
  2. **Use a Customer-Managed Key** → re-encrypts with a CMK from OCI Vault (e.g., `demokey2`).  

👉 This allows migration of an object from Oracle-managed encryption to customer-managed encryption.  

---

## 📄 3. Re-Encrypting an Object – Customer-Managed Keys
When a bucket is encrypted with a **Customer-Managed Key (CMK)**:  
- Select an object → **Re-encrypt**.  
- Two options appear:  
  1. **Use the Key Assigned to the Bucket** → re-encrypts with the **latest version** of the current CMK.  
  2. **Use a Different Customer-Managed Key** → re-encrypts the object with another CMK from the vault.  

📌 Example:  
- Inside the vault, rotate the key `demokey`.  
- Rotation generates a **new key version**.  
- When re-encrypting, you can use this updated version or select another CMK entirely.  

---

## ✅ Key Takeaways
- 🔄 **Bucket Re-encryption** refreshes DEKs using the latest MEK version.  
- 📑 **Object Re-encryption** depends on bucket encryption type:  
  - Oracle-managed → latest Oracle key or migrate to CMK.  
  - Customer-managed → latest CMK version or switch to another CMK.  
- 🔐 Key **rotation** enables stronger security by updating encryption without recreating data.

