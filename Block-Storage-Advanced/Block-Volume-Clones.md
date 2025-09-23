# 📦 OCI Lesson – Block Volume Clones

## 🎯 What are Block Volume Clones?
- Cloning allows you to **copy an existing block volume** without going through backup & restore.  
- A **clone** is a **point-in-time, direct disk-to-disk deep copy** of the source volume.  
- ✅ Data present at the time of cloning is copied.  
- ❌ Subsequent changes in the source volume are **not** reflected in the clone.  

---

## ⚡ Key Characteristics
- **Immediate Operation**: Clone creation is instant.  
- **Usage**: You can attach and use the clone as soon as its state becomes **Available**.  
- **Background Copying**: Data continues copying in the background (up to **30 minutes**, depending on volume size).  

---

## 🌍 Scope & Restrictions
- **Same Region & AD**: Clone must be created in the **same Availability Domain** as the source volume.  
  - Example: If the source is in **AD1, Phoenix**, the clone is also created in **AD1, Phoenix**.  
- **Tenant Restriction**: Must be in the **same tenancy**.  

---

## 🔄 Clone Limitations
- If **source volume is attached**:  
  - ✅ Only **one clone at a time** can be created.  
- If **source volume is detached**:  
  - ✅ Up to **10 clones simultaneously** can be created.  

---

## 📂 Volume & Group Cloning
- You can create clones of:  
  - 📀 **Individual Volumes**  
  - 📑 **Volume Groups**  

---

## ✅ Key Takeaways
- Cloning is a **fast and efficient alternative** to backup & restore.  
- Useful for **testing, development, and rapid provisioning**.  
- Remember: **Same region, same AD, same tenancy**.  
