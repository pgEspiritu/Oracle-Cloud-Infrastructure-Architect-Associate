# 🗂️ Demonstration: Creating a Replication Policy

## 🚀 Introduction
In this demo, we will create and test an **Object Storage Replication Policy** in OCI.

---

## 🛠️ Steps to Create Replication Policy

### 1️⃣ Create Source Bucket
- 🌍 Logged in as **storageadmin**
- 📍 Region: **Phoenix**
- 🪣 Bucket Name: `sourcebucket`
- 📤 Uploaded **imageA** *(before policy creation)*

⚠️ Objects uploaded **before policy creation** will **not replicate**.

---

### 2️⃣ Create Destination Bucket
- 📍 Region: **Ashburn**
- 🪣 Bucket Name: `targetbucket`
- ✍️ Created manually before replication policy
- ✅ Initially in **read/write** state

---

### 3️⃣ Create Replication Policy
- From **Phoenix Source Bucket** → **Replication Policy → Create Policy**
  - 📝 Policy Name: `ociaa replication policy`
  - 🌍 Destination Region: **Ashburn**
  - 🪣 Destination Bucket: `targetbucket`
- ✅ Policy created successfully

🔒 Now:
- Source bucket shows **Replication Enabled (Source)**
- Destination bucket shows **Replication Enabled (Destination, Read-Only)**

---

## 🔄 Replication Behavior

### ✅ After Policy Creation
- 📤 Upload **imageB** to `sourcebucket`  
- 📥 `targetbucket` shows **imageB replicated**  

### ⛔ Before Policy Creation
- 📤 **imageA** was uploaded earlier  
- 🚫 Not replicated to destination  

### 🗑️ Delete Behavior
- Deleting **imageB** from source → also deleted from destination  

---

## 🛑 Stopping Replication

### Source Side
- 🪣 From `sourcebucket` → Replication Policy → **Delete Policy**  
- ⚠️ Once deleted, replication stops & policy **cannot be recovered**  

### Destination Side
- 🪣 From `targetbucket` → Replication Policy → **Stop Replication**  
- 🔓 Bucket reverts back to **standard read/write** state  
- ⚠️ Policy is removed and **cannot be recovered**  

---

## ✅ Key Takeaways
- 📌 Destination bucket must exist **before** creating replication policy  
- 🔒 Destination becomes **read-only** during replication  
- ⛔ Objects uploaded **before policy creation** are not replicated  
- 🔄 Objects uploaded/deleted in source are replicated/deleted in destination  
- 🛑 Replication can be stopped from **source (delete policy)** or **destination (stop replication)**  
