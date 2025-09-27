# Question 01

**By default, OCI IAM policies follow the principle of least privilege. What does this principle mean in the context of policy creation?**

- A) Policies should be written in a complex and technical manner to enhance security.  
- B) Policies should grant all possible permissions to simplify access control.  
- C) Policies should provide only the minimum set of permissions required for users to perform their tasks effectively.  
- D) Policies should be identical for all users within a tenancy.  

---

## ✅ Correct Answer:  
**C) Policies should provide only the minimum set of permissions required for users to perform their tasks effectively.**

---

## Explanation of Choices

- **A) Policies should be written in a complex and technical manner to enhance security.**  
  - ❌ Incorrect.  
  - Policy language in OCI is designed to be **human-readable**, not complex. Complexity does not equal security.  

- **B) Policies should grant all possible permissions to simplify access control.**  
  - ❌ Incorrect.  
  - This goes against the principle of least privilege and exposes unnecessary risk.  

- **C) Policies should provide only the minimum set of permissions required for users to perform their tasks effectively.** ✅  
  - ✔ Correct.  
  - The **principle of least privilege** ensures users and groups have **only the permissions they need** to perform their jobs, nothing more.  
  - This reduces the attack surface and limits potential damage from mistakes or breaches.  

- **D) Policies should be identical for all users within a tenancy.**  
  - ❌ Incorrect.  
  - Policies should be **role-based** and tailored to different responsibilities. Uniform policies would give unnecessary access to many users.  

---

## 🔑 Key Takeaway
The **principle of least privilege** in OCI IAM policies means granting **just enough access** for users to perform their required tasks, improving both **security** and **compliance**.

---

# Question 02

**Which statement is true about File System Replication in Oracle Cloud Infrastructure (OCI)?**

- A) You cannot specify a replication interval when you create the replication resource.  
- B) You can replicate the data in one file system to another file system in the same region or a different region.  
- C) Only a file system that has been exported can be used as a target file system.  
- D) You can replicate the data in one file system to another file system only in the same region.  

---

## ✅ Correct Answer:  
**B) You can replicate the data in one file system to another file system in the same region or a different region.**

---

## Explanation of Choices

- **A) You cannot specify a replication interval when you create the replication resource.**  
  - ❌ Incorrect.  
  - OCI allows you to configure the **replication interval** (for example, every hour) when setting up file system replication.  

- **B) You can replicate the data in one file system to another file system in the same region or a different region.** ✅  
  - ✔ Correct.  
  - File System Replication in OCI supports both **intra-region** and **cross-region** replication, enabling disaster recovery and data protection strategies.  

- **C) Only a file system that has been exported can be used as a target file system.**  
  - ❌ Incorrect.  
  - The target file system does **not** need to be exported; it just serves as a replication destination.  

- **D) You can replicate the data in one file system to another file system only in the same region.**  
  - ❌ Incorrect.  
  - Replication is **not limited to the same region**; cross-region replication is supported.  

---

## 🔑 Key Takeaway
OCI **File System Replication** allows replication of data to another file system, either **within the same region or across regions**, supporting **disaster recovery, compliance, and high availability** requirements.

---

# Question 03

**What are the two types of capture filters that can be created for network monitoring?**

- A) Flow control capture filters and traffic capture filters  
- B) Flow log capture filters and packet capture filters  
- C) VTAP capture filters and network capture filters  
- D) Flow log capture filters and VTAP capture filters  

---

## ✅ Correct Answer:  
**D) Flow log capture filters and VTAP capture filters**

---

## Explanation of Choices

- **A) Flow control capture filters and traffic capture filters**  
  - ❌ Incorrect.  
  - These are not valid OCI terms; OCI does not define such capture filter types.  

- **B) Flow log capture filters and packet capture filters**  
  - ❌ Incorrect.  
  - Flow logs exist in OCI, but **packet capture filters** are not an OCI feature. Packet capture would require third-party tools.  

- **C) VTAP capture filters and network capture filters**  
  - ❌ Incorrect.  
  - VTAP (Virtual Test Access Point) filters are valid, but **network capture filters** are not a defined type in OCI.  

