# 🖼️ OCI Compute – Platform & Custom Images

## 📌 Introduction
When creating a compute instance in OCI, you must specify both:
- **Shape** → Defines the compute resources (CPU, memory, etc.)  
- **Image** → Defines the operating system and software stack  

An **image** can be thought of as a **template of a virtual hard drive**.

---

## 📂 Image Sources
OCI provides several options for instance images:

1. **Platform Images**  
   - Pre-built operating systems for Oracle Cloud Infrastructure  
   - Examples:  
     - Oracle Linux  
     - Ubuntu  
     - CentOS  
     - Microsoft Windows  
     - Oracle Autonomous Linux  

2. **Oracle Images**  
   - Oracle Enterprise images and solutions optimized for OCI.  

3. **Custom Images**  
   - Created from **existing running instances** in OCI.  
   - Includes **customization, configuration, and installed software**.  
   - Instance is **temporarily stopped** during image creation.  

4. **Partner Images**  
   - Trusted **third-party images** published in the **OCI Marketplace** by Oracle partners.  

5. **Bring Your Own Image (BYOI)**  
   - Import your own OS images into OCI.  
   - Limitations:  
     - Max image size = **400 GB**  
     - Hardware compatibility required  

---

## 🛠️ Custom Images in Detail
- **Creation Process:**  
  - OCI stops the instance temporarily.  
  - Creates an image snapshot.  
  - Restarts the instance automatically.  

- **Windows Custom Images:**  
  - **Generalized**: Cleaned of instance-specific data (ideal for reuse).  
  - **Specialized**: Snapshot of a disk at a given point (ideal for backups).  

---

## ✅ Summary
- Images determine the **OS and software stack** for compute instances.  
- OCI supports **platform, Oracle, partner, and custom images**.  
- You can also **bring your own image (BYOI)** with some size and compatibility constraints.  
- Custom images allow you to **capture and reuse configurations** across instances.  
