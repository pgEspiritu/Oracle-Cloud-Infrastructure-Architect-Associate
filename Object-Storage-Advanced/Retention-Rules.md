# 📘 Lesson: Retention Rules in Object Storage

## 🛡️ What Are Retention Rules?
- Protect data from **accidental or malicious updates, overwrites, or deletions**  
- Provide **immutable WORM-compliant storage** in both Object and Archive storage  
- Can be **locked** to prevent modifications (even by administrators)  
- Configured at the **bucket level**  

---

## 🔄 Types of Retention Rules
1. ⏳ **Time-Bound**
   - Specify **Retention Time Amount** + **Unit**  
   - Prevents modifications/deletions for the set duration  
   - Optional: **Enable Retention Rule Lock**  
   - Rule applied **per object**, based on **last modified timestamp**  

2. ♾️ **Indefinite**
   - Prevents modifications/deletions until the rule is deleted  
   - No need to specify duration  

---

## 🔒 Retention Rule Lock
- **Irreversible operation**  
- ⏱️ **14-day delay** before a rule is permanently locked  
- During delay → you can **test, modify, or delete** the rule  
- Once locked → rule deletion is only possible by **deleting the bucket**  

---

## 📅 Example: Time-Bound Rule
- Bucket **OCI** with 2 objects:  
  - 📄 `OCI_test` → last modified **14 months ago**  
  - 📄 `OCI_demo` → last modified **3 months ago**  
- Retention Rule: **1 year (12 months)**  
- Results:  
  - ✅ `OCI_test` → modification/deletion allowed (older than 1 year)  
  - ❌ `OCI_demo` → protected for next **9 months**  

---

## 📂 Multiple Retention Rules
- A bucket can have **multiple rules**  
- ♾️ **Indefinite rules** take precedence over ⏳ time-bound rules  

---

## 🏷️ Use Cases
- 📜 **Regulatory Compliance** → time-bound retention  
- 🗂️ **Data Governance** → time-bound retention (rule not locked for flexibility)  
- ⚖️ **Legal Hold** → indefinite retention (remains in effect until removed)  

---

## 🔗 Integration with Other Features
- 🔐 Retention rules **do not block bucket re-encryption** (Oracle-managed or Vault keys)  
- 🔄 Lifecycle policies:  
  - Can update **storage tier** of protected objects  
  - ❌ Cannot delete objects under active retention rules  
- 🌍 Replication: retention rules can be created on **source buckets**  
- 🚫 Retention rules **cannot be added** to buckets with **versioning enabled**  

---

## ✅ Key Takeaways
- Retention rules = **data immutability & compliance**  
- Choose between **time-bound** or **indefinite** depending on use case  
- **Locks make rules permanent** → plan carefully  