- **D) Flow log capture filters and VTAP capture filters** ✅  
  - ✔ Correct.  
  - OCI supports:  
    1. **Flow Log capture filters** → For monitoring and analyzing **VNIC flow logs**.  
    2. **VTAP capture filters** → For capturing **traffic mirrored from VNICs** using Virtual Test Access Points.  

---

## 🔑 Key Takeaway
OCI provides two capture filter types for network monitoring:  
- **Flow log capture filters** (log-based monitoring).  
- **VTAP capture filters** (traffic mirroring for deeper inspection).

---

# Question 04

**You want to protect your VM instance from low-level threats, such as rootkits and bootkits. What should you do?**

- A) Create a shielded instance.  
- B) Use in-transit encryption.  
- C) Create a burstable instance.  
- D) Use Vulnerability Scanning Service.  

---

## ✅ Correct Answer:  
**A) Create a shielded instance.**

---

## Explanation of Choices

- **A) Create a shielded instance.** ✅  
  - ✔ Correct.  
  - Shielded instances in OCI provide **measured boot and secure boot capabilities** to protect against low-level threats like **rootkits, bootkits, and firmware attacks**.  
  - They ensure the VM boots into a **trusted and verified state**.  

- **B) Use in-transit encryption.**  
  - ❌ Incorrect.  
  - In-transit encryption protects **data traveling over the network**, not the boot process or low-level threats.  

- **C) Create a burstable instance.**  
  - ❌ Incorrect.  
  - Burstable instances are a **cost-saving compute option** that allows CPU usage to scale up temporarily.  
  - They have nothing to do with security.  

- **D) Use Vulnerability Scanning Service.**  
  - ❌ Incorrect.  
  - Vulnerability Scanning Service (VSS) detects **known vulnerabilities in OS packages and ports**, but it does not protect against **rootkits or bootkits** at the firmware/boot level.  

---

## 🔑 Key Takeaway
To protect against **rootkits, bootkits, and firmware-level threats**, use **Shielded Instances**, which enforce a **trusted boot environment**.

---

# Question 05

**With OCI's pricing of $0.0085 USD per Gigabyte for Outbound Data Transfer in North America, how much will they spend per month for 7 Petabytes of Outbound Data Transfer?**

- A) $59,500.00  
- B) $59,415.00  
- C) $0.00 (free with OCI)  
- D) $150,000.00  

---

## ✅ Correct Answer:  
**B) $59,415.00**

---

## Step-by-Step Calculation

1. **Convert Petabytes to Gigabytes**  
   - 1 Petabyte = 1,000,000 Gigabytes (decimal convention is used for OCI billing).  
   - 7 Petabytes = **7,000,000 GB**.  

2. **Apply Pricing**  
   - Price per GB = **$0.0085**  
   - Total cost = 7,000,000 × 0.0085  

3. **Multiply**  
   - 7,000,000 × 0.0085 = **59,500.00**  

⚠ But here’s the catch: OCI provides the **first 10 TB (10,240 GB) free per month** for outbound data transfer.  

4. **Adjust for Free Tier**  
   - 7,000,000 GB – 10,240 GB = **6,989,760 GB billable**  

5. **Final Cost**  
   - 6,989,760 × 0.0085 = **59,413.96 ≈ $59,415.00**  

---

## Explanation of Choices

- **A) $59,500.00**  
  - ❌ Incorrect.  
  - This ignores the **10 TB free allowance**.  

- **B) $59,415.00** ✅  
  - ✔ Correct.  
  - Accounts for the **first 10 TB free**, then charges for the remaining outbound data.  

- **C) $0.00 (free with OCI)**  
  - ❌ Incorrect.  
  - Only the first 10 TB are free, not petabytes.  

- **D) $150,000.00**  
  - ❌ Incorrect.  
  - This doesn’t match OCI’s actual pricing structure.  

---

## 🔑 Key Takeaway
OCI charges **$0.0085/GB** for outbound data transfer in North America, with the **first 10 TB free** each month.  
For **7 PB outbound**, the monthly cost is about **$59,415.00**.

---

# Question 06

