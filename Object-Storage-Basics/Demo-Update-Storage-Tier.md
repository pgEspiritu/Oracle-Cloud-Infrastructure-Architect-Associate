# 🗄️ Demonstration: Updating Storage Tiers & Enabling Auto-Tiering

## 🎯 What You’ll Learn
- How to **manually update** an object’s storage tier  
- How to **restore** objects from the Archive tier  
- How to **enable Auto-Tiering** at the bucket level  
- Key restrictions and IAM policy requirements  

---

## 📂 Manual Update of Storage Tier
1. Navigate to a **bucket** → select an **object** (e.g., `sample.jpg`).  
2. Click **Update Storage Tier** → choose a new tier:  
   - 📦 Standard  
   - ❄️ Infrequent Access  
   - 🗃️ Archive  

### 🔄 Example
- Changed `sample.jpg` from **Standard → Infrequent Access** ✅  
- Then updated it to **Archive** ❌ (download disabled until restored).  

---

## ♻️ Restoring Objects from Archive
- Objects in **Archive** cannot be downloaded directly.  
- Must **Restore** before use:  
  - ⏱️ Specify availability (1–240 hours, default = 24h).  
  - Example: restored for **1 hour** → showed **56 minutes** left when checked later.  
- After restore → status = **Archive Restored** → download enabled.  

---

## 🪣 Bucket Creation & Default Tier Rules
- Once a bucket is created with a **default storage tier**, ❌ it **cannot be changed**.  
  - Example: Bucket with **Archive default** cannot be switched to **Standard** later.  
- 🚫 **Auto-Tiering not available** on Archive-tier buckets.  
- ✅ **Auto-Tiering editable** only on Standard-tier buckets.  

---

## ⚙️ Enabling Auto-Tiering
- Go to **Standard bucket → Edit → Enable Auto-Tiering**.  
- Monitors **data access patterns** and automatically optimizes cost.  
- Enabled at **bucket level only**.  

---

## 🔐 IAM Policy Requirement
To allow Auto-Tiering, you must grant Object Storage service permissions:  
```
Allow service objectstorage-<region-identifier> to manage object-family in tenancy
```


---

## ✅ Key Takeaways
- 📂 Storage tiers can be changed manually per object.  
- 🗃️ Archive objects must be restored before download.  
- 🪣 Bucket default tier is **permanent** after creation.  
- 🤖 Auto-Tiering works **only with Standard buckets**.  
- 🔑 Requires **IAM policy** to authorize Object Storage service.  

