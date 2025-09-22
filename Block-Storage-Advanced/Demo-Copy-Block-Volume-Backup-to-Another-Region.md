# 🌍 OCI Demonstration – Copying Block Volume Backup to Another Region & Restoring

### 1. Copy Backup to Another Region
1. Navigate to **Block Volume Backups** in the source region (**Phoenix**).  
2. Locate the desired manual backup.  
3. Click **ellipsis (…) → Copy to Another Region**.  
4. Provide details:  
   - **Name** → `demo-block-volume-backup-copy`.  
   - **Destination Region** → e.g., **Mumbai**.  
5. Confirm → The system begins copying the backup to the **target region**.  

---

### 2. Monitor Copy Operation
- Copy status can only be monitored in the **destination region**.  
- Switch to **Mumbai** region:  
  - The copy operation status → **In Progress**.  
  - Initially, no block volumes exist in the region.  
  - Wait until the backup state changes to **Available**.  

---

### 3. Restore the Backup in Destination Region
1. From **Mumbai** region → locate the copied backup.  
2. Click **Restore Block Volume** and provide details:  
   - **Name** → e.g., `restored-demo-block-volume`.  
   - **Compartment** → select target compartment.  
   - **Volume Size** → can be **increased** (e.g., set to **2 TB**).  
   - **Performance Tier** → set to **Higher Performance**.  
   - (Optional) **Enable Cross Region Replication**.  
   - (Optional) **Apply Backup Policy**.  
3. Click **Restore Block Volume**.  

---

### 4. Validate the Restored Volume
- Navigate to **Block Volumes** in **Mumbai** region.  
- Confirm:  
  - New block volume is **provisioned** from the copied backup.  
  - Volume attributes match chosen configuration (e.g., 2 TB, Higher Performance).  
- The copied backup remains in **Block Volume Backups**, and can be further copied to **other regions** if needed.  

---

## ✅ Key Notes
- Backups can be **copied across regions** for disaster recovery or migration purposes.  
- Restored volumes can be **resized** (larger only), tuned for **performance tiers**, and **attached** to instances in the destination region.  
- Backup copies remain independent and can be reused for multiple restores or further cross-region copies.  
