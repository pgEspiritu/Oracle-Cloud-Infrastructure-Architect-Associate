# 🗄️ Object Storage Resources

## 📌 Key Constructs

### 🏷️ Namespace
- A **top-level container** for all **buckets and objects**.  
- Assigned **once per tenant** at the time of account creation.  
- Unique across the tenancy.  

---

### 🪣 Bucket
- A **logical container** for storing objects.  
- Bucket names must be **unique per region within a tenancy**.  
  - Example:  
    - ✅ `demo-bucket` in **India West (Mumbai)**  
    - ❌ Cannot create another `demo-bucket` in Mumbai region  
    - ✅ You can create `demo-bucket` in **India South (Hyderabad)**  
- Buckets and objects exist in a **flat hierarchy** within a namespace.  

---

### 📦 Object
- Data stored as an **object + metadata**.  
- Objects exist in a **flat structure**, but **prefixes** can simulate directories.  

---

## 🌐 Object Storage Endpoint Structure
Example:  

```link
https://objectstorage.<region>.oraclecloud.com/n/<namespace>/b/<bucket>/o/<object>
```

- `/n/` → **Namespace**  
- `/b/` → **Bucket**  
- `/o/` → **Object**  
- `<region>` → Region of the bucket  
- `objectstorage` → Service name

```link
https://objectstorage.mumbai.oraclecloud.com/n/ociarchassociate/b/training/o/oci.jpg
```


---

## 📂 Prefixes (Simulated Hierarchy)
- Add a **prefix string** with `/` in the object name to simulate directories.  
  - Example:  
    - Object: `oci.jpg`  
    - Prefix: `training/oci/oci.jpg`  

### ✅ Benefits of Prefixes
- 📥 **Bulk operations** (delete/download) using CLI or API  
- 📊 Console displays a **hierarchical view** of objects  

---

## ✅ Summary
- **Namespace** = top-level container (unique per tenancy)  
- **Bucket** = logical container (unique name per region)  
- **Object** = stored data with metadata  
- **Endpoint** clearly shows namespace, bucket, and object path  
- **Prefixes** allow simulated directory structure & bulk operations  
👉 Example with values:  
