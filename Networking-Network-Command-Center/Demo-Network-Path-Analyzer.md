# 🚦 Demonstration: Network Path Analyzer in OCI

## 📌 Overview
In this demo, we will use **Network Path Analyzer** in OCI to check connectivity from a compute instance to the public internet.  
We’ll see how the tool detects routing misconfigurations and how fixing them makes the path reachable.

---

## 🏗️ Environment Setup
- **VCN**: `npademovcn`  
- **Subnet**: `npademosubnet`  
- **Internet Gateway**: created  
- **Default Route Table**: no changes made (no route to Internet Gateway yet)  
- **Security List (Default)**:  
  - **Egress Rules** → Destination: *Internet*, Protocol: *All*, Action: *Allow*  
- **Instance**: `npademoinstance` in the public subnet with a public IP  

---

## ▶️ Steps

### 1. Open Network Path Analyzer
- In the OCI Console, click **Navigation Menu** → **Networking** → **Network Command Center** → **Network Path Analyzer**.  
- Click **Create Path Analysis**.  
- Name: `demoanalysis`.  
- Select the compartment and protocol (many available, we’ll keep default).

---

### 2. Define Source
- **Source Type**: `Compute Instance`  
- **Instance**: `npademoinstance`  
- **VNIC**: default VNIC of the instance  
- **Source IP**: select the **public IP** of the instance  

*(Optional: in Advanced Options, you can also specify a source port.)*

---

### 3. Define Destination
- **Destination Type**: Enter an IP address  
- **Destination IP**: `8.8.8.8` (Google Public DNS)  
- **Port**: `53` (DNS)  

Select **Uni-directional traffic**.  
Click **Run Analysis**.  

---

### 4. First Analysis Result
- Status: ❌ **Unreachable**  
- Successful Hops: `0`  
- Analysis: **No Route configured**  
  - Routing ❌ Not configured  
  - Security ✅ Allowed  

---

### 5. Fix Routing
- Go to **VCN → Route Tables → Default Route Table**.  
- Add a route rule:  
  - **Destination**: `0.0.0.0/0`  
  - **Target**: Internet Gateway  
- Save changes.

---

### 6. Rerun Analysis
- Back in **Network Path Analyzer**, click **Analyze** again.  
- Status: ✅ **Reachable**  
- Successful Hops: `2`  

**Hop 1**: Instance → Internet Gateway  
- Routing: Forwarded  
- Security: Allowed  

**Hop 2**: Internet Gateway → `8.8.8.8`  
- Routing: Forwarded  
- Security: Allowed  

---

## 💡 Key Points
- **Without a route to the Internet Gateway**, connectivity fails even if Security List allows traffic.  
- **Network Path Analyzer** helps identify the exact cause (Routing vs Security).  
- You can save analyses for future reference.  
- Destination can be another **OCI resource** or an **external IP**.  
- Supports **OCI ↔ OCI** and **OCI ↔ Internet** connectivity validation.  
