# 🌍 Inter-Region Latency Overview

## 📖 What is the OCI Backbone Network?
- The **OCI Backbone Network** is Oracle’s **global private IP network**.  
- It is used when workloads in Oracle Cloud communicate **between different regions**.  
- The **Inter-Region Latency Dashboard** reflects the traffic flowing through this backbone.

---

## 📊 Inter-Region Latency Dashboard
- Displays **average inter-region round-trip latency** for all pairs of regions in an OCI realm.  
- ❗ Not available in realms with only **one region**.  
- Latency data is **not specific to your tenancy’s workloads**, but reflects average backbone performance.  

---

## 📈 Dashboard Views

### 1. ⏱️ Current Inter-Region Round-Trip Time
- Real-time snapshot (in **milliseconds**)  
- Average of values over the **last 5 minutes**  
- Updated **every minute**  
- Example: From **Frankfurt → Ashburn (US East)**, latency ≈ **97.24 ms**

### 2. 📉 Historical Inter-Region Round-Trip Time
- Historical view over the **last 30 days**  
- Select **source** and **destination regions**  
- Used for **validating long-term network performance**

---

## 🛠️ Use Cases

### 🌐 Network Planning
- Helps determine performance impact of regional selections  
- Supports decisions for:  
  - Disaster recovery  
  - Compliance  
  - Data residency  
  - Performance optimization  

### 🕵️ Troubleshooting
- Validate **real-time** and **historical** performance  
- Diagnose latency-related issues  

### 🔔 Monitoring & Alerts
- Latency metrics are available via the **Monitoring API**  
- Can be integrated into **on-prem monitoring platforms**  
- Trigger **alerts** when latency thresholds are exceeded  

---

## ✅ Summary
- The **Inter-Region Latency Dashboard** provides visibility into OCI backbone performance.  
- Two main views:  
  - ⏱️ Current round-trip time (5-min averages, real-time)  
  - 📉 Historical round-trip time (30-day view)  
- Supports **network planning, troubleshooting, and proactive monitoring**.
