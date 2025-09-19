# 📦 OCI Block Volume – Access Types  

## 🔑 Overview  
OCI Block Volume service allows **multiple instances** to connect to the **same volume**. There are **three access types** available:  

---

## 1️⃣ Read/Write (Default)  
- Configures the volume attachment as **read/write**.  
- ❌ **Not shareable** with other instances.  
- ✅ Enables attachment to a **single instance only**.  
- 📌 This is the **default** configuration.  

---

## 2️⃣ Read/Write Shareable  
- Configures the volume attachment as **read/write**.  
- ✅ **Shareable** with multiple instances.  
- ⚠️ Requires a **clustered file system** (e.g., OCFS2) to prevent data corruption.  
- ✅ Enables concurrent read/write attachments.  

---

## 3️⃣ Read-Only Shareable  
- Configures the volume attachment as **read-only**.  
- ✅ **Shareable** with multiple instances.  
- ❌ No data corruption risk since writes are not allowed.  

---

## 📊 Access Types – Quick Comparison  

| Access Type          | Shareable? | Mode       | Max Instances | Notes |
|----------------------|------------|------------|---------------|-------|
| **Read/Write**       | ❌ No       | R/W        | 1             | Default setting |
| **Read/Write Shareable** | ✅ Yes   | R/W        | Up to 8       | Requires clustered FS (e.g., OCFS2) |
| **Read-Only Shareable** | ✅ Yes   | Read-only  | Up to 8       | Safe sharing, no writes |

---

## ⚠️ Important Callout  
- When using **Read/Write Shareable**, you **must install and configure a clustered file system** (such as **OCFS2**) before use.  
- This is because the **block volume service does not coordinate concurrent write operations**.  

---

## ✅ Key Takeaways  
- **Read/Write** → Single instance, default mode.  
- **Read/Write Shareable** → Multi-instance writes, requires clustered FS.  
- **Read-Only Shareable** → Multi-instance read-only access, safe for sharing.  
