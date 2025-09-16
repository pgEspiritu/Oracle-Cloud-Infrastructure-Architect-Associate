# 📦 Multipart Uploads in OCI

## 🚀 Introduction
- Multipart uploads transfer data **in parallel** → faster & more efficient than single large uploads  
- If upload fails, 🔁 only re-upload the **failed part**, not the entire object  

---

## 📏 When to Use Multipart Upload
- Recommended if object size **> 100 MiB**  
- 🔟 Maximum **10,000 parts** per object  
- 📐 Each part:
  - Minimum: **10 MiB**  
  - Maximum: **50 GiB**  
- ⏸️ Uploads can be paused/resumed based on resources  

---

## 🗑️ Lifecycle Policies
- Use **Object Lifecycle Rules** to auto-delete ❌ uncommitted/failed multipart uploads after set number of days  
- Configurable via **OCI Console**  

---

## ⚙️ Multipart Upload Using API

### 🔢 Steps:
1. **Split Object**  
   - Example: 200 MB object → 🔟 parts of 20 MB each  

2. **Initiate Upload**  
   - Call **Create Multipart Upload REST API**  
   - Response: **Upload ID** (active until commit/abort)  

3. **Upload Parts**  
   - Call **Upload Part Request** for each part  
   - Returns **ETag** per part (needed for commit)  

4. **Commit Upload**  
   - Call **Commit Multipart Upload Request**  
   - Object Storage reconstructs the object from parts  

---

## 💻 Multipart Upload Using CLI

### 🔑 Key Differences vs API:
- No manual splitting needed → specify **part size** and OCI handles splitting  
- Auto-commit ✅ (no explicit commit step)  
- Can configure **parallel uploads**  

### 📝 Command Example:
```bash
oci os object multipart put \
  --bucket-name <bucket_name> \
  --name <object_name> \
  --file <large_file> \
  --part-size <size_in_MiB> \
  --parallel-upload-count <N>
```
- `--part-size` (mandatory) = integer in MiB
- `--parallel-upload-count` (optional) = max number of parts uploaded in parallel

---

## ✅ Summary
- Multipart uploads = ⚡ efficient, reliable, resumable
- Use API if you want fine-grained control (parts, ETags, commit)
- Use CLI for simpler, faster automation (no manual splitting, auto-commit)
