# 🔄 Object Lifecycle Management

## 🎯 Overview
Object Lifecycle Management helps you manage the lifecycle of your Object Storage data through **automated archiving and deletion**, reducing storage costs and saving time.  
It works by applying **rules** that trigger actions on objects.  

---

## ⚙️ Supported Lifecycle Actions
- ❄️ Move to **Infrequent Access**  
- 🗃️ Move to **Archive**  
- 🗑️ Delete  

### 🧩 Supported Resources
- 📦 Objects  
- 📑 Object Versions  
- 🚫 Uncommitted / Failed Multipart Uploads  

---

## 📌 Key Rules & Restrictions
- 🗑️ **Delete rules** always take priority over move rules.  
- 🤖 If **Auto-Tiering is enabled**, you cannot create rules to move objects to Infrequent Access.  
- 📂 Up to **1,000 lifecycle rules per bucket**.  
- 🗃️ On Archive buckets → only **delete rules** are supported.  
- 📜 Lifecycle policies apply to **both old and new data**.  
  - Example: A rule archiving objects >30 days old will immediately archive objects already older than 30 days.  

---

## 🔎 Object Name Filters
### 1. **Prefix Matching**
- Matches **left-most characters** of object names.  
- ❌ Wildcards not supported.  
- Example:  
  - Prefix = `training/oci`  
  - Matches → `training/oci/os.jpg`  

### 2. **Pattern Matching**
- Matches the **entire object name**.  
- ✅ Supports wildcards.  
- Example:  
  - Pattern = `*.jpg`  
  - Matches → `oci.jpg`, `training/oci/test.jpg`  

---

## 📊 Rule Precedence
Evaluation order when filters overlap:  
1. 🚫 Exclude by Pattern  
2. ✅ Include by Pattern  
3. 🔡 Include by Prefix  

---

## 🛠️ Supported Policy Options
- Move or delete **all objects** in a bucket.  
- Move or delete **filtered objects** (prefix/pattern-based).  
- Delete **uncommitted/failed multipart uploads**.  
- If **object versioning** is enabled/suspended:  
  - Rules can target both **previous** and **latest** object versions.  

---

## 🧪 Example Lifecycle Policies
- ⏳ Move **Standard-tier objects** → Archive **after 30 days**.  
- 🗑️ Delete **archived objects** after **180 days**.  
- 🚫 Delete **uncommitted/failed multipart uploads** after **5 days**.  

---

## ✅ Key Takeaways
- Automates **archiving and deletion**.  
- Supports **prefix & pattern-based filters**.  
- Rules follow **strict precedence**.  
- Works with **object versions** and multipart uploads.  
- Saves time & reduces cost through **policy-driven management**.  
