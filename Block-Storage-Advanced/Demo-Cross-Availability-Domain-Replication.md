# Demonstration: Enabling Cross-Availability Domain Replication

## Steps

### 1️⃣ Log in to OCI Console
- 👤 Log in using the **Storage Admin User**.
- 🍔 Click on the **Hamburger Menu** → **Storage** → **Block Storage** → **Block Volumes**.

---

### 2️⃣ Create a Block Volume
- 📝 Provide a name: `testvolume`.  
- 📂 Select the **associate compartment**.  
- 🗂️ Choose **Availability Domain 1** (out of three available domains).  
- ⚡ Keep **volume size and performance** as default.  
- 🔄 Backup policy: **none selected**.  

---

### 3️⃣ Enable Cross-AD Replication
- 🌍 Under replication settings, enable **cross-region replication**.  
  - Note: although labeled *cross-region replication*, here it’s being used for **cross-availability domain replication**.  
- 📍 Source Region: **US East (Ashburn)**.  
- 🏷️ Select **Availability Domain 2** as the replication target.  
- ✏️ Provide replica name: `testvolumereplica`.  
- ✅ Leave other options as default.  
- 🚀 Click **Create Block Volume**.

---

### 4️⃣ Verify the Block Volume
- ⏳ The block volume is **provisioned**.  
- 📦 Under **Block Volumes**, `testvolume` is **available**.  
- 🔁 Replication status shows **ON** → this indicates **cross-AD replication**.

---

### 5️⃣ Check the Block Volume Replica
- 📑 Navigate to **Block Storage → Block Volume Replicas**.  
- 👀 Confirm that `testvolumereplica` exists.  
- 🔎 Details show **source volume** and **source region**.

---

### 6️⃣ Activate the Replica
- ⚙️ Go to **Block Volume Replicas → testvolumereplica**.  
- ▶️ Click **Activate**.  
- 🛠️ Provide a name: `testvolumeactivatedreplica`.  
- ⚠️ Note: Initial sync may cause a **delay**.  
- ✅ Click **Activate Replica**.  

---

### 7️⃣ Confirm Activation
- 📂 Go to **Block Storage → Block Volumes**.  
- 🔄 You will see the new volume **provisioning**.  
- ✔️ Once complete, the new block volume is **available**.  
