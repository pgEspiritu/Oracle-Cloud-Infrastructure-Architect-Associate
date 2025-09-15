# 🛡️ Lesson: Shielded Instances in OCI

## 🔒 What Are Shielded Instances?
- Protect **VMs** and **Bare Metal instances** against **kernel-level threats** (Rootkits, Bootkits).  
- Deployment is simple: follow the **standard instance deployment flow**.  
- Supported images/shapes show a **shield icon 🛡️**.  
- In **Advanced Options**, you can enable:
  - ✅ **Secure Boot**  
  - ✅ **Measured Boot** (enables **TPM** automatically for VMs)  

💡 **No additional charge** — these security features are included with OCI.

---

## 🧩 Core Features of Shielded Instances

### 1. 🔐 Secure Boot
- A **UEFI feature** that prevents unauthorized bootloaders/OS from starting.  
- Ensures only **properly signed components** can run.  
- Protects against malicious or tampered boot code.  

---

### 2. 📏 Measured Boot
- **Enhances Secure Boot** by recording measurements of boot components:
  - Bootloaders  
  - Drivers  
  - Operating systems  
- Verifies that measurements remain unchanged between boots.  
- Available **only on VM instances**.  

---

### 3. 🧮 Trusted Platform Module (TPM)
- A **specialized security chip** used by Measured Boot.  
- Securely stores boot measurements.  
- Enabled automatically when **Measured Boot** is selected.  
- Stores data in **Platform Configuration Registers (PCRs)**:
  - PCRs are memory locations holding values that summarize measurement results.  

---

## 🎯 Summary
- Shielded Instances = **Secure Boot + Measured Boot + TPM**  
- ✅ **Secure Boot** → Blocks unauthorized boot code  
- ✅ **Measured Boot** → Records & verifies boot components  
- ✅ **TPM** → Stores measurements securely in PCRs  

Together, these features protect OCI instances against **firmware and OS-level attacks**.
