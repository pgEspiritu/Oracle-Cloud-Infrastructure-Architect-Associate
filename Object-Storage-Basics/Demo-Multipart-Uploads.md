# 📦 OCI CLI Multipart Upload Demonstration

## 🚀 Introduction
- Multipart uploads = **parallel data transfer** → faster & more efficient  
- 🔑 Oracle recommends: Use multipart uploads if object size **> 100 MiB**  
- With **OCI CLI**, you **don’t need to split objects manually**  
- Service splits into parts based on `--part-size` flag  
- Optional: `--parallel-upload-count` to control parallelism  

---

## ⚙️ Command Structure

```powershell
oci os object multipart put `
  --bucket-name <bucket_name> `
  --name <object_name> `
  --file <file_name> `
  --part-size <size_in_MiB> `
  --parallel-upload-count <N>
```

### 🔑 Key Flags:

- `--bucket-name` 🪣 → target bucket
- `--file` 📂 → local file to upload
- `--name` 🏷️ → object name in OCI (can differ from filename)
- `--part-size` 📏 → part size in MiB (integer, mandatory)
- `--parallel-upload-count` ⚡ → max parts uploaded in parallel (optional)

---

### 📝 Example: Windows PowerShell

```powershell
oci os object multipart put `
  --bucket-name ociaabucket `
  --name ocitestfile.bin `
  --file ocitest.bin `
  --part-size 20 `
  --parallel-upload-count 10
```

### 🖇️ Explanation:

- Bucket: ociaabucket
- File uploaded: ocitest.bin
- Object name in bucket: ocitestfile.bin
- Part size: 20 MiB → 1 GiB file = split into 50 parts
- Parallel uploads: 10

---

### 📊 Upload Process
- OCI Object Storage assigns an Upload ID 🔑
- Progress shown in CLI: % complete + ETA ⏱️
- Parts uploaded in parallel until complete
- On success ✅ → object appears in bucket

---

### 🔍 Validation
- Open OCI Console → navigate to target bucket
- Confirm object uploaded (e.g., ~1 GiB ocitestfile.bin)

---

### ✅ Summary
- Multipart uploads via CLI are:
  - ⚡ Fast
  - 🔄 Resumable
  - 📐 Efficient for large files
- Mandatory flag: --part-size
- Optional flag: --parallel-upload-count
