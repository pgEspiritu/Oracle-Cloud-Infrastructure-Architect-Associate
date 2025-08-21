# Demonstration: Site-to-Site VPN (Part 1)

## 🔹 Scenario Setup

We will work with **two OCI regions**:

- **Ashburn** → Simulating **On-Premises Network**  
- **Phoenix** → OCI side with **VCN + DRG + CPE + VM**

---

## 🔹 Ashburn Region (On-Prem Simulation)

### 1. Create VCN
- Name: `onpremnetwork`  
- Wizard: **VCN with Internet Connectivity**  
- Includes:
  - **Private subnet**
  - **Public subnet**

### 2. Launch Instances
- **CPE VM** (Customer Premises Equipment)
  - Deployed in **public subnet**
  - Upload public SSH keys
  - After creation → Edit VNIC → **Skip source/destination check**
- **Ping VM**
  - Deployed in **private subnet**
  - Upload public SSH keys

➡ Both VMs are now provisioned.  
Make note of the **CPE VM’s public and private IP addresses** (needed later).

---

## 🔹 Phoenix Region (OCI Network)

### 1. Create VCN
- Name: `OCI-VCN`  
- Provide custom **CIDR block**  
- Launch using **VCN wizard**

### 2. Launch Instance
- Name: `test`
- Deploy in **public subnet**
- Upload SSH keys

*(Provisioning continues in background, no need to wait now.)*

---

## 🔹 Configure Connectivity in Phoenix

### 1. Create DRG
- Go to **Networking → Customer Connectivity → DRG**
- Name: `DRG`
- Click **Create**

### 2. Create VCN Attachment
- Attach `OCI-VCN` to the **DRG**

### 3. Create Customer Premises Equipment (CPE)
- Navigate: **Networking → Customer Connectivity → Customer Premises Equipment**
- Name: `DemoCPE`
- Vendor: **Libreswan**
- Platform: `3.18 or later`
- Public IP: *(Use the **CPE VM public IP** from Ashburn region)*  
- Click **Create**

### 4. Create IPSec Connection
- Navigate: **Networking → Customer Connectivity → Site-to-Site VPN**
- Click **Create IPSec Connection**
- Provide:
  - **CPE object**: `DemoCPE`
  - **Dynamic Routing Gateway**: `DRG`
  - **On-Prem CIDR**: `10.0.0.0/16`
- Configure two tunnels:
  - `tunnel1` → **Static Routing**
  - `tunnel2` → **Static Routing**
- Click **Create**

---

## ✅ Summary of Part 1

- In **Ashburn**, created **on-prem simulation VCN** with CPE VM + Ping VM.  
- In **Phoenix**, created **VCN, Test VM, DRG, CPE object, and IPSec connection**.  
- The **IPSec connection** includes two tunnels with static routing.  
