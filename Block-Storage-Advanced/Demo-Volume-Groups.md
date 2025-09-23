# 🛠️ Demonstration: Creating a Volume Group in OCI

## 🎬 Introduction
In this demo, we’ll walk through the **creation of a Volume Group** in OCI using both block and boot volumes.

---

## 📦 Existing Setup
- **Block Volumes**:  
  - blockvolume-1  
  - blockvolume-2  
  - blockvolume-3  
- **Boot Volumes**:  
  - 2 boot volumes (in Availability Domain 1)  

Both **boot** and **block volumes** exist in the **same Availability Domain (AD-1)**.

---

## 📝 Steps to Create a Volume Group
1. **Navigate to Block Storage → Volume Groups**  
   - Click **Create Volume Group**  

2. **Provide Details**  
   - Name: `OCI Architect Associate Volume Group Demo`  
   - Select **Compartment**  
   - Select **Availability Domain** → `AD-1`  

3. **Add Volumes**  
   - Select **blockvolume-1**  
   - Select **blockvolume-2**  
   - Select **blockvolume-3**  
   - Select **Boot Volume 1 & Boot Volume 2**  
   ✅ Total: 5 volumes selected  

4. **Replication (Optional)**  
   - Cross-region replication option available  
   - For this demo: ❌ Not enabled  

5. **Backup Policy (Optional)**  
   - Assign a backup policy if required  
   - For this demo: Skipped  

6. **Review & Create**  
   - Review summary  
   - Click **Create**  

---

## 📊 Result
- **Volume Group created successfully**  
- Under **Resources**, you can view:  
  - Block Volumes: `blockvolume-1, blockvolume-2, blockvolume-3`  
  - Boot Volumes: `Boot Volume 1, Boot Volume 2`  

---

## ⚠️ Important Note
- A **volume can belong to only one volume group**.  
  - Example: Creating another group (`secondvg`) → previously selected volumes are **not available**.  

---

## ⚡ Additional Options
From the **ellipsis menu** on a volume group:  
- ➕ Create **Volume Group Backup**  
- ➕ Create **Volume Group Clone**  

---

## ✅ Summary
- Created a **volume group** with block + boot volumes.  
- Verified **single membership restriction** (one volume can’t belong to multiple groups).  
- Demonstrated available operations: **backup & clone**.  
