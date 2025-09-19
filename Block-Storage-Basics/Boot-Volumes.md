# 💻 OCI Boot Volumes  

## 🚀 What Are Boot Volumes?  
Boot volumes provide **remote boot disks** for your instances. They are:  
- 🔒 **Encrypted by default**  
- ⚡ Offer **faster performance** and **lower launch times**  
- 💾 Provide **higher durability** for both **bare metal** and **virtual machine instances**  

---

## 🔧 Features of Boot Volumes  
- ✅ **Backup and Clone** operations are supported  
- ✅ You can adjust performance between:  
  - **Balanced**  
  - **Higher performance level**  
- 🛑 When you **terminate an instance**, you can **preserve the boot volume and its data**  

---

## 📏 Boot Volume Sizes  
- When launching an instance, you can:  
  - Use the **default boot volume size**  
  - Or specify a custom size **up to 32 TB**  

**Defaults by OS:**  
- 🐧 **Linux** → 46.6 GB  
- 🪟 **Windows** → 47 GB  

**Allowed Range:** 50 GB ➝ 32 TB  

---

## 🛠️ Troubleshooting with Boot Volumes  
- You can **detach** a boot volume from its instance  
- Then **attach it as a block volume** to another instance for inspection or recovery  

---

## ✅ Key Takeaways  
- Boot volumes are **encrypted, durable, and high-performing**.  
- Support **backup, clone, and performance tuning**.  
- Can be preserved even after **instance termination**.  
- Flexible size options, ranging from **50 GB up to 32 TB**.  
- Useful for **troubleshooting** by detaching and reattaching.  
