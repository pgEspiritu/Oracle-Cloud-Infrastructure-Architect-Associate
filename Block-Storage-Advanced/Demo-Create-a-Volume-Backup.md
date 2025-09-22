# 📦 OCI Demonstration – Creating a Block Volume Backup

1. **Log in**  
   - Sign in to the **OCI Console** using a **Storage Admin user**.  
   - Navigate to **Block Volumes** → list of available volumes.  

2. **Select Volume**  
   - Identify the volume to back up.  
   - Click on the **ellipsis (⋮)** next to the volume.  
   - Choose **Create Manual Backup**.  

3. **Configure Backup**  
   - Enter a **name** for the backup (e.g., `BlockVolumeName_ManualBackup`).  
   - Choose **Backup Type**:  
     - **Full** – First backup is always full.  
     - **Incremental** – Captures changes since the last backup.  

4. **Create Backup**  
   - Click **Create Block Volume Backup**.  
   - Backup job begins → **Status: Creating**.  
   - After completion → **Status: Available**.  

---

## 🔹 Backup Details in Console
- **Backup Source** → Selected Block Volume.  
- **Backup Type** → Full (first time).  
- **Backup Size** and **Volume Size** shown.  
- Stored in **Object Storage**.  

---

## 🔹 Available Actions on Backup
From the **Block Volume Backups** page, click the ellipsis (⋮) to:  
- 📤 **Copy** → Replicate backup to another region.  
- ♻️ **Restore** → Create a new block volume from the backup.  
- 🔍 **View Details** → Inspect metadata and settings.  

---

## ✅ Key Notes
- First backup is always **Full**.  
- Subsequent backups can be **Incremental**.  
- Backups are always stored in **OCI Object Storage**.  
- Policies can be defined later for **automated scheduling**.  
