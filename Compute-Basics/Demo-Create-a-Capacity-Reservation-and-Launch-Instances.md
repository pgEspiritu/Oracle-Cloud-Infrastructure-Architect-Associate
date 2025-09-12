# 💻 Demonstration: Working with Capacity Reservations  

This demo shows how to **create, configure, and manage capacity reservations** in Oracle Cloud Infrastructure (OCI).  

---

## 🔑 Prerequisites  
Before creating a capacity reservation, ensure proper IAM policies are in place. Example:  

```hcl
Allow group computeadmins to use compute-capacity-reservations in tenancy
Allow group computeadmins to manage compute-capacity-reservations in tenancy
```

---


## 📝 Steps

### 1️⃣ Navigate to Capacity Reservations
- Log in as **computeadmin**.  
- Go to: `☰ Hamburger Menu → Compute → Capacity Reservations`.

---

### 2️⃣ Create a Reservation
- **Name**: `ocicapacityreservation`  
- **Compartment**: `archassociate-compartment`  
- **Availability Domain**: `AD-1`  
- (Optional) **Set as default reservation** → requires **root compartment**.  

➡️ Default reservation ensures all compatible instances in `AD-1` use this capacity.

---

### 3️⃣ Add Capacity Configurations
**Config 1**  
- Fault Domain: `default`  
- Shape: `VM.Standard1.1`  
- Count: `3`  

**Config 2**  
- Fault Domain: `FD-1`  
- Shape: `VM.Standard.E4.Flex`  
- Count: `2`  

✅ Review and **Create** → Reservation becomes **Active**.

---

### 4️⃣ Verify Reserved vs Used Capacity
- Reserved:  
  - `VM.Standard1.1 = 3`  
  - `VM.Standard.E4.Flex = 2`  
- Used: `0` (initially)

---

### 5️⃣ Launch Instance with Reservation
1. Go to **Instances → Create Instance**.  
2. Under **Placement → Show Advanced Options → Select Capacity Reservation**.  
3. Shape: `VM.Standard1.1` (matches reserved config).  
4. Launch (SSH keys optional).  

➡️ Instance provisions using the **capacity reservation**.  
➡️ Used capacity updates:  
   - `VM.Standard1.1 = 1`.

---

### 6️⃣ Edit Capacity Configuration
⚠️ **Cannot** change fault domain or shape.  
✅ **Can** update count:  
- Example: reduce **3 → 2** → Reserved = 2, Used = 1.  
- Example: increase **2 → 4** → Reserved = 4, Used = 1.  

---

### 7️⃣ Add Additional Configurations
- Fault Domain: `FD-1`  
- Shape: `VM.Standard2.1`  
- Count: `2`  

➡️ New entry added under **Capacity Configurations**.

---

### 8️⃣ Move Instances In/Out of Reservation
**To move OUT**:  
- Edit instance → Placement → Remove reservation → Save.  
- Used capacity = `0`, Instance type = **On-demand**.  

**To move IN**:  
- Edit instance → Placement → Apply reservation → Save.  
- Used capacity updates accordingly.  

---

## ✅ Summary
- Capacity reservations ensure **guaranteed compute availability**.  
- You can **add, edit, or move instances** across reservations.  
- **IAM policies** must allow reservation management.  
- **Reserved vs Used capacity** updates in real-time.  
