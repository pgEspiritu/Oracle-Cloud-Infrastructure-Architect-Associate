# 📘 Lesson: Capture Filters in OCI

## 📌 Introduction
As part of **Network Command Center Services**, we have two key features:
- 📊 **Flow Logs**  
- 🛰️ **Virtual Test Access Points (VTAPs)**  

👉 When using either **Flow Logs** or **VTAPs**, you can apply **Capture Filters** to decide which traffic to include.  
This helps avoid unnecessary overhead by focusing only on the traffic you care about.

---

## 🎯 Why Capture Filters?
- Capturing *all traffic* can cause **performance degradation**.  
- Capture Filters let you **selectively capture traffic** → only what’s needed.  
- A **VTAP must have an associated capture filter**.  
- Each filter:  
  - Must have **at least 1 rule**  
  - Can have **up to 10 rules**  

⚠️ **Rules are executed in order**. Once a packet matches a rule, **remaining rules are ignored**.  
This means **rule order is critical**.

---

## ⚙️ Capture Filter Rules
A rule can specify:
- ✅ **Include** or ❌ **Exclude**  
- 🌐 **Source & Destination CIDR**  
- 🔄 **Traffic Direction** (Ingress / Egress)  
- 📡 **Protocol** (TCP, UDP, ICMP, etc.)  
- 🔢 **Source & Destination Port**

📌 **Default behavior**: If no CIDR or protocol is specified → **all IPs / protocols are accepted**.

---

## 🏗️ Example: Filtering HTTP Traffic
Imagine:
- **VTAP Source** = Load Balancer  
- **VTAP Target** = Network Load Balancer  
- Backend servers are inside **Subnet A**  

👉 We want to capture **ingress HTTP traffic** from the internet.

**Rule Example:**
- Direction: **Ingress**  
- Source CIDR: `0.0.0.0/0` (Internet) 🌍  
- Destination CIDR: `Subnet A`  
- Protocol: **TCP**  
- Destination Port: **80** (HTTP)  

📊 This captures **incoming HTTP requests** from the internet.

---

## 🧩 Rule Order Example
Goal: Capture all traffic from `10.1.0.0/16` except from `10.1.1.1`.

### ✅ Correct Rule Order
1. `10.1.1.1/32 → Exclude`  
2. `10.1.0.0/16 → Include`  

🔎 Result:  
- Traffic from `10.1.1.1` matches **Rule 1 → Excluded**  
- Other traffic in `10.1.0.0/16` matches **Rule 2 → Included**

---

### ❌ Incorrect Rule Order
1. `10.1.0.0/16 → Include`  
2. `10.1.1.1/32 → Exclude`  

🔎 Result:  
- Traffic from `10.1.1.1` matches **Rule 1 → Included**  
- Rule 2 is never evaluated 🚫  

⚠️ **Ordering directly affects capture results.**

---

## ✅ Key Takeaways
- 📌 Capture Filters = Selective traffic capture for Flow Logs & VTAPs  
- 🛠️ Each VTAP **must** have a capture filter  
- 🔢 Up to **10 rules**, executed **in sequence**  
- ⚡ Rule ordering is **critical**  
- 🧪 Supports filtering by CIDR, protocol, port, and traffic direction  
