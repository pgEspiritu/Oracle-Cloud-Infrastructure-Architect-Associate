# 📦 OCI Lesson – Block Volume Backups

## 🔹 What are Block Volume Backups?
- A **point-in-time snapshot** of Block Volume data.  
- **Encrypted** and stored in **OCI Object Storage**.  
- Can be **restored as new volumes** to any Availability Domain (AD) within the same region.  
- Provides **disaster recovery** capability across ADs.  
- Source **volume stacks** are automatically included in the backup.  

---

## 🔹 Architecture Example
1. Block Volume created in **AD1** and attached to an instance.  
2. Backup stored in **Object Storage**.  
3. Backup can be restored to **AD2** and attached to a different instance.  

---

## 🔹 Backup & Restoration Features
- **Cross-Region Copy**: Backups can be copied between regions for region-wide disaster recovery.  
- **Resized Volume Rule**: First backup after resize is always a **full backup**.  
- Can create a backup when volume is **attached** or **detached**.  

---

## 🔹 Backup Initiation Methods
### 1. **Manual Backup**
- On-demand, one-off backup.  
- Can choose **Incremental** or **Full**.  

### 2. **Policy-Based Backup**
- Automated based on a defined schedule.  
- **Oracle-Defined Policies**: Predefined, cannot be modified.  
- **User-Defined Policies**: Fully customizable schedules & retention.  

---

## 🔹 Backup Types
- **Full**: Includes all changes since the volume was created.  
- **Incremental**: Includes only changes since the last backup.  
  - Note: The **first incremental backup** is effectively a full backup.  

---

## 🔹 Oracle-Defined Backup Policies
1. **Bronze**
   - Monthly incremental → Retained **12 months**.  
   - Yearly incremental (January) → Retained **5 years**.  

2. **Silver**
   - Includes Bronze.  
   - **Weekly incremental (Sunday)** → Retained **4 weeks**.  

3. **Gold**
   - Includes Bronze + Silver.  
   - **Daily incremental** → Retained **7 days**.  

---

## 🔹 User-Defined Backup Policies
- Consist of:  
  - **Policy** → Defines scope & behavior.  
  - **Schedules** → Frequency (**daily, weekly, monthly, yearly**).  
  - **Retention Period** → Keep backups for **days, weeks, months, or years**.  
- Can enable **scheduled cross-region automated backups**.  

---

## ✅ Key Takeaways
- Block Volume backups ensure **data durability** and **DR readiness**.  
- Two types: **Full** and **Incremental**.  
- Backups can be **manual** or **policy-based**.  
- Oracle provides **Bronze, Silver, Gold policies**, or you can define **custom policies**.  
- **Cross-region backups** protect against regional outages.  

---
📌 **This concludes the lesson on Block Volume Backups.**
