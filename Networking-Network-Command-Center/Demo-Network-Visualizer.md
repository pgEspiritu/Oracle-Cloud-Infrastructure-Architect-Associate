# 🎥 Demonstration: Network Visualizer in OCI

## 📌 Introduction
In this demo, we’ll explore how to use **Network Visualizer** inside the **OCI Console** to view and analyze your cloud network topology.  

---

## 🖥️ Step 1: Accessing Network Visualizer
1. Open the **OCI Console**.  
2. Click on the **Navigation Menu**.  
3. Select **Networking → Network Command Center → Network Visualizer**.  

👉 The first time you open it, the **Regional Routing Map** will automatically load.

---

## 🗺️ Step 2: Exploring the Regional Routing Map
- You can **change the compartment** or **include child compartments**.  
- A **search bar** is available to find specific resources on the map.  
- Use the **Map Legend** to identify icons:  
  - 🌍 **OCI Region**  
  - 🕸️ **VCN**  
  - 🔗 **Dynamic Routing Gateway (DRG)**  
  - 🔗 **Service / Internet / Local Peering Gateways**  

📊 Example: In this demo, two VCNs (`testvcn` and `npademovcn`) are attached to the **Dynamic Routing Gateway**.

---

## 🔍 Step 3: Drilling Down into a VCN
- Click on a **VCN** in the map.  
- You’ll see:  
  - **Resource Summary** (name, state, details)  
  - **Resource Maps** → Switch between **VCN Routing Map** and **VCN Security Map**  

### 🛣️ VCN Routing Map
- Shows routing configuration (e.g., **routes to Internet Gateway**, **DRG attachments**).  
- Provides a clear diagram of how traffic flows.

---

## 🧩 Step 4: Exploring Subnet Details
- Click on a **Subnet** within the VCN.  
- Under **Resource Maps**, choose:  
  - **Subnet Inventory Map** → Displays instances, load balancers, and other resources.  
  - **Subnet Security Map** → Shows **security lists** or **NSGs** and their enforced rules.  

📌 Example:  
- The demo subnet `npademosubnet` shows a running compute instance.  
- Security view shows it is associated with the **default security list**, displaying its ingress/egress rules.

---

## ⚡ Step 5: Creating Path Analysis from Network Visualizer
- Directly from the subnet or instance view, you can create a **Path Analysis**.  
- Choose **Source** or **Destination**, and link it with **Network Path Analyzer** for connectivity validation.  

---

## ✅ Summary
- **Network Visualizer** provides interactive **Regional, VCN, and Subnet topology maps**.  
- Helps you:  
  - 🔎 Troubleshoot misconfigurations  
  - 🗺️ Understand dependencies and relationships  
  - 📊 Visualize routing and security rules in context  
- Essential for designing and validating complex OCI network architectures.
