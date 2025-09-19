# 💽 OCI Block Volume Creation Demonstration  

## 🖥️ Steps to Create a Block Volume  

### 1️⃣ Navigate to Block Storage  
- Log in to the **OCI Console** as a **Storage Admin user**.  
- Click on the **hamburger menu** → **Storage** → **Block Storage**.  

---

### 2️⃣ Create Block Volume  
- Click **Create Block Volume**.  
- Provide a **name** → `OCI demo block volume`.  
- Select the **compartment** → *Architect Associate*.  
- Choose an **Availability Domain (AD)**.  

---

### 3️⃣ Configure Size & Performance  
- **Default**: ~1 TB volume, **Balanced** performance.  
- **Custom Options**:  
  - 📏 Size → **50 GB – 32 TB**  
  - ⚡ Performance Tiers →  
    - 🟢 **Lower Cost**  
    - 🟡 **Balanced**  
    - 🔴 **Higher Performance**  
    - 🔵 **Ultra High Performance**  
- Demo choice → **2 TB** with **Balanced tier**.  

---

### 4️⃣ Backup Policies (Optional)  
- **Oracle-defined**: 🥇 Gold | 🥈 Silver | 🥉 Bronze  
- **Custom** policies available  
- Demo choice → **No backup policy enabled**  

---

### 5️⃣ Cross-Region Replication (Optional)  
- Can enable to replicate volume **asynchronously** to another region.  
- Requires selecting:  
  - Target Region 🌍  
  - Availability Domain 🏢  
  - Replicated volume name 🏷️  
- Demo choice → **Not enabled**  

---

### 6️⃣ Encryption  
- Default: **Oracle-managed keys 🔑**  
- Option: Use **Customer-managed keys**  
- Demo choice → **Oracle-managed keys**  

---

### 7️⃣ Create  
- Click **Create Block Volume** ✅  
- Volume is created and becomes **Available**.  

---

## 📊 Information After Creation  
- **Availability Domain** → AD1  
- **Size** → 2 TB  
- **Performance Tier** → Balanced  
- **Scheduled Backups** → None  
- **Cross-Region Replication** → Disabled  

---

## ✅ Key Takeaways  
- Block Volumes can be **customized** in size and performance.  
- Backup policies & cross-region replication are optional but useful for resilience.  
- Encryption is enabled by default with Oracle-managed keys.  
- Once created, volumes can be attached to compute instances (covered in upcoming demonstrations).  
