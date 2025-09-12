# 💡 Lesson: Burstable Instances

## 🔎 What are Burstable Instances?
A **burstable instance** is a virtual machine instance that:
- Provides a **baseline level of CPU performance**.
- Can **burst to higher levels** when workloads spike.
- Is designed for workloads that are mostly idle or low-CPU, with occasional bursts.

---

## 💰 Cost Model
- Burstable instances **cost less** than regular instances with the same OCPU count.  
- Charges are based on the **baseline OCPU**, not the peak.  
- Example: If baseline = 12.5%, you pay for that fraction, even if the instance bursts.  

---

## ⚙️ How Bursting Works
- **CPU only** can burst (memory does not).  
- Bursting is allowed if:
  - The instance’s **average CPU utilization** over the last **24 hours** is below its baseline.  
- **No guarantee of bursting** if the physical VM host is oversubscribed.  

---

## 🛠️ Supported Shapes
Not all shapes support burstable instances. Examples include:
- `VM.Standard3.Flex`  
- `VM.Standard.E3.Flex`  
- `VM.Standard.F4.Flex`  

---

## 📐 Configuration
When creating a burstable instance:
1. Select a **supported shape**.  
2. Specify the **number of OCPUs** (maximum available).  
3. Enable the **burstable option**.  
4. Set the **baseline CPU utilization**:
   - **12.5%** (1/8 of each OCPU)  
   - **50%** (half of each OCPU)  

---

## 🧑‍💻 Use Cases
Burstable instances are ideal for workloads that run light most of the time but occasionally need more compute:
- Microservices  
- Development & test environments  
- CI/CD tools  
- Static websites  
- Monitoring systems  

---

## 💵 Pricing Model Recap
- **Always billed at baseline OCPU rate**.  
- Bursting above the baseline does **not** incur extra charges.  

---

## ✅ Summary
- Burstable instances provide **low-cost compute** with occasional burst capability.  
- Best suited for workloads with **predictable low CPU utilization** and occasional spikes.  
- You configure OCPUs, enable bursting, and select a baseline (12.5% or 50%).  
