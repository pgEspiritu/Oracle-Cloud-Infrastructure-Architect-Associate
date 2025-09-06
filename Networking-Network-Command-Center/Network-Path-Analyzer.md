# 🔎 Network Path Analyzer

## 📌 Overview
**Network Path Analyzer** is a **Network Command Center tool** that helps identify connectivity problems by analyzing routing and security configurations.  
It provides **hop-by-hop path visualization** and supports both **uni-directional** and **bi-directional** (forward + return path) analysis.

---

## ⚙️ How It Works
- Uses **automated configuration analysis**:
  - Examines **routing rules** and **security rules**.
  - Queries networking constructs to confirm reachability.  
- **No actual traffic** is sent — analysis is done purely via configuration checks.  
- **Free service** — no cost regardless of how many analyses are run.  
- Supports multiple connectivity scenarios:
  - **OCI ↔ OCI**  
  - **OCI ↔ On-premises**  
  - **OCI ↔ Internet**

---

## ✨ Features
- 🔍 Pinpoints **routing & security misconfigurations**.  
- 🌐 Supports connectivity to **Oracle Services Network** via service gateway or private endpoint.  
- 🔄 Bi-directional and uni-directional analysis options.  
- 📊 Provides **visual hop-by-hop connectivity path**.

---

## 🛠️ Example Scenarios
### 1. **OCI ↔ OCI**
- Source: Instance inside a VCN.  
- Destination: Instance inside another VCN.  
- Both connected via **DRG (Dynamic Routing Gateway)**.  
- ❌ Traffic denied due to **misconfigured security list**, resulting in **unreachable status**.  

### 2. **OCI ↔ Internet**
- Source: OCI resource.  
- Destination: Internet service (e.g., **Google Public DNS**).  
- ❌ No route configured + **egress rule denies access**.  
- ✅ Fix: Add required **route** and **security rules**.

---

## 🚀 Use Cases
- 🧭 **Troubleshoot** routing and security misconfigurations causing connectivity issues.  
- ⏱️ **Reduce Mean Time to Resolution (MTTR)** during outages.  
- 🔬 Perform **on-demand validation** of logical paths before onboarding production apps.  
- ⚡ Proactively **verify and validate** network routing and security policies.  
- 📦 Avoid deployment delays by ensuring connectivity setup works **before go-live**.  
