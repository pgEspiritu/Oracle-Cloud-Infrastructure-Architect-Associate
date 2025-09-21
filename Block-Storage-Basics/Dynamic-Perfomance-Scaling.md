# 🔄 OCI Lesson – Block Volume Dynamic Performance Scaling

## 🚀 Overview
OCI **Block Volume** provides **dynamic performance scaling with autotuning**.  
This feature automatically adjusts performance levels to optimize workloads.  

There are **two types** of autotuning:  

1. **⚡ Performance-Based Autotuning**  
   - Adjusts performance dynamically **between default and maximum levels**.  
   - Uses monitored performance metrics to decide scaling.  

2. **🔌 Detached-Volume Autotuning**  
   - When volume is **detached**, performance level drops to **Lower Cost (0 VPUs/GB)**.  
   - When **reattached**, it restores to the previous default setting.  

---

## ⚡ Performance-Based Autotuning
- You configure:  
  - **Default VPUs per GB** (minimum guaranteed performance).  
  - **Maximum VPUs per GB** (upper limit).  
- Rules:  
  - Default VPUs/GB cannot be **0** or **120**.  
  - Maximum VPUs/GB must be **≥ 10 higher** than default.  

### 📊 Key Metrics Used
- **Volume Throttled Operations** → # of I/O operations throttled.  
- **Volume Guaranteed VPUs per GB** → Baseline performance units.  
- **Volume Guaranteed IOPS** → Minimum IOPS guaranteed.  
- **Volume Guaranteed Throughput** → Minimum throughput guaranteed.  

The service monitors these metrics and scales performance up/down automatically.

---

## 🔌 Detached-Volume Autotuning
- When **enabled**:  
  - **Detached volumes** → Performance scales down to **Lower Cost (0 VPUs/GB)**.  
  - **Reattached volumes** → Performance scales back up to the **default VPUs/GB** setting.  
- If **Performance-Based Autotuning** is also enabled, scaling continues dynamically after reattachment.  

---

## ✅ Key Takeaways
- **Performance-Based Autotuning** → Dynamically scales based on workload demand.  
- **Detached-Volume Autotuning** → Saves cost when volumes are not in use.  
- Both features can be **combined** for maximum efficiency and flexibility.  
