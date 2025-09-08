# 📦 OCI Compute – Import/Export & Bring Your Own Image (BYOI)

## 📌 Introduction
OCI supports **image import/export** and the ability to **bring your own image (BYOI)**.  
These features allow migration of workloads between environments, replication of custom images across regions, and support for legacy systems.

---

## 🔄 Image Import & Export
You can share **custom images** across **regions** and **tenancies** using OCI Object Storage.

### 🚀 Launch Modes
When importing an image into OCI, three launch modes are supported:

1. **Emulation Mode**  
   - For VMs **without paravirtualized drivers**.  
   - Typically used for **older on-premises physical or virtual machines**.  

2. **Paravirtualized Mode**  
   - For VMs that **support paravirtualized drivers**.  
   - Created outside of OCI but compatible with OCI hypervisors.  

3. **Native Mode**  
   - For images that were **exported from OCI** itself.  
   - Best performance and compatibility.  

---

### 🛠️ Steps to Replicate an Image Across Regions
1. **Export** → Export the image to an **Object Storage bucket** in the same region.  
2. **Copy** → Copy the image to an Object Storage bucket in the **destination region**.  
3. **Get URL** → Obtain the **URL path** to the image object.  
4. **Import** → Import the image into the **destination region**.  

---

## 🖼️ Bring Your Own Image (BYOI)
With BYOI, you can **migrate existing virtual machines** into OCI by importing them as **custom images**.

### ✅ Supported Formats
- `qcow2` (QEMU Copy-On-Write v2)  
- `VMDK` (VMware Virtual Disk)  

### ⚡ Key Benefits
- Enables **VM cloud migration projects**.  
- Supports both **old and new operating systems**.  
- Increases **infrastructure flexibility**.  
- Encourages **testing and experimentation**.  

⚠️ **Note:** You must comply with all **licensing requirements** when importing images.  

---

## ✅ Summary
- **Image Import/Export** allows sharing custom images across **regions** and **tenancies** via Object Storage.  
- OCI supports **Emulation, Paravirtualized, and Native modes** for different VM origins.  
- **BYOI** enables you to migrate VMs from other environments using `qcow2` or `VMDK` formats.  
- Provides flexibility for **migration, testing, and compliance** scenarios.  

---

© 2025 Oracle University  
Privacy / Do Not Sell My Info · Contact Us · Terms of Use · Cookie Preferences · Ad Choices
