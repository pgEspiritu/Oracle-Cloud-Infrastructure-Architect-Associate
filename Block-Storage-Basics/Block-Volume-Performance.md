# ⚡ OCI Lesson – Block Volume Performance

## 🚀 Overview
The **Block Volume service** in OCI uses **NVMe-based storage infrastructure**, designed for:
- Consistency  
- Flexibility  
- Elastic performance  

When creating a volume:
- Default = **Balanced** performance level ⚖️  
- You can adjust performance at creation time or update later.  
- Control is available via **slider** or **Volume Performance Unit (VPU) control**.  

---

## 📊 Performance Levels

### 1️⃣ Lower Cost 💰
- **IOPS**: 2 IOPS per GB (max 3,000 IOPS/volume)  
- **Throughput**: 240 KB/s per GB (max 480 MB/s/volume)  
- **Pricing**: Only storage cost (❌ no VPU cost)  
- **Availability**: Block volumes only (not boot volumes)  
- **Use cases**:  
  - Streaming  
  - Log processing  
  - Data warehouses  

---

### 2️⃣ Balanced ⚖️ *(Default)*
- **IOPS**: 60 IOPS per GB (max 25,000 IOPS/volume)  
- **Throughput**: 480 KB/s per GB (max 480 MB/s/volume)  
- **Pricing**: 10 VPUs/GB/month  
- **Availability**: Block & boot volumes  
- **Use cases**: General-purpose workloads (best cost-performance balance)  

---

### 3️⃣ Higher Performance ⚡
- **IOPS**: 75 IOPS per GB (max 50,000 IOPS/volume)  
- **Throughput**: 600 KB/s per GB (max 680 MB/s/volume)  
- **Pricing**: 20 VPUs/GB/month  
- **Availability**: Block & boot volumes  
- **Use cases**:  
  - High I/O workloads  
  - Databases with demanding transactions  

---

### 4️⃣ Ultra High Performance 🚀
- **IOPS**: 225 IOPS per GB (range 90–225 IOPS/GB)  
- **Throughput**: 1,800 KB/s per GB (max 2,680 MB/s/volume)  
- **Pricing**: 30–120 VPUs/GB/month  
- **Availability**: Block volumes only  
- **Use cases**:  
  - Extreme I/O workloads  
  - Large databases  
  - High-frequency trading systems  

---

## ✅ Key Takeaways
- **Balanced** is default and suitable for most workloads.  
- **Lower Cost** offers budget-friendly throughput, but only for block volumes.  
- **Higher Performance** is for demanding but not extreme workloads.  
- **Ultra High Performance** is the **top tier** for mission-critical, I/O-heavy workloads.  
