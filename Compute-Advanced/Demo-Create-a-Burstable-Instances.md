# 🖥️ Demo: Create a Burstable Instance

In this demonstration, we will create a **burstable instance** in OCI.  
A burstable instance is a VM that provides a **baseline level of CPU performance**, with the ability to **burst higher** to support occasional spikes.

---

## 🔑 Steps to Create a Burstable Instance

### 1. Navigate to Compute
- Log in to the **OCI Console** as a user with Compute privileges.  
- Go to **Compute → Instances**.  
- Click **Create Instance**.  

---

### 2. Configure Basic Details
- **Name**: `burstable-instance-demo`  
- **Compartment**: Select the desired compartment.  
- **Placement**: Choose an availability domain.  
- **Image**: Use the default (e.g., **Oracle Linux 8**).  

---

### 3. Select a Burstable Shape
1. Click **Change Shape**.  
2. Available shapes that support burstable mode include:
   - `VM.Standard3.Flex` (Intel)  
   - `VM.Standard.E3.Flex` (Previous Gen)  
   - `VM.Standard.E4.Flex` (AMD)  

> ⚠️ Note: Not all shapes support bursting.  
   For example, `VM.Optimized3.Flex` allows OCPU and memory selection but **does not support burstable mode**.

---

### 4. Enable Burstable Mode
- Select `VM.Standard3.Flex`.  
- Configure:
  - **OCPUs**: e.g., `1`.  
  - **Memory**: Default value.  
  - **Burstable Option**: ✅ Enable.  
  - **Baseline Utilization**: Choose **12.5%** or **50%** per OCPU.  

💡 Example:  
- **1 OCPU** with a **12.5% baseline** → The instance always has 12.5% CPU available, but can burst to 100% if resources are available.  

---

### 5. Create the Instance
- Click **Select Shape**.  
- Review other settings (networking, boot volume, etc.).  
- Click **Create**.  

The instance will enter **Provisioning** state and then become **Available**.

---

## 🔍 Verifying Configuration
- Open the instance details page.  
- Under **Shape Configuration**, confirm:
  - Shape name (`VM.Standard3.Flex`).  
  - OCPU count (e.g., `1`).  
  - Burstable baseline (e.g., `12.5%`).  

---

## ⚙️ How It Works
- If the **average CPU utilization** of the instance over the past **24 hours** is **below the baseline**, the system will allow bursting up to the total OCPUs.  
- Example: `1 OCPU` @ `12.5% baseline` → guaranteed 12.5% but can burst to 100%.  
- **Bursting is not guaranteed** if the physical host is oversubscribed.  

---

## 💰 Pricing Notes
- Burstable instances are billed based on the **baseline OCPUs only**.  
- Bursting **does not increase the cost**.  
- This makes them **cheaper** than regular instances with the same OCPU count.  

---

## ✅ Demo Recap
- Navigated to Compute → Instances.  
- Selected a **burstable-supported shape**.  
- Configured **OCPUs**, enabled **burstable mode**, and set a **baseline**.  
- Created and verified the instance.  
