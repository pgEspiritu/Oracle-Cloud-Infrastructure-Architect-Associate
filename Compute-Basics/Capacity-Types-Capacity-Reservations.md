# 🗂️ Lesson: Capacity Reservations  

## 📖 What is a Capacity Reservation?  
- A way to **reserve compute capacity in advance** and use it later when creating instances.  
- When reserved-capacity instances are **terminated**, the capacity returns to the reservation.  
- Provides **assurance** that you have enough resources for your workloads.  

### 💡 Key Features  
- No **size or time constraints** → reserve as little or as much as needed.  
- Can be **deleted anytime** to stop charges.  
- **Charges still apply** even if unused:  
  - 💤 Unused reserved capacity → billed at **85%**.  
  - ⚡ Instances launched from reservation → billed at **100%**.  

---

## 🛠️ Example Use Cases  
- Large capacity needs for **migrations** or **new project launches**.  
- Ensures **capacity availability** for **failover scenarios**.  
- Handles **maintenance** or **seasonal spikes** in usage.  
- Acts as a **buffer** for unexpected workload surges.  

---

## 📌 Support & Limitations  

- ✅ Must specify an **Availability Domain (AD)** at creation.  
- 🚫 Cannot be **shared** between ADs.  
- 🚫 Cannot be **moved** between ADs or tenancies.  
- 🚫 Not supported with **Dedicated VM Hosts**.  
- ✅ Capacity is **allocated immediately** when the reservation is created.  
  - If full capacity is unavailable, OCI creates as many as possible.  
  - Example: request 20 instances → only 10 available → reservation created with 10.  
- ✅ Shape is **fixed** → only the shape defined in the reservation config is allowed.  

---

## 📊 Example Configuration (Conceptual)  
- **Availability Domain**: `AD1`  
- **Reserved Shape**: `VM.Standard.E3.Flex`  
- **Reserved Count**: 1 instance  
- **Used Capacity**: 0  

---

## ✅ Summary  
Capacity reservations in OCI:  
- Guarantee compute availability.  
- Are billed whether or not fully used.  
- Provide resilience during migrations, failovers, and workload spikes.  
- Must be carefully planned because they are limited by AD, tenancy, and shape.  

---
