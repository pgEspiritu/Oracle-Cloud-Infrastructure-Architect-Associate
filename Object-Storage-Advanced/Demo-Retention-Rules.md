# 📘 Lesson: Retention Rules in Object Storage

## 🛡️ Overview
- Protect data from **accidental or malicious updates, overwrites, or deletions**  
- Provide **immutable WORM-compliant storage** in Object & Archive storage  
- Can be **locked** to prevent changes, even by administrators  
- Configured at the **bucket level**  

---

## 🔄 Types of Retention Rules
1. ⏳ **Time-Bound**
   - Specify **Retention Time Amount** + **Unit**  
   - Prevents modification/deletion for the set duration  
   - Optional: **Enable Retention Rule Lock**  

2. ♾️ **Indefinite**
   - Prevents modification/deletion until rule is deleted  
   - No duration required  

---

## 🔒 Retention Rule Lock
- **Irreversible operation**  
- ⏱️ Mandatory **14-day delay** before a lock becomes permanent  
- During delay → rule can be **tested, modified, or deleted**  
- Once locked → only way to delete is by deleting the **bucket**  

---

## 📅 Example: Time-Bound Rule
- Bucket **OCI** with 2 objects:  
  - 📄 `OCI_test` → last modified **14 months ago**  
  - 📄 `OCI_demo` → last modified **3 months ago**  

**Retention Rule:** 1 year (12 months)  

- ✅ `OCI_test` → modification/deletion allowed (older than 1 year)  
- ❌ `OCI_demo` → protected for next **9 months**  

---

## 📂 Multiple Retention Rules
- Buckets can have **multiple rules**  
- ♾️ **Indefinite rules take priority** over ⏳ time-bound rules  

---

## 🏷️ Use Cases
- 📜 **Regulatory Compliance** → time-bound rules  
- 🗂️ **Data Governance** → time-bound rules (not locked for flexibility)  
- ⚖️ **Legal Hold** → indefinite rules  

---

## 🔗 Integration with Other Features
- 🔐 Retention rules **do not block bucket re-encryption** (Oracle-managed or Vault keys)  
- 🔄 Lifecycle policies:  
  - ✅ Can update **storage tier**  
  - ❌ Cannot delete protected objects  
- 🌍 Replication: rules can be created on **source buckets**  
- 🚫 Cannot add retention rules to buckets with **versioning enabled**  

---

## ✅ Key Takeaways
- Retention rules = **data immutability & compliance**  
- Choose **time-bound** or **indefinite** based on business need  
- **Locks are permanent** → plan carefully  
