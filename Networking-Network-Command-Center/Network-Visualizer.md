# 🌐 Lesson: Network Visualizer in OCI

## 📌 Introduction
**Network Visualizer** is a service in OCI that helps you **visualize complex virtual networks** with ease.  
As your environment grows with more VCNs, subnets, and gateways, it can become difficult to track overall architecture.  
This is where Network Visualizer provides clarity with interactive topology maps.

---

## 🏗️ Sample Architecture
- Inside an **OCI Region**, multiple **VCNs** exist.  
- Various gateways such as:
  - 🔗 Service Gateway  
  - 🔗 Local Peering Gateway (LPG)  
  - 🔗 Dynamic Routing Gateway (DRG)  
  - 🔗 Remote Peering Connection (RPC)  
  - 🏢 Customer Premises Equipment (CPE) for on-premises connectivity  
- Each VCN contains **subnets** hosting resources like:
  - 🖥️ Virtual Machines  
  - 🗄️ Database Systems  
  - ☁️ Object Storage in the Oracle Services Network  

As environments scale, Network Visualizer makes it easier to explore and troubleshoot these components.

---

## 🔍 Key Features

### 1. **Regional Topology Map**
- High-level layout of the **entire virtual network** in a selected region.  
- Shows **VCNs, DRGs, CPEs, and gateways**.

### 2. **VCN Topology Map**
- View of a **single VCN**, including:  
  - Subnets  
  - Routing configuration  
  - Connected gateways  

### 3. **Subnet Topology Map**
- Detailed view of resources within a subnet:  
  - Instances  
  - Load Balancers  
  - OKE Clusters  
  - Security lists and NSGs  

---

## 💡 Use Cases
- 🔎 **Troubleshoot network security configuration issues**  
  - Understand relationships between **Security Lists / NSGs** and other resources.  
- 📊 **Visualize resource dependencies**  
  - See how subnets, gateways, and routes connect.  
- 🛠️ **Validate DRG and transit routing configurations**  
  - Identify misconfigurations more easily.  
- 🌍 **Enhanced architecture understanding**  
  - Explore the impact of network changes before applying them.

---

## ✅ Summary
- **Network Visualizer** provides interactive topology maps of your OCI network.  
- Helps with **navigation, troubleshooting, and planning**.  
- Supports **regional, VCN, and subnet-level views**.  
- Improves customer experience by simplifying complex network structures.

---

© 2025 Oracle University  
Privacy / Do Not Sell My Info · Contact Us · Terms of Use · Cookie Preferences · Ad Choices
