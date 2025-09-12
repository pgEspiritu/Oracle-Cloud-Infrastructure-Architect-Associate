# ⚡ Lesson: Preemptible Instances  

## 🔎 What are Preemptible Instances?  
- Similar to **on-demand instances** with one key difference:  
  - OCI can **terminate** preemptible instances if compute capacity is needed elsewhere  
- Run on unused on-demand capacity  
- 💰 **50% cheaper** compared to on-demand instances  
- Designed for **short-term usage**, not suitable for long-running workloads  

---

## ⚙️ Characteristics  
- You can **only change the instance name** after launch  
- ❌ Cannot change the shape after launch  
- ❌ Cannot convert preemptible → on-demand instance  
- ❌ Not supported for bare metal instances  
- ❌ Cannot be used in **instance configurations**  
- ❌ Cannot be used in **instance pools**  
- Pricing: **Always 50% cheaper** than on-demand  

---

## ⚠️ Termination Rules  
- OCI can reclaim capacity anytime if demand for on-demand instances increases  
- **Event Service** sends a termination notice  
- ⏳ Notice is given **30 seconds before termination**  

---

## 💡 Use Cases  
- Batch jobs (e.g., video encoding, image processing)  
- Workloads that can tolerate interruption  

---

## 🚀 How to Create a Preemptible Instance  
1. In the **OCI Console**, go to **Create Instance**  
2. Under **Placement → Capacity Type**, select **Preemptible Capacity**  
3. Configure other settings as usual  
4. Launch the instance  

---

## 🎯 Summary  
- Preemptible instances = discounted, short-term compute  
- **50% cheaper** but can be **terminated anytime**  
- Not suitable for critical or persistent workloads  
- Best for **fault-tolerant, interruptible jobs**  

---
