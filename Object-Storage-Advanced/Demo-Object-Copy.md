# 📦 OCI Object Copy Demonstration

## 🔑 Setup

- Logged in to **OCI Console** using **storageadmin** user.  
- Inside a bucket (Phoenix region) with a few uploaded images.  
- In **Ashburn region**, there’s an empty bucket named **`demobucket`**.  

Goal: Copy objects from Phoenix bucket ➝ **Ashburn’s `demobucket`**.  

---

## 📝 Copy Object Steps

1. **Select Object** → e.g., `imageA`.  
2. **Click Ellipsis → Copy Object**.  
3. Provide:  
   - **Destination Namespace**  
   - **Destination Region** → Ashburn  
   - **Destination Bucket Name** → `demobucket` (must exist beforehand)  
   - **Destination Object Name** → e.g., `imageA.png`  
   - **Storage Tier** → Standard  
4. **Overwrite Rules (ETag matching):**
   - ✅ Overwrite destination object  
   - 🚫 Do not overwrite destination object  
   - 🎯 Overwrite destination object **only if ETag matches** (destination)  
   - 🎯 Copy object **only if source ETag matches**  

---

## 📖 Understanding ETag Rules

- **ETag** = unique identifier for a resource version.  
- **After copy**, the ETag of source and destination objects **will differ**.  

### Example Rules:
- **Overwrite Destination Object** → No ETag check.  
- **Do Not Overwrite** → Prevents overwriting regardless of ETag.  
- **Overwrite if Destination ETag Matches** → Copies only when ETag provided matches destination’s ETag.  
- **Copy if Source ETag Matches** → Copies only when ETag provided matches source’s ETag.  

---

## 🧪 Demonstration

### 1. Overwrite Destination Object
- Copy `imageA.png` from Phoenix → Ashburn `demobucket`.  
- ✅ Status → **Completed**.  
- Destination object appears with **new ETag**.  

### 2. Overwrite Destination Object (ETag Validation)
- Try again, but change 1 character in ETag.  
- ❌ Copy **failed** because ETag mismatch.  
- Retry with **correct ETag** → ✅ Copy succeeded.  

### 3. Copy if Source Matches ETag
- Select `imageB.png`.  
- Use **Source ETag** as condition.  
- If incorrect → ❌ Fails.  
- If correct → ✅ Copy succeeds.  

---

## 📌 Key Takeaways

- Destination bucket **must exist** beforehand.  
- **ETag changes** after copying.  
- Use overwrite rules to control accidental object overwrites.  
- Supports both **destination-based** and **source-based** ETag validations.  
