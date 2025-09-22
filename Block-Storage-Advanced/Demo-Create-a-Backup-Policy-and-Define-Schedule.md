# 📦 OCI Demonstration – Creating a Backup Policy and Defining Schedules

### 1. Apply an **Oracle-Defined Policy**
1. Navigate to **Block Volumes** in the OCI Console.  
2. Select a block volume (e.g., **OCI Demo Block Volume**).  
3. Click **Edit** → scroll down to **Backup Policy**.  
4. Choose one of the **Oracle-defined backup policies**:  
   - **Gold**  
     - Daily incremental @ midnight → retained **7 days**  
     - Weekly incremental @ midnight Sunday → retained **4 weeks**  
     - Monthly incremental @ midnight, 1st → retained **12 months**  
     - Yearly full @ midnight, Jan 1 → retained **5 years**  
   - **Silver** – Excludes daily incremental backups.  
   - **Bronze** – Includes only monthly + yearly backups.  
5. Save changes → view the **scheduled backups** and next 3 backup dates.  

---

### 2. Create a **Custom Backup Policy**
1. Navigate to **Block Storage → Backup Policies**.  
2. Click **Create Backup Policy**.  
   - Enter a name (e.g., `Custom Backup Policy`).  
   - Select a compartment.  
   - (Optional) Enable **Cross Region Copy Target** → choose a region (e.g., Ashburn).  
   - Confirm **Enable Copying** → click **Create Backup Policy**.  

---

### 3. Add a Schedule to the Custom Policy
1. Inside the newly created policy → click **Add Schedule**.  
2. Configure schedule details:  
   - **Frequency** → Daily, Weekly, Monthly, or Yearly.  
   - **Start Time** → Select the hour of the day.  
   - **Retention** → Define duration (e.g., 7 days, 4 weeks, 12 months, etc.).  
   - **Backup Type** → Incremental or Full.  
3. Example schedules:  
   - **Daily** → Incremental, 7-day retention.  
   - **Weekly (Monday)** → Incremental, 4-week retention.  
   - **Monthly (1st)** → Full, 12-month retention.  

---

### 4. Attach Custom Policy to a Volume
1. Go back to **Block Volumes**.  
2. Select the target block volume.  
3. Click **Edit** → select **Custom Backup Policy**.  
4. Enable **Scheduled Volume Backup Copies** (if cross-region enabled).  
5. Save changes.  

---

## ✅ Key Notes
- Oracle-defined policies (Gold, Silver, Bronze) are **pre-configured** and cannot be modified.  
- Custom policies allow **full flexibility** in schedules, backup type, retention, and cross-region replication.  
- Backups are always stored in **OCI Object Storage**.  
- First backup in any schedule is always a **Full backup**, subsequent ones can be incremental.  
