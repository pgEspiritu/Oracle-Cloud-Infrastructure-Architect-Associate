# 🔗 OCI Block Volume – Attachment Types  

## ⚙️ Volume Attachment Options  
When you attach a **Block Volume** to a VM instance, there are **two attachment types** available:  

1. **iSCSI Attachment**  
2. **Paravirtualized Attachment**  

---

## 🔹 iSCSI Attachment  
- Uses **internal storage stack** in the **guest OS**.  
- Leverages **network hardware virtualization**.  
- ❌ **Hypervisor not involved**.  
- ⚡ Provides **higher maximum IOPS performance**, especially for large block volumes.  
- 🔑 Best for **IOPS-intensive workloads**.  

---

## 🔹 Paravirtualized Attachment  
- A **lightweight virtualization technique**.  
- VM/guest OS uses **hypervisor APIs** to access remote storage as if it were local.  
- ✅ **Simplifies configuration** → no extra commands required to access volume.  
- ⚠️ Comes with **virtualization overhead**, reducing maximum IOPS performance compared to iSCSI.  
- 🔑 Best for **simpler setups** where ease of use > raw performance.  

---

## 📊 iSCSI vs Paravirtualized – Quick Comparison  

| Feature                  | iSCSI Attachment | Paravirtualized Attachment |
|--------------------------|------------------|-----------------------------|
| **Hypervisor Involvement** | ❌ No             | ✅ Yes (via APIs)            |
| **Performance (IOPS)**   | ⚡ Higher          | ⚠ Lower (overhead present)  |
| **Ease of Setup**        | ⚠ Requires setup commands | ✅ Simple, no extra setup  |
| **Use Case**             | IOPS-sensitive workloads | General workloads, quick access |

---

## ✅ Key Takeaways  
- Use **iSCSI** when **performance & IOPS** are critical.  
- Use **Paravirtualized** when you want **ease of management** with simpler configuration.  
