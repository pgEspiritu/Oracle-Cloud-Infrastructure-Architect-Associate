# 🖥️ OCI Compute – Shapes

## 📌 Introduction
A **shape** in Oracle Cloud Infrastructure (OCI) is a **template** that defines:
- Number of **OCPUs** (Oracle CPUs)
- Amount of **memory**
- Other resources (network bandwidth, vNICs, etc.) allocated to an instance  

Shapes are available with:
- **AMD processors**
- **Intel processors**
- **ARM-based processors**

---

## 🏷️ Types of Shapes
### 1. **Fixed Shapes**
- Predefined configuration of OCPUs and memory  
- Cannot be customized  
- Available for:
  - **Bare Metal instances**
  - **Virtual Machine (VM) instances**

---

### 2. **Flexible Shapes**
- Allows customization of **OCPUs** and **memory**  
- Available **only for Virtual Machine instances**  
- Network bandwidth and number of vNICs **scale proportionally** with OCPUs  

#### Example:  
- **VM.Standard.E3.Flex** or **VM.Standard3.Flex**  
- You can:
  - Choose **1–32 OCPUs**  
  - Allocate up to **64 GB of memory per OCPU**  
- If you select **4 OCPUs**, the maximum memory = **4 × 64 GB = 256 GB**  

---

## ⚡ Benefits of Flexible Shapes
- Build **VMs tailored to workload requirements**  
- **Optimize performance** while **minimizing cost**  
- Scale **CPU, memory, and network** as needed  

---

## ✅ Summary
- **Fixed shapes**: Predefined, used for Bare Metal and VMs.  
- **Flexible shapes**: Customizable, available only for VMs, with scalable bandwidth and vNICs.  
- Flexible shapes help achieve a balance between **performance and cost efficiency**.  
