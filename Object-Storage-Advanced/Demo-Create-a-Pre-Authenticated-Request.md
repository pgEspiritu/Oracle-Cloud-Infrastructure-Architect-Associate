# 🧪 Demonstration: Working with Pre-Authenticated Requests (PARs)

Hello, and welcome. In this demonstration, I will show you how to work with **Pre-Authenticated Requests (PARs)**.  
We’ll cover **two scenarios**:  
1. Creating a PAR at the **object level**.  
2. Creating a PAR at the **bucket level** and using it to upload files.  

---

## 🔹 Demo 1: Object-Level Pre-Authenticated Request

1. Logged in to the **OCI Console** as `storageadmin`.  
2. Bucket visibility → changed to **private**.  
   - Tried accessing the object via URL → ❌ Access denied (expected).  
3. Created a **Pre-Authenticated Request** for a single object:  
   - Selected **Object** → `imageE.png`.  
   - Access Type → **Permit Object Reads**.  
   - Expiration → `30-Apr-2022`.  
   - Generated a unique **PAR URL** (copy immediately, not shown again).  
4. Accessed the URL → ✅ Object visible despite bucket being private.  

---

## 🔹 Demo 2: Bucket-Level Pre-Authenticated Request

1. Navigated to **Pre-Authenticated Requests** under bucket resources.  
2. Created a new PAR:  
   - Scope → **Bucket** (applies to all objects).  
   - Access Type → **Permit Object Reads and Writes**.  
   - Enabled **Object Listing** (optional).  
   - Generated **PAR URL**.  

---

### 📤 Uploading Objects with Bucket-Level PAR

**Using Cloud Shell (`curl`)**

```bash
curl -X PUT -T sample.jpg "<PAR_URL>"
```

- Uploaded `sample.jpg`.  
- Verified in the bucket → ✅ File visible.  

---

**Using Windows PowerShell (`curl`)**

```powershell
curl -X PUT -T "C:\Users\Me\Downloads\samvit.png" "<PAR_URL>"
```

- Uploaded `samvit.png`.  
- Verified in the bucket → ✅ File visible.  

---

## ✅ Key Takeaways

- **Object-level PAR** → restricts access to a single object.  
- **Bucket-level PAR** → enables access for all objects in the bucket (based on permissions).  
- You can use **cURL or OCI CLI** to upload objects with a PAR URL.  
- Buckets can remain **private** while still securely sharing or uploading objects via PARs.  
