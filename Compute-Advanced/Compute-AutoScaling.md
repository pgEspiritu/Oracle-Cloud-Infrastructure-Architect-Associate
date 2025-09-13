# ⚙️ Compute Autoscaling

## 🧩 Key Constructs

### 📄 Instance Configuration
- A **template** that defines the settings for creating compute instances.  
- Can be used to:
  - Launch individual instances  
  - Create one or more instances in an **instance pool**  
- Does **not** include the contents of any block volumes.  
- To modify → create a **new instance configuration** with desired settings.  

### 🗂️ Instance Pool
- A **group of multiple compute instances** within the same region.  
- Uses **one instance configuration** per pool.  
- You can:
  - Update pool size  
  - Add/remove instances  
  - Attach/detach load balancers  
  - Scale instance count via **metrics** or **schedule**  

🔑 Example:  
- Instance pool target count = **2**  
- Two instances are created and running in the pool.  

---

## 🛠️ Creating an Instance Configuration
- Can be created from:
  - An **existing running instance**  
  - A **set of configuration parameters**  

Includes:  
- OS image  
- Metadata  
- Shape  
- VNICs  
- Storage  
- Subnet info  

Instance configurations can then be used to launch instances in an **instance pool**, which may span multiple availability domains and can be placed behind a **load balancer**.  

---

## 📈 Autoscaling Policies

### 🔹 Metric-Based Autoscaling
- Triggered when a **performance metric** (e.g., CPU/memory utilization) meets or exceeds a threshold.  
- Benefits:
  - Ensures consistent performance during demand spikes  
  - Reduces cost during low usage  

### 🔹 Schedule-Based Autoscaling
- Triggered at **specific times** defined by a schedule.  
- Useful for predictable workloads (e.g., business hours vs. off-hours).  

---

## 📝 Steps to Configure Autoscaling

1️⃣ **Create an Instance Configuration**  
2️⃣ **Create an Instance Pool** from that configuration  
3️⃣ **Configure Instance Pool** (pool size, load balancers, etc.)  
4️⃣ **Define Autoscaling Policies** (metric-based or schedule-based)  

---

## 🏗️ Example Architecture
- Instance pool initial size = **2**  
- Scaling rule:  
  - ➕ Add **2 instances** if CPU/memory utilization > 70%  
  - ➖ Remove **2 instances** if CPU/memory utilization < 70%  
- Minimum size = **1**  
- Maximum size = **4**  

📌 Result:  
- Scale-out → pool grows from 2 → 4 instances  
- Scale-in → pool shrinks from 4 → 2 or 1 instance  

---

## ✅ Summary
- **Instance Configurations** define templates for compute instances.  
- **Instance Pools** allow managing multiple instances as a group.  
- **Autoscaling Policies** can be based on **metrics** or **schedules**.  
- Ensures performance efficiency and cost savings.  

---

© 2025 Oracle University  
Privacy / Do Not Sell My Info | Contact Us | Terms of Use | Cookie Preferences | Ad Choices