**You can attach resources to a Dynamic Routing Gateway (DRG). Select THREE of these resources.**

- A) Virtual Circuits  
- B) Subnet  
- C) VNIC  
- D) Remote Peering Connections  
- E) IPSec Tunnel  
- F) Local Peering Connection  

---

## ✅ Correct Answers:  
**A) Virtual Circuits**  
**D) Remote Peering Connections**  
**E) IPSec Tunnel**

---

## Explanation of Choices

- **A) Virtual Circuits** ✅  
  - ✔ Correct.  
  - A DRG connects to **FastConnect** through **virtual circuits**, enabling private dedicated connectivity from on-premises to OCI.  

- **B) Subnet**  
  - ❌ Incorrect.  
  - Subnets connect to a **VCN**, not directly to a DRG.  

- **C) VNIC**  
  - ❌ Incorrect.  
  - A VNIC is attached to an **instance**, not to a DRG.  

- **D) Remote Peering Connections (RPC)** ✅  
  - ✔ Correct.  
  - DRGs support **remote VCN peering** (across regions) via **Remote Peering Connections**.  

- **E) IPSec Tunnel** ✅  
  - ✔ Correct.  
  - A DRG terminates **site-to-site VPNs** via **IPSec tunnels**, linking on-premises networks to OCI.  

- **F) Local Peering Connection (LPG)**  
  - ❌ Incorrect.  
  - LPG is used for **local VCN-to-VCN peering within the same region** and does not require a DRG.  

---

## 🔑 Key Takeaway
A **DRG** acts as a hub for **hybrid and multicloud connectivity**, attaching to:  
- **Virtual Circuits (FastConnect)**  
- **IPSec Tunnels (VPN)**  
- **Remote Peering Connections (RPC)**  

---

# Question 07

**What is the primary function of the Network Path Analyzer (NPA) tool provided by Oracle Cloud Infrastructure (OCI)?**

- A) Collecting and analyzing network configuration to identify virtual network configuration issues impacting connectivity  
- B) Optimizing network performance by dynamically adjusting routing paths based on traffic patterns  
- C) Sending actual traffic between source and destination to diagnose connectivity issues  
- D) Providing real-time monitoring of network traffic to detect security threats and unauthorized access attempts  

---

## ✅ Correct Answer:  
**A) Collecting and analyzing network configuration to identify virtual network configuration issues impacting connectivity**

---

## Explanation of Choices

- **A) Collecting and analyzing network configuration** ✅  
  - ✔ Correct.  
  - OCI **Network Path Analyzer** inspects **VCNs, subnets, route tables, gateways, and security rules** to detect misconfigurations that may block connectivity.  
  - It does **not send live traffic**, instead it uses configuration analysis to model the path.  

- **B) Optimizing network performance**  
  - ❌ Incorrect.  
  - NPA does not reroute traffic; it's a diagnostic tool, not an optimizer.  

- **C) Sending actual traffic**  
  - ❌ Incorrect.  
  - NPA does **not generate real packets**; it analyzes configuration state only.  

- **D) Real-time monitoring for threats**  
  - ❌ Incorrect.  
  - That’s the role of **OCI Cloud Guard** or **Network Monitoring**, not NPA.  

---

## 🔑 Key Takeaway
The **Network Path Analyzer (NPA)** helps troubleshoot connectivity by **analyzing configuration**, not by generating or monitoring traffic.

---

# Question 08

**Which TWO are key benefits of setting up Site-to-Site VPN on Oracle Cloud Infrastructure (OCI)?**

- A) When setting up Site-to-Site VPN, customers can expect bandwidth above 2 Gbps.  
- B) When setting up Site-to-Site VPN, customers can configure it to use static or dynamic routing (BGP).  
- C) When setting up Site-to-Site VPN, OCI provisions redundant VPN tunnels.  
- D) When setting up Site-to-Site VPN, it creates a private connection that provides consistent network experience.  

---

## ✅ Correct Answers:  
**B) Static or dynamic routing (BGP)**  
**C) Redundant VPN tunnels**  

---

## Explanation of Choices

