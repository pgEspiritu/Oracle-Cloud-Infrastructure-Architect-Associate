# 🧪 Demonstration: Virtual Test Access Points (VTAP)

## 📌 Introduction
This demo walks through how to create, start, and stop a **Virtual Test Access Point (VTAP)** in the Oracle Cloud Infrastructure (OCI) Console.  
A VTAP mirrors traffic from a **source** (e.g., VNIC, DB System) to a **target** (Network Load Balancer) for analysis and monitoring.

---

## 🚀 Steps to Create a VTAP

### 1. Navigate to VTAPs
- In the **OCI Console**, open the **Navigation menu**.  
- Click **Networking** → **Network Command Center** → **VTAPs**.  

---

### 2. Create a VTAP
1. Click **Create VTAP**.  
2. Enter a **Name** (e.g., `vtapdemo`).  
3. Select the **Compartment** and **VCN**.  

---

### 3. Define the Source
- Supported **source types**:  
  - DB System  
  - Exadata VM Cluster  
  - Instance VNIC  
  - Load Balancer  
  - Autonomous Data Warehouse  

👉 For this demo, select **Instance VNIC**:  
- Choose the **Subnet**.  
- Choose the **VNIC** of the source instance.  

---

### 4. Define the Target
- Target must be a **Network Load Balancer (NLB)**.  
- Select an existing NLB to receive mirrored traffic.  

---

### 5. Associate a Capture Filter
- A **Capture Filter** defines which traffic will be mirrored.  
- Select an existing capture filter.  
- (Optional) Under **Advanced Options**, configure:
  - **VXLAN Network Identifier** (auto-generated if not provided).  
  - **Maximum Packet Size**.  
  - **Priority Mode** → gives mirrored traffic the same priority as production traffic.  

Click **Create VTAP**.  

---

## ▶️ Starting and Stopping the VTAP

- **Default Status:** Newly created VTAPs are in a **Stopped** state.  
- **Start VTAP:**  
  - Select your VTAP (`vtapdemo`).  
  - Click **Start** → traffic from the source is now mirrored to the NLB target.  
- **Stop VTAP:**  
  - Select the VTAP.  
  - Click **Stop** → mirroring is suspended.  

---

## ⚡ Key Notes
- **Source Options:** Multiple OCI resources can act as VTAP sources.  
- **Target Requirement:** Must be a **Network Load Balancer** in the same VCN.  
- **Capture Filter:** Defines what traffic is mirrored.  
- **Priority Mode:** Optional, treats mirrored traffic at the same priority as production traffic.  

---

## ✅ Summary
- VTAP mirrors traffic from a chosen source to a target NLB.  
- Requires an associated **Capture Filter**.  
- Supports start/stop lifecycle for controlling mirroring.  
- Useful for monitoring, troubleshooting, and security analysis.  

---
