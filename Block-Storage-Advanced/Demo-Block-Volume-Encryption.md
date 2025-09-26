# Demonstration: Encrypting Block Volumes with Customer-Managed Keys

## Steps

### 1️⃣ Check the Existing Block Volume
- 📦 Block volume created: **`blockvolume-encryptiondemo`**.  
- 🔑 Encryption key: **Oracle-managed by default**.  
- 🛠️ Goal: Assign a **customer-managed master encryption key**.

---

### 2️⃣ Create an OCI Vault
- 🍔 Navigate: **Hamburger Menu → Identity & Security → Vault**.  
- 🗄️ Click **Create Vault**.  
- 📝 Provide a name (not a virtual private vault).  
- ✅ Click **Create Vault**.

---

### 3️⃣ Configure IAM Policy
- 📜 Add a policy in **IAM** to authorize **Block Storage** service to use keys in the compartment:  
```text
Allow service blockstorage to use keys in compartment <compartment_name>
```


---

### 4️⃣ Create Keys in the Vault
- 🔑 Inside the vault → click **Create Key**.  

1. **Key 1 (Valid)**  
 - Name: `demokey`  
 - Algorithm: **AES**  
 - Status: **Enabled**  

2. **Key 2 (Invalid for Block Storage)**  
 - Name: `testkey`  
 - Algorithm: **RSA**  
 - Status: **Enabled**

---

### 5️⃣ Assign Keys to the Block Volume
- 📂 Go back to **Block Storage → blockvolume-encryptiondemo**.  
- ⚙️ Under **Encryption Key** → click **Assign**.  
- 🔎 Select the vault and key:  

- ❌ If you choose `testkey (RSA)`:  
  - You get an **error** → RSA keys are **not supported** for encrypting volumes.  

- ✅ If you choose `demokey (AES)`:  
  - Encryption is successfully applied.  
  - The block volume is now encrypted with a **customer-managed key**.

---

### 6️⃣ Optional Features
- 🔒 **In-Transit Encryption**:  
- When attaching the volume to an instance (**Attach → Paravirtualized → Select Instance**),  
- You can enable **in-transit encryption**.

- ⚠️ **Cross-Region Replication Restriction**:  
- If you try enabling **cross-region replication** on a volume using a **customer-managed key**,  
- ❌ You get an error:  
  > "You cannot enable cross-region replication for a volume as this volume is using a vault encryption key."

---

## Conclusion
🎉 You have successfully encrypted a block volume using a **customer-managed AES key** in OCI.  
- ✅ RSA keys are **not supported**.  
- ✅ In-transit encryption is available.  
- ⚠️ Cross-region replication is **not supported** with vault encryption keys.  
