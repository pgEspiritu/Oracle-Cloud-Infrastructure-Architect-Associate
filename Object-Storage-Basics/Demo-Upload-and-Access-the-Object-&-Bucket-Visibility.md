# 📂 Uploading and Accessing Objects in OCI

## 🎯 Overview
In this demo, we will:
- 📤 Upload objects to an OCI bucket  
- 👀 Access the uploaded objects  
- 🔐 Understand bucket visibility options (private vs public)  
- 💻 Upload objects using **Cloud Shell**  

---

## 🌐 Step 1: Upload Object via OCI Console
1. Go to **OCI Console → Object Storage → Buckets**  
2. Select an existing bucket (e.g., `ociaabucket-console`)  
3. Scroll to **Objects → Upload**  
4. Provide an **Object Name Prefix** (e.g., `OCI/Training/`)  
5. Choose a **Storage Tier**:
   - 🟢 **Standard** → frequently accessed objects  
   - 🟡 **Infrequent Access** → less frequent usage  
   - 🔵 **Archive** → rarely accessed data  
   > ⚠️ Storage tier options depend on the **bucket’s default tier**.  
6. Select a file (e.g., `sample.jpg`) and click **Upload**  
7. ✅ Object appears under the prefix path: `OCI/Training/sample.jpg`  
   > Note: Object Storage has a **flat hierarchy**, but prefixes simulate folders.  

---

## 🔒 Step 2: Access Restrictions
- By default, bucket visibility = **Private**  
- Trying to access the object URL ❌ **fails** because it requires authentication  

### 🌍 Making the Bucket Public
1. Edit bucket settings → change **Visibility** to **Public**  
2. Warning: OCI recommends **Pre-Authenticated Requests (PARs)** instead of public buckets  
3. Save changes  
4. Now, refreshing the object URL ✅ shows the uploaded file  

---

## 💻 Step 3: Upload Object via Cloud Shell
1. Launch **Cloud Shell** from OCI Console  
2. Run the upload command:  
   ```bash
   oci os object put \
     --bucket-name <bucket_name> \
     --file sample.jpg
   ```
3. Output shows 100% upload complete
4. Verify in Console → Object appears in bucket

---

## ✅ Summary

- 📤 Uploaded object using both Console and Cloud Shell
- 🔒 Learned that private buckets block public access
- 🌍 Made bucket public to allow anonymous access
- ⚠️ Best practice → use Pre-Authenticated Requests (PARs) instead of public buckets
