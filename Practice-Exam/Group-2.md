# Question 01

**Which policy would you write to provide admin access to all three of your existing admin groups for a shared Test compartment?**

- A) Allow all-group to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'  
- B) Allow dynamic-group to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'  
- C) Allow any-user to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'  
- D) Allow group any-group to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'  

---

## ✅ Correct Answer: **A) Allow all-group to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'**

---

## Explanation of Choices

- **A) Allow all-group to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'** ✅  
  - Correct.  
  - `all-group` is a special principal that allows you to use **tag-based conditional policies** across multiple IAM groups.  
  - By checking the group tag `EmployeeGroup.Role='Admin'`, only your three admin groups with that tag will get admin access to the **Test** compartment.  

- **B) Allow dynamic-group to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'**  
  - ❌ Incorrect.  
  - A **dynamic group** is for instances and resources with matching rules, not human IAM groups.  
  - This would not apply to your admin groups.  

- **C) Allow any-user to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'**  
  - ❌ Incorrect.  
  - `any-user` applies to **federated users** (e.g., from an identity provider).  
  - Not appropriate for OCI native IAM groups.  

- **D) Allow group any-group to manage all-resources in compartment Test where request.principal.group.tag.EmployeeGroup.Role='Admin'**  
  - ❌ Incorrect.  
  - There is no reserved keyword `any-group` in IAM policy syntax.  
  - This would result in a policy syntax error.  

---

# Question 02

**Which TWO statements are true about performing a multipart upload using the Multipart Upload API?**

- A) You do not have to commit the upload after uploading all parts.  
- B) You do not need to split the object into parts.  
- C) Each part can be as large as 50 GiB.  
- D) You can keep adding parts as long as the total number is less than 10,000.  

---

## ✅ Correct Answers: **C) Each part can be as large as 50 GiB** and **D) You can keep adding parts as long as the total number is less than 10,000**

---

## Explanation of Choices

- **A) You do not have to commit the upload after uploading all parts.**  
  - ❌ Incorrect.  
  - A multipart upload requires a **final commit step**.  
  - Without committing, the upload remains incomplete and the object won’t be available in the bucket.  

- **B) You do not need to split the object into parts.**  
  - ❌ Incorrect.  
  - The whole point of a multipart upload is to **split the object** into multiple parts to improve reliability and parallelism.  
  - If you don’t want to split, a standard single-part upload is used instead.  

- **C) Each part can be as large as 50 GiB.** ✅  
  - ✔ Correct.  
  - OCI Multipart Upload supports **parts up to 50 GiB** in size.  
  - The minimum part size is **128 MiB** (except for the last part).  

- **D) You can keep adding parts as long as the total number is less than 10,000.** ✅  
  - ✔ Correct.  
  - A multipart upload supports up to **10,000 parts** per object.  

---

# Question 03

**Which of the following is a valid RFC 1918 CIDR prefix that can be used for creating an Oracle Cloud Infrastructure (OCI) Virtual Cloud Network (VCN)?**

- A) 192.168.0.0/16  
- B) 0.0.0.0/0  
- C) 192.268.0.0/24  
- D) 10.0.0.0/8  

---

## ✅ Correct Answers: **A) 192.168.0.0/16** and **D) 10.0.0.0/8**

---

## Explanation of Choices

- **A) 192.168.0.0/16** ✅  
  - ✔ Correct.  
  - This is one of the private IP ranges defined in **RFC 1918**.  
  - Commonly used for home and enterprise networks.  

- **B) 0.0.0.0/0**  
  - ❌ Incorrect.  
  - This represents the **entire IPv4 address space** (all possible addresses).  
  - It is not a private CIDR block and cannot be assigned to a VCN.  

- **C) 192.268.0.0/24**  
  - ❌ Incorrect.  
  - This is an **invalid IP range** because the maximum value for any octet is **255**, not 268.  

- **D) 10.0.0.0/8** ✅  
  - ✔ Correct.  
  - Another valid **RFC 1918 private IP range**, often used in large enterprise and cloud networks.  

---

