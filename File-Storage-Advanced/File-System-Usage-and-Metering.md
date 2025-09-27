# 📊 Lesson: File System Usage and Metering

## ⏱️ Metered File System Utilization
- The File Storage Service reports **metered file system utilization**, updated **hourly**.  
- This utilization comes from the **metered bytes** value in the APA.  
- When files are added or removed, it may take **up to 1 hour** for changes to appear.  

---

## 📂 Viewing Usage from an Instance
- OCI File Storage supports the **Network File System (NFS) protocol**.  
- You can check usage with:  
  - `df` → Reports **metered file system size** (matches metered bytes).  
  - `du` → Reports storage used by a **directory hierarchy**.  

⚠️ Note: `du` can show **larger values** than metered bytes, but `df` aligns with the metered value.

---

## 📸 Snapshot Metered Utilization
- A **snapshot** is a point-in-time view of your file system.  
- Initially, snapshots **consume no additional storage**, since they reference existing data.  
- The **metered size of a snapshot** is included in the **metered bytes** of its parent file system.  

### Example:
1. Create a file system `Testfilesystem`.  
   - Add `file1` = **1 GB**.  
   - After update → **Metered bytes = 1 GB**.  
2. Create a snapshot.  
   - No differentiated data yet.  
   - After update → **Metered bytes = 1 GB**.  
3. Overwrite first **0.5 GB** of `file1`.  
   - Differentiated data = **0.5 GB**.  
   - New total = **1.5 GB** (1 GB from snapshot + 0.5 GB changes).  

---

## 🪞 Clone Metered Utilization
- A **clone** references its parent file system’s data, so its **initial cost is metadata only**.  
- **Parent file system** is metered for data shared with clones.  
- **Clone** is metered for:  
  - Metadata  
  - Incremental changes made to its data  

### Example:
1. Clone `Testfilesystem` → `testclone`.  
   - At creation:  
     - Parent (`Testfilesystem`) = metered for its **data + metadata**  
     - Clone (`testclone`) = metered for **metadata only**  
2. Add **2 GB file** in `testclone`:  
   - Parent = still metered for shared data  
   - Clone = metadata + **2 GB of new data**  

---

## ✅ Summary
- **Metered utilization updates hourly**.  
- `df` = accurate metered size, `du` = directory usage (can be higher).  
- **Snapshots** don’t initially add cost, but differentiated data increases usage.  
- **Clones** start with metadata only but are metered for any new changes.  
