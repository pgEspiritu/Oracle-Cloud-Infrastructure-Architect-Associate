# 📂 Lesson: File System Replication in OCI

Replication enables **asynchronous data transfer** between a **source** file system and a **target** file system to ensure data protection and consistency.

---

## 🔑 Key Concepts

- **Source File System** 🟢  
  The file system whose data you want to replicate.  

- **Target File System** 🎯  
  The destination for replicated data.  
  ⚠️ Must be a file system that has **never been exported**.  

- **Replication Resource** ⚙️  
  - Control component of replication.  
  - Attached to the source file system.  
  - Captures updates via **replication snapshots** and transmits them.  

- **Replication Target Resource** 📥  
  - Resides in the destination region or availability domain.  
  - Applies data to the target file system.  
  - Created automatically when replication is configured.  
  - Can only be **deleted manually during failover**.  

- **Replication Snapshot** 📸  
  Captures incremental changes since the last snapshot.  
  Managed automatically by the service.  

- **Replication Interval** ⏱️  
  Defines replication frequency in minutes.  
  Must be **≥ 60 minutes**.  

---

## 🔄 Replication Workflow

1. **Base Copy** 🗂️  
   - Initial full transfer from source → target file system.  

2. **Delta Copy** ➕  
   - Subsequent transfers of incremental changes.  
   - Triggered at each **replication interval**.  

---

## 🔁 Delta Cycle States

1. **Idle** 😴 → No capturing or applying.  
2. **Capturing** 📝 → Differentiated data captured in source snapshot.  
3. **Transferring** 🚚 → Snapshot data is captured **and** committed.  
4. **Applying** 📤 → Snapshot data is written to the target file system.  

---

## ⚙️ Replication Process Overview

- Replication resource is created on the **source file system**.  
- It generates a **replication snapshot**.  
- Snapshot is sent to the **replication target resource**.  
- Data is applied to the **target file system**.  
- Snapshots remain until the **next interval**, then replaced automatically.  
- This process repeats at the specified interval until replication is stopped.  

---

## 🌍 Use Cases

### 🔐 Disaster Recovery  
- Provides protection from **regional outages**.  
- Supports **cross-region replication**.  
- Helps meet **data redundancy & compliance requirements**.  

**Example:**  
An Oracle E-Business Suite customer in **Phoenix** may replicate to another availability domain in **Aspen** for backup and recovery.  

---

## ✅ Summary
- Replication provides **asynchronous, consistent copies** of file systems.  
- Supports **cross-AD** and **cross-region** replication.  
- Ensures **business continuity, DR readiness, and compliance**.  
