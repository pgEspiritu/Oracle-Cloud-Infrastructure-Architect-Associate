# 📦 OCI Lesson – Resizing a Volume

## 🔄 Online Resizing
- Expand an **existing volume in place** without detaching from an instance.  
- **Increase only** → You cannot decrease a volume size.  
- After resizing, the **first backup** taken will be a **full backup**.  
- **Preferred method** to avoid workload disruption.  
- If **Cross-Region Replication** is enabled:  
  1. Disable replication before resizing.  
  2. Resize volume.  
  3. Re-enable replication afterward.  

### ⚙️ Example
- Initial size: **1,024 GB**  
- Can be expanded up to **32 TB**  
- Cannot shrink (e.g., ❌ 512 GB).  

### 📌 Post-Resize Requirement
- Extend the partition to use the new size.  
- If volume is attached:  
  - Run **rescan commands**.  
  - Then extend partitions manually.  

---

## 📴 Offline Resizing Options
1. **Expand Detached Volume**  
   - Detach volume → Resize → Reattach.  
   - Only partition extension needed (no rescan).  

2. **Restore from Backup**  
   - Restore a backup into a **larger volume**.  

3. **Clone Volume**  
   - Create a **new, larger volume** by cloning an existing one.  

---

## ✅ Key Takeaways
- Volume size can only be **increased**, never decreased.  
- Choose **online resizing** for minimal downtime.  
- For offline methods, detach, restore, or clone depending on the use case.  
