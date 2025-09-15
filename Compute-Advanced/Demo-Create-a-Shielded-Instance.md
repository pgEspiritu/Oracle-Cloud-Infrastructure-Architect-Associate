# 🛡️ Demonstration: Creating a Shielded Instance in OCI

## 🖥️ Step 1: Launch Instance
- Go to **OCI Console** → **Create Instance**.  
- Name the instance: `demoinstance-shielded`.  
- Choose the **compartment** where it will be created.  
- Under **Placement**:
  - Select an **Availability Domain**.  
  - Keep **Capacity Type** = On-Demand.  

---

## 📦 Step 2: Select Image & Shape
- **Image**:  
  - Click **Change Image**.  
  - Look for images marked with a **🛡️ shield icon**.  
  - Example: `Oracle Linux 8` (supports Shielded Instances).  

- **Shape**:  
  - Choose a shape that supports shielded instances (**look for the shield icon 🛡️**).  
  - Example: `VM.Standard2.1`.  

✅ Both Image & Shape must support **Shielded Instances**.

---

## ⚙️ Step 3: Configure Advanced Options
- Expand **Show Advanced Options**.  
- Enable:
  - 🔐 **Secure Boot**  
  - 📏 **Measured Boot** (available only for VMs)  
    - Automatically enables **TPM** (Trusted Platform Module).  

- Keep networking as needed (e.g., use an existing VCN).  
- SSH keys (optional).  

Click **Create**.

---

## 🚀 Step 4: Verify Shielded Instance
- Once provisioning completes, confirm the instance is **Shielded**.  
- Go to **Instance → Shielded Instance tab**.  

### 🧾 PCR Values
- **PCR (Platform Configuration Register)** = memory in TPM storing boot measurements.  
- Click **Copy PCR Values** to save them.  

---

## 🔄 Step 5: Reset Golden Measurements
- After OS updates or changes:
  - Go to **Shielded Instance tab** → **Reset Golden Measurements**.  
  - Confirms: replace baseline values with new ones.  
  - ✅ Golden measurements updated.  

---

## 🎯 Summary
In this demo, we:  
1. Created a shielded instance with supported **image + shape**.  
2. Enabled **Secure Boot, Measured Boot, and TPM**.  
3. Verified **PCR values**.  
4. Learned how to **reset golden measurements**.  

Shielded instances provide strong protection against **rootkits and bootkits** by validating integrity at boot.
