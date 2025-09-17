# 🗂️ Lesson: Object Storage Replication

## 🚀 Introduction
- 📦 Replication Policy → Replicate objects from one bucket (**source**) to another bucket (**destination**) in the **same** or a **different region**.  
- 🛠️ Destination bucket becomes **read-only** → updated only by replication.  
- 🔄 Objects are **asynchronously replicated** after policy creation.  
- ⛔ Objects uploaded **before policy creation** are **not replicated**.  
- 🗑️ Deleting an object in the **source** also deletes it in the **destination**.  

---

## 🌍 Example Scenario
- 📍 Source: **Mumbai Region** → two buckets  
- 🎯 Destination: **Hyderabad Region** (or another bucket in Mumbai itself)  
- 🔗 Replication works **within the same region** or **across different regions**.  

---

## 🎯 Benefits of Replication
- 🛡️ **Disaster Recovery** support  
- 📜 **Compliance & Data Residency** requirements  
- 🌐 Protection from **regional outages**  
- ⚡ Lower **latency** with multiple copies closer to users  

---

## 🛠️ Creating a Replication Policy
- 📝 Provide a **Policy Name**  
- 🌍 Select **Destination Region**  
- 📦 Specify **Destination Bucket**  
- ⚠️ **Note**: Policy does **not** auto-create the destination bucket  
- ⚠️ Replication will **overwrite objects** in destination with the same name as in source  

---

## ⚖️ Limitations & Considerations
- 📦 Must **manually create** destination bucket before enabling replication  
- 🗄️ Source/Destination buckets can be **Standard** or **Archive** tiers  
- 🔢 Maximum limits:  
  - 1️⃣ Replication policy per **source bucket**  
  - 1️⃣ Source per **destination bucket**  
  - 1️⃣ Destination per **source bucket**  
- 🔗 ❌ **Chain replication not supported** (a destination cannot also be a source)  
- 🔒 Destination bucket = **read-only** after policy creation  
- 🚫 Cannot delete replication destination bucket unless:  
  - ❌ Delete replication policy from source  
  - 🔓 Stop replication on destination (make bucket writable again)  

---

## ✅ Key Takeaways
- 🔄 Replication ensures **durability, compliance, and disaster recovery**.  
- ⛔ Pre-policy objects are **not replicated**.  
- 🔒 Destination bucket is **read-only** → uploads only via source.  
- ⚠️ One-to-one mapping rules apply (no chaining, no multiple destinations).  
