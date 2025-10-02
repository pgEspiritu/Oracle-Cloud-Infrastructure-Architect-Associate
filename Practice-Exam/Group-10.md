# Question 01

**Which is NOT a valid Oracle Cloud Infrastructure (OCI) Virtual Cloud Network (VCN) approach?**

- a) Ensure VCN CIDR prefix overlaps with other VCNs in your tenancy or with your organizations private IP network ranges.  
- b) Ensure not all IP addresses are allocated at once within a VCN or subnet; instead reserve some IP addresses for future use.  
- c) Private subnets should ideally have individual route tables to control the flow of traffic within and outside of VCN.  
- d) Use OCI tags to tag VCN resources so that all resources follow organizational tagging/naming conventions  

---

## ✅ Correct Answer: **a) Ensure VCN CIDR prefix overlaps with other VCNs in your tenancy or with your organizations private IP network ranges**  

---

## Explanation of Choices

- **a) Overlapping VCN CIDR** ❌  
  - Invalid; VCN CIDR ranges must not overlap with other VCNs or on-premises networks to avoid routing conflicts.  

- **b) Reserve IPs** ✅  
  - Valid; leaving some IP addresses unallocated ensures flexibility for future growth.  

- **c) Individual route tables** ✅  
  - Valid; private subnets benefit from separate route tables to control traffic flows.  

- **d) Use OCI tags** ✅  
  - Valid; tagging ensures compliance with organizational standards.  

---

# Question 02

**Your company sells services to photographers where patrons can preview the photos that they want prints for. To avoid unauthorized copies, the sample photos have lower resolution and are watermarked. The photos are processed after they are uploaded. The process is fast but not immediate. It creates samples and sends them to storage outside of the instances. Which type of instance is ideal for a process like this; short lived and one that keeps the cost low?**

- a) Preemptible instances  
- b) Spot instances  
- c) On-demand instances  
- d) Burstable instances  

---

## ✅ Correct Answer: **a) Preemptible instances**  

---

## Explanation of Choices

- **a) Preemptible instances** ✅  
  - Ideal for short-lived, interruptible workloads. Cost-effective and suitable for tasks like batch image processing.  

- **b) Spot instances**  
  - OCI does not use this term; preemptible is the correct option.  

- **c) On-demand instances**  
  - More expensive; better for long-running or critical workloads.  

- **d) Burstable instances**  
  - Designed for low-utilization workloads with occasional CPU bursts; not cost-optimal for batch processing.  

---

# Question 03

**Which TWO statements are TRUE about Public IP addresses in Oracle Cloud Infrastructure (OCI)?**

- a) Public IP addresses can be ephemeral or reserved.  
- b) You must use OCI provided public IP addresses. You cannot bring your own IP addresses to OCI.  
- c) By default, an instance in a public subnet has one primary public IP address.  
- d) You can assign a given instance multiple public IPs across one or more VNICs.  

---

## ✅ Correct Answer: **a) Public IP addresses can be ephemeral or reserved** and **c) By default, an instance in a public subnet has one primary public IP address**  

---

## Explanation of Choices

- **a) Ephemeral or reserved** ✅  
  - True; OCI supports both types.  

- **b) Must use OCI IPs**  
  - False; BYOIP is supported in certain cases.  

- **c) Default primary public IP** ✅  
  - True; instances in public subnets get one primary public IP automatically.  

- **d) Multiple public IPs**  
  - False; public IPs per instance are limited; multiple public IPs across VNICs are not supported in general.  

---

# Question 04

**Your IT team has asked you to provision an Autonomous Database in Oracle Cloud Infrastructure (OCI), but they want it to operate similar to what you have currently on-premises. What are the TWO prerequisites for successfully deploying an Autonomous Dedicated Database in OCI?**

- a) Autonomous Container Database  
- b) Object Storage  
- c) Exadata Infrastructure  
- d) Identity and Access Management (IAM) Policies  

---

## ✅ Correct Answer: **c) Exadata Infrastructure** and **d) Identity and Access Management (IAM) Policies**  

---

## Explanation of Choices

- **a) Autonomous Container Database**  
  - Not required; deployment uses dedicated infrastructure directly.  

- **b) Object Storage**  
  - Optional; used for backups but not required for deployment.  

- **c) Exadata Infrastructure** ✅  
  - Required; dedicated database runs on Exadata infrastructure.  

- **d) IAM Policies** ✅  
  - Required to grant the appropriate permissions to provision and manage the database.  

---

# Question 05

**Which of the following statements is true about cloning a volume in the Oracle Cloud Infrastructure (OCI) Block Volume service?**

- a) You need to detach a volume before cloning it.  
- b) Creating a clone takes longer than creating a backup of a volume.  
- c) You can clone a volume to another region.  
- d) You can change the block volume size when cloning a volume.  

---

## ✅ Correct Answer: **d) You can change the block volume size when cloning a volume**  

---

## Explanation of Choices

- **a) Detach before cloning**  
  - Not required; cloning can happen while the volume is attached.  

- **b) Takes longer than backup**  
  - Incorrect; cloning is usually faster because it is snapshot-based.  

