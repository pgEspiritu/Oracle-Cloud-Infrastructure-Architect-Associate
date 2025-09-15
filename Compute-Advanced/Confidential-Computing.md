# 🔒 Confidential Computing

## 📖 Introduction
Before **Confidential Computing**, all data running in memory was accessible as clear text.  
With the arrival of confidential computing, data can now be **encrypted while running in memory**, not just at rest or in transit.

---

## 🛡️ What is Confidential Computing?
- Protects **data in use** at the hardware level.  
- Both **data** and the **application processing it** are encrypted and isolated.  
- Prevents unauthorized access or modification of:
  - The data  
  - The application  

🔑 **Minimizes trusted parties** (OS, ecosystem partners, administrators), reducing risk of data exposure.

---

## ⚙️ How It Works in OCI
- Powered by **AMD EPYC processors** with AMD Infinity Guard features:
  - 🔐 **SEV (Secure Encrypted Virtualization)** → for confidential VMs  
  - 🔐 **SME (Secure Memory Encryption)** → for confidential bare metal servers  

- Available on **E3 and E4 compute shapes** using 2nd & 3rd gen AMD EPYC processors.  

---

## 🖥️ Supported Compute Shapes

### Virtual Machines
- `VM.Standard.E4.Flex`  
- `VM.Standard.E3.Flex`  
✅ Supported on **Oracle Linux 7.x and 8.x** platform images.

### Bare Metal
- `BM.DenseIO.E4.128`  
- `BM.Standard.E4.128`  
- `BM.Standard.E3.128`  
✅ Supported on **any platform image**.

---

## 🌟 Benefits of Confidential Computing
- 🔐 **Improved Isolation**: Real-time encryption for data and applications.  
- 🔑 **Per-VM Encryption Keys**:  
  - Generated at VM creation.  
  - Reside only in the **AMD Secure Processor** inside the CPU.  
  - Inaccessible to apps, hypervisors, or even OCI.  
- ⚡ **No Application Changes Required**: Works transparently with existing workloads.  
- 🚀 **Minimal Performance Impact**: Nearly identical performance with encryption enabled.

---

## ✅ Summary
Confidential computing takes encryption to the next level by:  
- Protecting **data in memory**.  
- Using **hardware-based isolation**.  
- Delivering **security without performance trade-offs**.  
