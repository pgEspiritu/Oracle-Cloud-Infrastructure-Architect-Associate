# 🗄️ OCI Object Storage Tiers

## 🎯 Purpose
Storage tiers help balance:
- ⚡ **Performance** (fast access when needed)  
- 💲 **Cost optimization** (pay less for cold/rarely accessed data)  

---

## 🪣 Bucket-Level Storage Tier Options
- **Standard Storage Tier Bucket**  
  - ✅ Can contain **mixed object storage tiers** (Standard, Infrequent Access, Archive)  

- **Archive Storage Tier Bucket**  
  - 📦 Can contain **only archive objects**  

⚠️ Once a bucket’s default storage tier is set, it **cannot be changed**.  

---

## 📦 Object Storage Tiers

### 1️⃣ Standard Tier
- 🔑 **Default tier**  
- ⚡ **Frequent & immediate access**  
- 💰 Higher storage cost than other tiers  
- 🔄 Supports **auto-tiering**  
- **Use cases**:  
  - 🖼️ Content repositories (images, logs, videos)  
  - 📊 Hadoop / Big Data workloads  

---

### 2️⃣ Infrequent Access (Cool) Tier
- ⏳ **Occasional access** but still **immediate availability**  
- 💲 Lower storage cost than Standard  
- 📅 **31-day minimum retention period**  
- 💵 Retrieval incurs **per GB fees**  
- **Use cases**:  
  - 💾 Backups for on-premises data  

---

### 3️⃣ Archive Tier
- 💤 **Rare access, long-term retention**  
- 💲 **Lowest storage cost**  
- 📅 **90-day minimum retention period**  
- 🔄 Objects must be **restored to Standard** before access  
- ⏱️ Restore time ≈ **1 hour**  
- **Use cases**:  
  - ⚖️ Compliance & audit requirements  
  - 📜 Historical data storage  

---

## ✅ Key Takeaways
- 📍 Choose the right tier based on **access frequency** & **cost sensitivity**.  
- 🪣 **Standard buckets** → flexible (all tiers allowed).  
- 🪣 **Archive buckets** → archive-only objects.  
- ⚠️ Tier choice at **bucket creation** is permanent.  
