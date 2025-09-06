# 📘 Lesson: Virtual Test Access Points (VTAP)

## 📌 Introduction
A **Virtual Test Access Point (VTAP)** provides a way to **mirror traffic** from a designated source to a selected target.  
It is useful for:
- Troubleshooting
- Security analysis
- Data monitoring

If multiple VTAPs have overlapping source configurations, traffic from the **more specific source** will be mirrored.

---

## 🧩 Key Components of VTAP
A VTAP consists of three main parts:

1. **VTAP Source**  
   - The resource that the VTAP monitors.  
   - Supported sources include:  
     - Compute instance VNICs  
     - Load balancers  
     - Database systems  
     - Exadata VM clusters  
     - Autonomous Databases  

2. **VTAP Target**  
   - The destination that receives mirrored traffic.  
   - Must be a **Network Load Balancer (NLB)** with a **UDP listener on port 4789**.  
   - Must be in the **same VCN** as the VTAP source.  
   - The backend set performs analysis on the mirrored traffic.  

3. **Capture Filter**  
   - Rules that define what traffic is mirrored.  
   - Examples: source/destination CIDR, protocols, ports, ingress/egress direction.  

---

## 🔄 How VTAP Works (Example)
- A **VM in Subnet A** sends traffic to another **VM in Subnet B**.  
- A **VTAP in Subnet A** checks traffic leaving the first VM.  
- If the traffic matches the **capture filter**, the VTAP mirrors it to the target (e.g., an NLB in Subnet C).  
- The backend servers behind the NLB analyze the mirrored traffic.  

👉 Mirrored traffic is encapsulated in **VXLAN** and sent to the VTAP target over **UDP port 4789**.  

---

## 🎯 Use Cases of VTAP
- **Deep packet inspection** → Detect anomalous behavior.  
- **Compliance monitoring** → Log and monitor traffic as mandated.  
- **Troubleshooting** → Identify issues impacting application performance.  

---

## ✅ Summary
- VTAP enables **traffic mirroring** for monitoring and analysis.  
- Core components: **Source, Target, Capture Filter**.  
- Target must be an **NLB with UDP listener on port 4789** in the same VCN.  
- Supports security, compliance, and troubleshooting scenarios.  

---

© 2025 Oracle University  
Privacy / Do Not Sell My Info · Contact Us · Terms of Use · Cookie Preferences · Ad Choices