- **A) Bandwidth above 2 Gbps**  
  - ❌ Incorrect.  
  - Site-to-Site VPNs are **limited to around 250 Mbps per tunnel**, not multi-Gbps.  
  - For guaranteed high bandwidth, customers should use **FastConnect**, not VPN.  

- **B) Static or dynamic routing (BGP)**  
  - ✔ Correct.  
  - OCI supports **policy-based (static)** and **route-based (BGP dynamic)** routing for flexibility.  

- **C) Redundant VPN tunnels**  
  - ✔ Correct.  
  - OCI provisions **two IPsec VPN tunnels** for high availability and failover.  

- **D) Private connection with consistent experience**  
  - ❌ Incorrect.  
  - VPN runs **over the public internet** and is subject to internet latency/variability.  
  - A **private, consistent connection** is provided only by **FastConnect**.  

---

## 🔑 Key Takeaway
OCI **Site-to-Site VPN** is best for secure, encrypted connectivity with **redundant tunnels** and **flexible routing options** — but for guaranteed bandwidth and consistency, **FastConnect** is the right service.

---

# Question 09

**Which statement is TRUE about restoring a volume from a block volume backup in the Oracle Cloud Infrastructure (OCI) Block Volume service?**

- A) You can restore a volume from any full volume backup but not from an incremental backup.  
- B) You can restore a block volume backup to a larger volume size.  
- C) You can restore only one volume from a manual block volume backup.  
- D) You can only restore a volume to the same availability domain in which the original block volume resides.  

---

## ✅ Correct Answer:  
**B) You can restore a block volume backup to a larger volume size.**

---

## Explanation of Choices

- **A) Restore only from full backup, not incremental**  
  - ❌ Incorrect.  
  - OCI automatically handles incremental backups: when you restore from an incremental backup, it uses the chain of full + incremental backups to rebuild the volume.  

- **B) Restore to a larger volume size**  
  - ✔ Correct.  
  - OCI allows restoring a backup to a new volume that is **equal or larger** in size than the original.  
  - This is useful if you need more capacity.  

- **C) Restore only one volume from a manual backup**  
  - ❌ Incorrect.  
  - You can **create multiple volumes** from the same backup.  

- **D) Restore only to the same AD**  
  - ❌ Incorrect.  
  - Block volume backups are **regional**. You can restore them to **any availability domain** in the region, not just where the original volume was created.  

---

## 🔑 Key Takeaway
Block volume backups in OCI are **regional, incremental, and flexible** — you can restore them to **any AD in the region** and even **resize to larger volumes** during restore.

---

# Question 10

**Which statement is TRUE about delegating an existing domain to the Oracle Cloud Infrastructure (OCI) DNS service?**

- A) All domains can be retrieved to OCI DNS via DYN.  
- B) Domains can be delegated to OCI DNS from the Domain Registrar's self-service portal.  
- C) Domains can be delegated to OCI DNS via FastConnect partners.  
- D) Domains can be self-delegated to OCI DNS from its own service portal.  

---

## ✅ Correct Answer:  
**B) Domains can be delegated to OCI DNS from the Domain Registrar's self-service portal.**

---

## Explanation of Choices

- **A) Retrieved via DYN**  
  - ❌ Incorrect.  
  - OCI DNS is based on Dyn’s infrastructure, but domains are **not automatically retrieved** from Dyn or other providers.  

- **B) Delegated via registrar’s self-service portal**  
  - ✔ Correct.  
  - To use OCI DNS, you configure your domain’s **NS (Name Server) records** at your **domain registrar** (e.g., GoDaddy, Namecheap) to point to OCI DNS servers.  

- **C) Delegated via FastConnect partners**  
  - ❌ Incorrect.  
  - FastConnect is for **network connectivity**, not DNS delegation.  

- **D) Self-delegated from OCI DNS portal**  
  - ❌ Incorrect.  
  - Delegation must happen at the **domain registrar**, not directly inside OCI DNS.  

---

## 🔑 Key Takeaway
To use **OCI DNS** for your domain, you must **update NS records at the domain registrar** so that traffic is directed to Oracle’s DNS servers.
