# 📘 Lesson: Object Copy in Object Storage

## 🛡️ Overview
- Copy objects:
  - ✅ To buckets in the **same region**  
  - ✅ To buckets in **other regions**  
- Copy requests are handled **asynchronously**  
- 🚫 Cannot copy directly from **Archive Storage**  
- 🚫 Copy operation does **not auto-create buckets**  
- Each copied object gets a **new ETag**  

---

## 🔄 Overwrite Rules (4 Types)

1. **Overwrite destination object** *(default)*  
   - Always overwrites destination object  
   - Use when no ETag restrictions are needed  

2. **Do not overwrite any destination object**  
   - Prevents overwriting if destination object already exists  
   - Ignores destination object’s ETag value  

3. **Overwrite destination object only if ETag matches**  
   - Copy succeeds only if supplied ETag = destination object’s ETag  
   - Useful to prevent **accidental overwrite**  

4. **Copy object only if source ETag matches**  
   - Copy succeeds only if supplied ETag = source object’s ETag  
   - Ensures only the **specified version** of the source is copied  

---

## 📝 Copy Operation Requirements
- **Destination Namespace**  
- **Destination Region**  
- **Destination Bucket**  
- (Optional) **Destination Object Name**  
- (Optional) **Destination Storage Tier**  
- Select **one overwrite rule** before execution  

---

## ✅ Key Takeaways
- Object copy = move data **across regions or buckets**  
- New copy always gets a **new ETag**  
- Choose overwrite rule carefully to control **data consistency & safety**  
- Not supported for **direct archive-to-archive copy**  


