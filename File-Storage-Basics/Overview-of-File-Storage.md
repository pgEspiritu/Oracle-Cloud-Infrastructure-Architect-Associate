# Lesson: Overview of File Storage

## 📂 What is File Storage?

- Supports **NFS v3.0** (Network File System).  
- Data is **replicated for durability** within each availability domain.  
- A **fully managed, elastic file system** that scales automatically up to **8 exabytes**.  
- Designed for applications that require a **shared file system**.  
- Provides a **durable, scalable, secure, and enterprise-grade** storage solution.

---

## 🌐 Connectivity

You can connect to file storage from:
- **Bare metal, VM, or container instances** in your VCN.  
- Outside the VCN via:
  - 🔗 VCN Peering  
  - ⚡ OCI FastConnect  
  - 🔒 IPSec VPN  

📌 **No upfront provisioning** → Scales automatically from **1 byte to exabytes**.

---

## 🔑 Features

- Supports **NFS v3.0** protocol.  
- Supports **Network Lock Manager (NLM)** protocol for file locking.  
- **Snapshots** available for data protection.  
- **Encryption**:  
  - At rest: AES-256 (default Oracle-managed keys).  
  - Option to use **customer-managed keys** via OCI Vault.  
- **In-transit encryption**: TLS to secure data between instances and mounted file systems.  

---

## 📌 Use Cases

- 🚀 **Lift & Shift Enterprise Apps** (e.g., Oracle E-Business Suite).  
- 📈 **Unlimited pool of file systems** for structured & unstructured data.  
- 📊 **Analytics workloads** with persistent data storage.  
- ⚡ **Scale-out applications**.  
- 🧪 **Test & development workloads**.  
- 🐳 **Persistent storage for containers**.  
- 💻 **Large compute clusters** → thousands of instances with **high-performance shared storage**.

---

## ✅ Summary

The **File Storage Service (FSS)** in OCI is:
- Elastic, fully managed, and highly scalable.  
- Secure with **default encryption** at rest and optional in-transit encryption.  
- A great choice for **enterprise workloads, analytics, scaling apps, and container persistence**.  
