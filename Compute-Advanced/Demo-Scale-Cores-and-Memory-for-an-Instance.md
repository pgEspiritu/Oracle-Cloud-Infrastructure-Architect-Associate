# ⚡ Compute Vertical Scaling Demo – Scale Cores & Memory

## 🖥️ Starting Point
- Inside **OCI Console**, with a few running instances.  
- Example instance:  
  - **Shape:** `VM.Standard.E4.Flex`  
  - **OCPUs:** `1`  
  - **Memory:** `16 GB`  

---

## 🔧 Steps to Scale

1. **Edit Instance**  
   - Go to the instance → **Edit** → **Edit Shape**.  

2. **Choose a New Shape**  
   - Current series: **AMD**.  
   - Change to **Intel** → `VM.Optimized3.Flex`.  

3. **Adjust Resources**  
   - Set **OCPUs** → `5`  
   - Set **Memory** → `16 GB`  

4. **Save & Reboot**  
   - Confirm reboot (required when scaling while the instance is running).  
   - Instance transitions to **Stopping → Updating → Starting**.  

---

## 📊 Monitoring Progress
- Check **Work Requests** under **Resources**.  
- Operation: `Update Instance`.  
- Monitor **state** and **percentage complete**.  

---

## ✅ Final Result
- Instance shape changed to: **`VM.Optimized3.Flex`**  
- OCPUs scaled **from 1 → 5**  
- Memory scaled → **16 GB**  

---

## ⚠️ Important Notes
- The **shape series** and **image** of the original instance determine which target shapes are available.  
- Scaling requires a **reboot** of the instance.  

---

## 📝 Summary
We successfully scaled an OCI VM instance by:  
- Editing its shape  
- Increasing CPU cores from **1 → 5**  
- Keeping memory at **16 GB**  
- Verifying via **work requests**  

This demonstrates how **vertical scaling** (scale up/down) works in practice.  