- **c) Clone to another region**  
  - Not supported; cloning is limited to the same region.  

- **d) Change size when cloning** ✅  
  - Supported; the new volume can be larger than the source volume.  

---

# Question 06

**You just got a last minute request to create a set of instances in Oracle Cloud Infrastructure (OCI). The configuration and installed software are identical for every instance, and you already have a running instance in your OCI tenancy. Which image option allows you to achieve this task with the least amount of effort?**

- a) Bring your own image and use it as a template for the new instances.  
- b) Select an image from the OCI Marketplace.  
- c) Use Oracle-provided images and customize the installation using a third-party tool.  
- d) Create a custom image and use it as a template for the new instances.  

---

## ✅ Correct Answer: **d) Create a custom image and use it as a template for the new instances**  

---

## Explanation of Choices

- **a) BYO image**  
  - Requires additional work to upload; not minimal effort.  

- **b) Marketplace image**  
  - Pre-built images may not match your configuration.  

- **c) Oracle-provided images**  
  - Requires manual customization; more effort.  

- **d) Custom image as template** ✅  
  - Fastest and easiest way to replicate a configured instance.  

---

# Question 07

**Which is NOT a valid action within the Oracle Cloud Infrastructure (OCI) Block Volume service?**

- a) Expanding an existing volume in place with offline resizing.  
- b) Restoring from a volume backup to a larger volume.  
- c) Attaching a block volume to an instance in a different availability domain.  
- d) Cloning an existing volume to a new, larger volume.  

---

## ✅ Correct Answer: **c) Attaching a block volume to an instance in a different availability domain**  

---

## Explanation of Choices

- **a) Expanding volume offline** ✅  
  - Supported; offline resize may be required for certain OSs.  

- **b) Restore to larger volume** ✅  
  - Supported; allows resizing during restore.  

- **c) Attach across ADs** ❌  
  - Not allowed; block volumes are bound to a single availability domain.  

- **d) Clone to larger volume** ✅  
  - Supported; size can be increased when cloning.  

---

# Question 08

**When creating an Oracle Cloud Infrastructure (OCI) Virtual Cloud Network (VCN) with the VCN wizard, which THREE gateways are created automatically?**

- a) Internet Gateway  
- b) Local Peering Gateway  
- c) Dynamic Routing Gateway  
- d) NAT Gateway  
- e) Storage Gateway  
- f) Bastion Host  
- g) Service Gateway  

---

## ✅ Correct Answer: **a) Internet Gateway**, **d) NAT Gateway**, **g) Service Gateway**  

---

## Explanation of Choices

- **a) Internet Gateway** ✅  
  - Enables outbound internet traffic.  

- **b) Local Peering Gateway**  
  - Must be created manually; not automatic.  

- **c) Dynamic Routing Gateway**  
  - Optional; not created automatically.  

- **d) NAT Gateway** ✅  
  - Provides internet access to private subnets.  

- **e) Storage Gateway**  
  - Not created by default.  

- **f) Bastion Host**  
  - Must be provisioned separately.  

- **g) Service Gateway** ✅  
  - Enables private access to Oracle services without using the internet.  

---

# Question 09

**Which THREE capabilities are available with the Oracle Cloud Infrastructure (OCI) DNS service?**

- a) Creating and managing records  
- b) Creating and managing WAF rules  
- c) Creating and managing Identity Access Management (IAM) policies  
- d) Creating and managing zones  
- e) Viewing all zones  
- f) Creating and managing security lists  

---

## ✅ Correct Answer: **a) Creating and managing records**, **d) Creating and managing zones**, **e) Viewing all zones**  

---

## Explanation of Choices

- **a) Creating and managing records** ✅  
  - True; you can create, update, and delete DNS records.  

- **b) Creating and managing WAF rules**  
  - Not a DNS capability; handled by the WAF service.  

- **c) Creating and managing IAM policies**  
  - Not part of DNS service.  

- **d) Creating and managing zones** ✅  
  - True; DNS zones can be created and managed.  

- **e) Viewing all zones** ✅  
  - Supported; can list all DNS zones.  

- **f) Creating and managing security lists**  
  - Networking service; not part of DNS.  

---

# Question 10

**Which Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) policy is invalid?**

- a) Allow dynamic-group FrontEnd to manage instance-family in compartment Project-A  
- b) Allow any-user to inspect users in tenancy  
- c) Allow group A-Developers to create volumes in compartment Project-A  
- d) Allow group A-Admins to manage all-resources in compartment Project-A  

---

## ✅ Correct Answer: **b) Allow any-user to inspect users in tenancy**  

---

## Explanation of Choices

- **a) Allow dynamic-group FrontEnd to manage instance-family** ✅  
  - Valid; dynamic group can manage instances.  

- **b) Allow any-user to inspect users** ❌  
  - Invalid; `any-user` cannot inspect users in the tenancy.  

- **c) Allow group A-Developers to create volumes** ✅  
  - Valid; group can create block volumes in the compartment.  

- **d) Allow group A-Admins to manage all-resources** ✅  
  - Valid; grants full management rights within the compartment.  