## 🔑 Quick RFC 1918 Reference

- **10.0.0.0/8**  
- **172.16.0.0/12**  
- **192.168.0.0/16**  

Only these ranges are considered **private** and can be used for VCNs in OCI.  

---

# Question 04

**What would happen if you choose not to proactively reboot the instance before the scheduled maintenance due date?**

- A) You will receive another notification to reboot within the next 14 days.  
- B) The instance will get terminated.  
- C) The instance is either reboot-migrated or rebuilt in place for you.  
- D) You will receive another notification to reboot within the next 7 days.  

---

## ✅ Correct Answer: **C) The instance is either reboot-migrated or rebuilt in place for you.**

---

## Explanation of Choices

- **A) You will receive another notification to reboot within the next 14 days.**  
  - ❌ Incorrect.  
  - OCI does not keep extending maintenance deadlines indefinitely.  

- **B) The instance will get terminated.**  
  - ❌ Incorrect.  
  - Maintenance events do **not terminate instances**.  
  - The goal is to preserve workloads while applying security and infrastructure updates.  

- **C) The instance is either reboot-migrated or rebuilt in place for you.** ✅  
  - ✔ Correct.  
  - If you don’t reboot before the due date, OCI automatically performs maintenance:  
    - **Reboot migration** (moves the VM to a healthy host)  
    - or **Rebuild in place** (updates the same host)  
  - This ensures patches and hardware fixes are applied without requiring termination.  

- **D) You will receive another notification to reboot within the next 7 days.**  
  - ❌ Incorrect.  
  - Maintenance deadlines are enforced. OCI does not just keep notifying; it takes automated action.  

---

## 🔑 Key Takeaway
If you don’t reboot your instance before the scheduled maintenance deadline, **OCI automatically handles it for you** by reboot-migrating or rebuilding the instance to apply necessary updates.

---

# Question 05

**Which TWO statements about the Oracle Cloud Infrastructure (OCI) File Storage Service are accurate?**

- A) Communication with file systems in a mount target is encrypted via HTTPS.  
- B) Customers can encrypt data in their file system using their own Vault encryption key.  
- C) Customers can encrypt the communication to a mount target via export options.  
- D) File systems use Oracle-managed keys by default.  

---

## ✅ Correct Answers:  
**B) Customers can encrypt data in their file system using their own Vault encryption key.**  
**D) File systems use Oracle-managed keys by default.**

---

## Explanation of Choices

- **A) Communication with file systems in a mount target is encrypted via HTTPS.**  
  - ❌ Incorrect.  
  - File Storage Service uses **NFS v3** for communication, not HTTPS.  
  - Encryption of data in transit is handled via **Kerberos authentication** and **network security**, not HTTPS.  

- **B) Customers can encrypt data in their file system using their own Vault encryption key.** ✅  
  - ✔ Correct.  
  - By default, OCI File Storage encrypts data using **Oracle-managed keys**.  
  - However, customers can choose to use their **own keys stored in OCI Vault** for greater control (Customer-Managed Keys).  

- **C) Customers can encrypt the communication to a mount target via export options.**  
  - ❌ Incorrect.  
  - Export options control **client access and permissions**, not encryption.  
  - Encryption in transit is provided via supported methods like Kerberos.  

- **D) File systems use Oracle-managed keys by default.** ✅  
  - ✔ Correct.  
  - All data in OCI File Storage is automatically encrypted **at rest** with **Oracle-managed keys**, unless customers override with their own Vault keys.  

---

## 🔑 Key Takeaway
OCI File Storage Service ensures encryption at rest by default with Oracle-managed keys, but customers have the flexibility to bring their own keys via OCI Vault for stricter security compliance.

---

# Question 06

**Which OCI feature should be used to ensure that communication between database servers and OCI Object Storage is secure?**

- A) Use a Local Peering Gateway  
- B) Use a NAT Gateway  
- C) Use a VPN Gateway  
- D) Use a Service Gateway  

---

## ✅ Correct Answer:  
**D) Use a Service Gateway**

---

## Explanation of Choices

