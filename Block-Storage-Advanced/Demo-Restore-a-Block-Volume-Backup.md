# 📦 OCI Demonstration – Restoring a Block Volume Backup

### 1. Locate the Backup
1. Navigate to **Block Storage → Block Volume Backups** in the OCI Console.  
2. Find the **manual backup** created earlier (e.g., from `demo block volume`).  
   - Original source volume location: **Availability Domain 1 (AD-1)**.  
   - Backups are always stored in **OCI Object Storage**.  

---

### 2. Start the Restore Process
1. Click the **ellipsis (…) → Restore Block Volume**.  
2. Provide details for the new volume:  
   - **Name** → e.g., `restored-demo-block-volume`.  
   - **Compartment** → choose the target compartment.  
   - **Availability Domain** → you can select a **different AD** (e.g., restore to **AD-2**).  

---

### 3. Configure Restore Options
- **Volume Size**  
  - Must be **greater than or equal to** the backup’s size.  
  - Example: Original size = **1,024 GB (1 TB)** → Restored as **2,048 GB (2 TB)**.  
  - ❌ Cannot shrink the size (e.g., 512 GB is invalid).  
- **Performance Level**  
  - Select desired performance (Balanced, Higher Performance, etc.).  
  - Example: Restored with **Higher Performance**.  

---

### 4. Complete the Restoration
1. Click **Restore Block Volume**.  
2. Monitor status → initially shows **In Progress**.  
3. Once completed, check **Block Volumes** list:  
   - New volume → `restored-demo-block-volume`.  
   - Size = **2 TB**.  
   - Performance = **Higher Performance**.  
   - Availability Domain = **AD-2**.  

---

## ✅ Key Notes
- Restoring from backup allows:  
  - Choosing a **different availability domain**.  
  - **Increasing** the volume size (not decreasing).  
  - Adjusting **performance levels**.  
- Restored volumes behave like normal block volumes and can be **attached to instances**.  
- Backups remain stored in **Object Storage** for future restores.  
