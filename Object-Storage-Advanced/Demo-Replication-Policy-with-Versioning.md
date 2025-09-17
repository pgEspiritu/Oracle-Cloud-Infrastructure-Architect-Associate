# 🧪 Demo: Replication Policy with Object Versioning

## 🏗️ Setup
- 🌐 **Source Region:** Phoenix  
- 🪣 **Source Bucket:** Enabled with **Object Versioning + Replication**  
- 🌐 **Target Region:** Ashburn  
- 🪣 **Target Bucket:** Replication destination (read-only)  

---

## 📤 Step 1: Upload Initial File
- Upload `versioningtestfile.txt` → content = **v1**  
- ✅ Replication copies file automatically to **target bucket**  
- 🔎 Verify: target bucket shows `versioningtestfile.txt` → content = **v1**  

---

## ⚠️ Step 2: Attempt to Enable Versioning on Target
- Try enabling **versioning** on **target bucket** → ❌ Error:  
  - "You cannot enable versioning on a replication destination bucket"  

---

## 🔄 Step 3: Update File in Source
- Modify `versioningtestfile.txt` → content = **v2**  
- Upload again → source bucket now shows:  
  - 📄 Previous version = v1  
  - 📄 Latest version = v2  

---

## 📥 Step 4: Check Target Bucket
- Replication copies only **latest version**  
- 🔎 Target bucket object details = **v2**  
- 🛑 **Previous versions are not replicated**  

---

## ✅ Key Takeaways
- 📦 Replication works seamlessly with **latest object version**  
- 🚫 Target bucket cannot have **object versioning enabled**  
- 🕒 Only **latest versions** replicate — previous versions stay only in the **source bucket**  
