# 🖥️ OCI Demo – Creating a Block Volume Clone

## 🔹 Steps to Create a Clone
1. Navigate to **Block Volumes** and identify the volume you want to clone.  
2. Click on the **ellipsis (⋮)** → **Create Clone**.  
3. Provide a **name** (e.g., `Demo Clone`).  
4. Select the **compartment**.  
5. (Optional) Customize:  
   - 📏 **Volume Size** → e.g., increase to **3072 GB (3 TB)**.  
   - ⚡ **Performance Tier** → e.g., set to **Ultra-High Performance**.  
   - 🌍 **Cross-Region Replication** → Enable if required.  
   - 🔒 **Encryption Options** → Choose desired encryption settings.  
6. Click **Create Clone**.

---

## 📦 Where to Find the Clone?
- Unlike backups, **clones do not appear under Block Volume Backups**.  
- Instead, the **clone is created as a Block Volume** directly.  
- ✅ It behaves just like a **regular block volume** and is available for immediate use.

---

## 📍 Availability Domain Consideration
- Clones are always created in the **same Availability Domain** as the source volume.  
- You **cannot choose a different AD** for the clone.  
- Once created, the clone can perform all operations like any other block volume.

---

## ✅ Key Takeaways
- Clones are **direct disk-to-disk copies**.  
- They are created as **regular block volumes**.  
- AD is inherited from the source volume.  
- Fully customizable in size, performance, replication, and encryption.  
© 2025 Oracle University  
Privacy / Do Not Sell My Info • Contact Us • Terms of Use • Cookie Preferences • Ad Choices
