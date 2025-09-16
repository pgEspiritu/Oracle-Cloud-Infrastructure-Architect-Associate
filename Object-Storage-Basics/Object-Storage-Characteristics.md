# 📦 Object Storage Characteristics

## 🔑 Key Features

### 🔄 Strong Consistency
- Always serves the **most recent copy** of the data.  
- Ensures clients get **up-to-date results** for read requests.  

---

### 🛡️ High Durability
- Designed for **11 nines (99.999999999%) durability**.  
- Achieved by storing objects redundantly:  
  - 🌍 **Multi-AD Regions** → 3 different Availability Domains  
  - 🏢 **Single-AD Regions** → 3 different Fault Domains  

---

### 🔍 Data Integrity
- Integrity monitored with **checksums**.  
- **Corrupt data** is automatically detected and repaired.  
- Redundancy loss triggers **self-healing remediation** without customer intervention.  

---

### 🔒 Security
- All data is **encrypted at rest by default**.  
- Fully integrated with **OCI Identity and Access Management (IAM)**.  
- Data is transferred over **SSL endpoints** using **HTTPS**.  

---

### 📈 Scalability
- **Unlimited data storage**.  
- **Thousands of buckets** per account.  
- Each bucket can hold **unlimited objects**.  
- Object size range: **0 bytes → 10 TiB**.  

---

## ✅ Summary
- 📖 **Strong consistency** → always get the latest data  
- 🛡️ **Durability (11 nines)** → redundancy across ADs/FDs  
- 🔍 **Data integrity** → checksums + auto-repair  
- 🔒 **Security** → encryption + IAM integration + HTTPS  
- 📈 **Scalable** → virtually unlimited storage, buckets, and object size flexibility  
