# 🗂️ Lesson: Object Versioning

## 🚀 Introduction
Object Versioning in OCI automatically creates a new version of an object whenever:  
- 📤 A new object is uploaded  
- ✏️ An existing object is overwritten  
- 🗑️ An object is deleted  

⚙️ Enabled at the **bucket level**:  
- ✅ Can enable at creation or later  
- ⛔ Cannot disable (only suspend)  

---

## 🛡️ Benefits
- 🔒 Protection from **accidental or malicious overwrite/delete**  
- 🕒 Retains **latest + previous versions**  
- 💰 Charged for all versions until explicitly deleted  

---

## 📊 Versioning Status

### ❌ Disabled
- ✏️ Upload with same name → overwrites existing (not recoverable)  
- 🗑️ Delete → permanent, cannot be recovered  

### ✅ Enabled
- ✏️ Upload with same name → old object becomes **previous version**, new one is **latest**  
- 🗑️ Delete → creates a **delete marker**, old version retained  
- 🆔 Each version has a **unique identifier**  

### ⏸️ Suspended
- 📥 Behaves like **Disabled** for new operations  
- 📦 Existing versions remain until explicitly deleted  
- 🔄 Can re-enable anytime  

---

## 🔗 Interactions with Other Features
- 🔐 **Bucket Re-encryption** → applies to all versions  
- 📜 **Lifecycle Policies**:  
  - Archive/delete **latest** → becomes previous + delete marker created  
  - Delete **previous** → permanent  
- 📑 **Copy Object** → only selected version is copied  
- 🔄 **Replication** → only latest version replicated (not previous)  
- ⛔ Cannot enable versioning on:  
  - Replication destination bucket (read-only)  
  - Bucket with **active retention rules**  

---

## ✅ Key Takeaways
- ⚙️ Versioning is **bucket-level**  
- 🛡️ Protects against overwrite & delete  
- ⏸️ Can only **suspend**, not disable  
- 💾 All versions consume **storage and cost**  
