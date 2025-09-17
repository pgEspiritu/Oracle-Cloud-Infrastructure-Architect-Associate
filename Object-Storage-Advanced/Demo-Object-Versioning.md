# 🧪 Demo: Working with Object Versioning

## 🔑 Step 1: Enable Versioning
- 🪣 Go to **bucket** → click **Edit** → enable **Object Versioning**  
- 🆕 You can also enable versioning during **bucket creation** by selecting the checkbox  

---

## 📤 Step 2: Upload Object
- Upload `versioningtestfile.txt` → content = **v1**  
- Re-upload with changes → content = **v2**  
- 🆚 View versions via **Show Object Versions**:  
  - 📄 Previous version = v1  
  - 📄 Latest version = v2  

---

## 🗑️ Step 3: Delete Object
- Deleting object does **not** erase data → creates a **Delete Marker**  
- 🔎 Use **Show Deleted Objects** to see:  
  - v1, v2, and Delete Marker  
- To restore → **delete the Delete Marker**  
  - The most recent version (v2) becomes **latest active version**  

---

## ❌ Step 4: Delete Object Version
- Deleting a **specific version** = permanent ❗  
- 🗑️ Example: delete v1 → cannot recover it  
- If **latest version** is deleted → also gone permanently  
- ⚠️ Difference:  
  - **Delete Object** → adds Delete Marker (can restore)  
  - **Delete Version** → permanent removal  

---

## ⏸️ Step 5: Suspend Versioning
- ⚙️ Versioning cannot be disabled, only **suspended**  
- 📴 Suspend → behaves like versioning disabled for new uploads/deletes  
- 🔄 Can re-enable anytime, old versions remain intact  

---

## ✅ Key Takeaways
- 🛡️ Versioning protects against overwrite & accidental deletion  
- 🔎 Use **Show Object Versions** & **Show Deleted Objects** for recovery  
- ⚠️ Deleting an **object version** = permanent, no restore  
- ⏸️ Can only **suspend**, not disable, versioning  
