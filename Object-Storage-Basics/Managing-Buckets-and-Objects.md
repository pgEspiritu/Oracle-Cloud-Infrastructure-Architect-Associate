# 🪣 Managing Buckets and Objects in OCI

## 📌 Key Rules
- 🔠 **Case sensitive** → bucket and object names  
- 🚫 **No nesting** → a bucket cannot contain other buckets  
- 📏 **Object size limit** → up to **10 TiB**  
- ✍️ **No edits/appends** → must replace entire object if updating  
- 🕓 **Versioning** → retain previous versions of objects  

---

## 🔑 Features

### 🔒 Pre-Authenticated Requests
- Provide access to a bucket/object **without credentials**  

### 🛡️ Retention Rules
- Applied at **bucket level**  
- Enable **immutable storage**  
- ✅ Use cases: governance, compliance, legal requirements  

### 🔄 Replication Policy
- Automatically replicate objects:  
  - 📍 Same region  
  - 🌍 Cross-region  

### 🧰 Security Zones
- Enforce **Oracle security principles**  
- Example: buckets must remain **private**  

### 📂 Object Copy
- Copy objects to:  
  - Buckets in same region  
  - Buckets in other regions  

### 🗓️ Lifecycle Policies
- Automate:  
  - 📦 Archiving  
  - 🗑️ Deletion  
- Based on **predefined schedule**  

---

## ✅ Summary
- Buckets and objects in OCI have strict rules (case sensitivity, size limits, no nesting).  
- Advanced features include **versioning, replication, retention rules, lifecycle policies, and security zones**.  
- These enable compliance, governance, and efficient data management.  