- **A) Use a Local Peering Gateway**  
  - ❌ Incorrect.  
  - A Local Peering Gateway (LPG) connects **two VCNs in the same region**, not to OCI services like Object Storage.  

- **B) Use a NAT Gateway**  
  - ❌ Incorrect.  
  - A NAT Gateway allows private resources to access the internet, but this would expose traffic to the public internet rather than keeping it secure within Oracle’s network.  

- **C) Use a VPN Gateway**  
  - ❌ Incorrect.  
  - A VPN Gateway secures communication between **on-premises networks** and OCI VCNs over IPSec.  
  - It does not directly secure communication between OCI database servers and Object Storage.  

- **D) Use a Service Gateway** ✅  
  - ✔ Correct.  
  - A Service Gateway allows VCN resources (like databases) to access OCI services such as **Object Storage** securely without traversing the public internet.  
  - This ensures traffic stays **within the Oracle Cloud network backbone**, providing security and efficiency.  

---

## 🔑 Key Takeaway
To keep communication between OCI resources and services (like Object Storage) **secure and private**, always use a **Service Gateway** instead of exposing traffic to the internet.

---

# Question 07

**What is the primary purpose of the Web Application Acceleration service offered by Oracle Cloud Infrastructure (OCI)?**

- A) Monitoring and analyzing HTTP traffic patterns  
- B) Improving the reliability of layer 7 HTTP load balancers  
- C) Encrypting HTTP traffic  
- D) Speeding up traffic on layer 7 HTTP load balancers  

---

## ✅ Correct Answer:  
**D) Speeding up traffic on layer 7 HTTP load balancers**

---

## Explanation of Choices

- **A) Monitoring and analyzing HTTP traffic patterns**  
  - ❌ Incorrect.  
  - Monitoring and traffic analysis is done through **OCI Logging, Monitoring, and Application Performance Monitoring (APM)** services, not Web Application Acceleration.  

- **B) Improving the reliability of layer 7 HTTP load balancers**  
  - ❌ Incorrect.  
  - Reliability of load balancers is handled by **OCI Load Balancing service** itself with high availability configurations.  
  - Web Application Acceleration does not directly improve reliability, it improves **performance**.  

- **C) Encrypting HTTP traffic**  
  - ❌ Incorrect.  
  - Encryption of HTTP traffic is done using **SSL/TLS termination** on the Load Balancer, not Web Application Acceleration.  

- **D) Speeding up traffic on layer 7 HTTP load balancers** ✅  
  - ✔ Correct.  
  - Web Application Acceleration (a feature of OCI Load Balancing) provides **caching, compression, and connection optimization**.  
  - These reduce latency and improve performance of applications by accelerating traffic at the **application (layer 7) level**.  

---

## 🔑 Key Takeaway
The **Web Application Acceleration** feature in OCI primarily enhances the **speed and performance** of traffic handled by **layer 7 HTTP load balancers** through caching and optimization techniques.

---

# Question 08

**Which OCI Object Storage tier is suitable for storing the backup to minimize cost while meeting the requirements of immediate accessibility and retention of 31 days?**

- A) Archive tier  
- B) Auto-Tiering tier  
- C) Standard tier  
- D) Infrequent Access tier  

---

## ✅ Correct Answer:  
**D) Infrequent Access tier**

---

## Explanation of Choices

- **A) Archive tier**  
  - ❌ Incorrect.  
  - Archive is the **lowest-cost storage tier**, but objects stored here are **not immediately accessible**.  
  - They require a **restore process** that can take hours, making it unsuitable for workloads that need instant access.  

- **B) Auto-Tiering tier**  
  - ❌ Incorrect.  
  - Auto-Tiering automatically moves objects between **Standard and Infrequent Access** based on usage patterns.  
  - However, for a **known 31-day retention period**, choosing **Infrequent Access** directly is more cost-efficient and predictable.  

- **C) Standard tier**  
  - ❌ Incorrect.  
  - Standard tier provides **immediate access** but is more expensive than Infrequent Access.  
  - Since the data is for backup and likely accessed rarely, Standard is not the most cost-efficient option.  

