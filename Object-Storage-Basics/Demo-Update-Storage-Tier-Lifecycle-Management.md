# 🧪 Demonstration: Working with Lifecycle Policy Rules

## 🔑 Setup
- 👤 Logged in as: **storageadmin**  
- 📦 Selected Bucket: `ociaabucket-console`  
- 🔧 Pre-demo changes:  
  - ❌ Disabled **Auto-Tiering** (to enable lifecycle “Move to Infrequent Access” option)  
  - ✅ Enabled **Object Versioning** (to demonstrate rules on versions)  

---

## 📤 Object Uploads
- 📂 Uploaded with prefix `OCI/training`:  
  - 🖼️ imageA  
  - 🖼️ imageB  
- 📂 Uploaded without prefix:  
  - 🖼️ imageC  

---

## 📜 Lifecycle Policy Rules
- 🏗️ A single **Lifecycle Policy** can contain up to **1,000 rules**.  
- 📑 Supported Resources:  
  - 🆕 Latest Object Versions  
  - 📜 Previous Object Versions  
  - 🚫 Uncommitted / Failed Multipart Uploads  
- ⚙️ Supported Actions:  
  - ❄️ Move to **Infrequent Access**  
  - 🗃️ Move to **Archive**  
  - 🗑️ Delete  

---

## 🎯 Object Name Filters
- 🔡 **Prefix Matching** → Exact left-most characters (no wildcards).  
- 🌀 **Pattern Matching** → Full object name (wildcards supported).  
- ⛔ **Exclude by Pattern** → Takes highest precedence.  

📊 **Precedence Order**:  
1. 🚫 Pattern Exclusion  
2. ✅ Pattern Inclusion  
3. 🔡 Prefix Inclusion  

---

## 🛠️ Demo Rule Creation

### 📏 Rule 1: `firstlifecyclerule`
- 🆕 Target: **Latest Object Versions**  
- ❄️ Action: **Move to Infrequent Access** after **30 days**  
- 🔡 Filter: **Prefix** → `OCI/training`  
- 🎯 Impact:  
  - 🖼️ imageA  
  - 🖼️ imageB  

---

### 📏 Rule 2: `secondlifecyclerule`
- 🆕 Target: **Latest Object Versions**  
- 🗃️ Action: **Move to Archive** after **90 days**  
- 🌀 Filter: **Pattern** → `*` (wildcard for all objects)  
- 🎯 Impact:  
  - 🖼️ imageA  
  - 🖼️ imageB  
  - 🖼️ imageC  

---

## ✅ Key Takeaways
- 🗂️ Lifecycle policies automate **archiving and deletion**.  
- 🔡 Filters can be applied via **prefix** or **pattern**.  
- 🧩 Rules follow strict **precedence order**.  
- 📦 Multiple objects/versions can be targeted under a single policy.  

