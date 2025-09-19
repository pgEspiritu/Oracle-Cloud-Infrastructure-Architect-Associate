# 📦 OCI Block Volume – Overview  

## 🗂 OCI Storage Services Summary  
OCI offers multiple storage services. In this section, we focus on **Block Storage**, which comes in two main flavors:  

- ⚡ **Local NVMe** – non-persistent but survives reboots, extremely low latency, high-performance.  
- 💽 **Block Volume** – persistent, durable storage with **99.99% annual durability**.  

| Storage Type  | Persistence | Performance | Use Cases |
|---------------|-------------|-------------|-----------|
| Local NVMe    | Non-persistent (survives reboot, not instance termination) | Very high, low latency | Big Data, OLTP, high-performance workloads |
| Block Volume  | Persistent, durable | High | General-purpose storage, scalable workloads |

---

## 🎯 Use Cases for Block Volume  
1. **Persistent Storage**  
   - Retain and migrate data between instances.  
   - Data remains safe even when detached.  

2. **Expand Compute Instance Storage**  
   - Add additional storage capacity on-demand.  

3. **Flexible Scaling**  
   - Terminate instances but keep boot volumes.  
   - Launch new instances with different shapes using the same boot volume.  

---

## 🔑 Block Volume Features  
- 📏 **Size Range**: 50 GB → 32 TB (in 1 GB increments).  
- 📦 **Default Size**: 1 TB.  
- 🔗 **Attachments**: Up to 32 volumes per instance.  
- 🔄 **Replication**: Automatic replication across multiple storage servers with repair mechanisms.  
- 🔒 **Encryption**:  
  - At-rest encryption with **AES-256**.  
  - In-transit encryption option for VM volume attachments.  

---

## ⚡ Local NVMe SSD Devices  
- Available in specific compute shapes (e.g., `BM.DenseIO2.52`).  
- Provide **ultra-low latency, high-performance block storage**.  
- ❗ **No automatic backup, RAID, or durability features** → Customer is responsible for data protection.  

👉 Example: Using `lsblk` command on a DenseIO shape displays 8 NVMe devices:  

---

## ✅ Key Takeaways  
- **Block Volumes** are persistent, durable, and secure with built-in replication & encryption.  
- **Local NVMe** delivers unmatched performance but requires customer-managed durability.  
- Both can be leveraged depending on workload requirements:  
  - 📊 Analytics & OLTP → Local NVMe.  
  - 💼 General workloads & scalable apps → Block Volumes.  