- **D) Infrequent Access tier** ✅  
  - ✔ Correct.  
  - Best suited for **data that must remain immediately accessible but is not frequently retrieved**.  
  - Ideal for **backups with a retention period of 31 days**, balancing **low cost** and **instant access**.  

---

## 🔑 Key Takeaway
For **backups with immediate accessibility requirements** and **short-term retention (like 31 days)**, the **Infrequent Access tier** is the most cost-effective Object Storage option.

---

# Question 09

**Why was SSH still possible after port 22 was removed from the Security Lists?**

- A) The VCN where that compute instance resides still has an Internet Gateway.  
- B) The VNIC of that compute instance is attached to a Cluster Network.  
- C) The VCN where that compute instance resides still has a route rule.  
- D) The VNIC of that compute instance is attached to a Network Security Group (NSG).  

---

## ✅ Correct Answer:  
**D) The VNIC of that compute instance is attached to a Network Security Group (NSG).**

---

## Explanation of Choices

- **A) The VCN where that compute instance resides still has an Internet Gateway.**  
  - ❌ Incorrect.  
  - An Internet Gateway only provides **connectivity** to the internet.  
  - It does not override **port access rules** like SSH (port 22).  

- **B) The VNIC of that compute instance is attached to a Cluster Network.**  
  - ❌ Incorrect.  
  - Cluster Networks are used for **HPC (High-Performance Computing)** setups and do not impact SSH access in this context.  

- **C) The VCN where that compute instance resides still has a route rule.**  
  - ❌ Incorrect.  
  - A route rule only defines the **path of traffic**, not whether traffic is allowed or blocked at the port level.  

- **D) The VNIC of that compute instance is attached to a Network Security Group (NSG).** ✅  
  - ✔ Correct.  
  - **NSGs** provide a **virtual firewall at the VNIC level**.  
  - If the instance’s VNIC is in an NSG with rules that allow **SSH (port 22)**, SSH access remains possible even if Security Lists block it.  

---

## 🔑 Key Takeaway
In OCI, **NSG rules override Security List rules** for VNICs attached to an NSG. If port 22 is open in the NSG, SSH remains accessible.

---

# Question 10

**Which is NOT a necessary step to complete this setup for instance principals?**

- A) Deploy the application and the SDK to all the instances that belong to the dynamic group.  
- B) Create a dynamic group with matching rules to specify which instances can make API calls against services.  
- C) Create a policy granting permissions to the dynamic group to access services in your compartment or tenancy.  
- D) Generate Auth Tokens to enable instances in the dynamic group to authenticate with APIs.  

---

## ✅ Correct Answer:  
**D) Generate Auth Tokens to enable instances in the dynamic group to authenticate with APIs.**

---

## Explanation of Choices

- **A) Deploy the application and the SDK to all the instances that belong to the dynamic group.**  
  - ✔ Necessary.  
  - Applications running on instances need the **OCI SDK or CLI** to leverage instance principals for authentication.  

- **B) Create a dynamic group with matching rules to specify which instances can make API calls against services.**  
  - ✔ Necessary.  
  - Dynamic groups are how you identify and group instances for **authorization** without using individual credentials.  

- **C) Create a policy granting permissions to the dynamic group to access services in your compartment or tenancy.**  
  - ✔ Necessary.  
  - The dynamic group alone is not enough—you must create an IAM **policy** to allow it to perform specific actions.  

- **D) Generate Auth Tokens to enable instances in the dynamic group to authenticate with APIs.** ❌  
  - Not required.  
  - **Auth Tokens** are used for users (e.g., for CLI access), not for instances.  
  - Instance principals use **short-lived certificates issued by the Instance Metadata Service (IMDS)**, not auth tokens.  

---

## 🔑 Key Takeaway
When configuring **instance principals**, you need to:  
1. Deploy the app/SDK.  
2. Create a dynamic group.  
3. Write a policy for that dynamic group.  
**You do NOT need to generate Auth Tokens.**
