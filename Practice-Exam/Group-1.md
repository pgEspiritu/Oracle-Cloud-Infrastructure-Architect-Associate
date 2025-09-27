# Question 01

**OCI compartment quotas have three quota policy statements: Set, Unset, and Zero. Which statement removes all access to a specific resource type within a compartment?**

- a) Set  
- b) Unset  
- c) Zero  
- d) All statements have the same effect  

---

## ✅ Correct Answer: **c) Zero**

---

## Explanation of Choices

- **a) Set**  
  - The `Set` statement assigns a fixed quota (e.g., `set compute quota vm-standard2-1 count to 5`).  
  - It limits the resource to the specified number, **not** completely removing access.  

- **b) Unset**  
  - The `Unset` statement removes a quota policy previously applied.  
  - This restores the resource to the default service limits, not eliminating access.  

- **c) Zero** ✅  
  - The `Zero` statement explicitly sets the quota of a resource to **0**, effectively blocking any creation of that resource type in the compartment.  
  - Example: `set compute quota vm-standard2-1 count to zero`.  
  - This is the **only statement that removes all access**.  

- **d) All statements have the same effect**  
  - Incorrect, since each has a distinct purpose (`Set` limits, `Unset` removes limits, `Zero` blocks access).  

---

# Question 02

**Which two are valid retention rule types in Oracle Cloud Infrastructure (OCI) Object Storage?**

- a) Time-bound  
- b) Unlimited  
- c) Indefinite  
- d) Duration-bound  

---

## ✅ Correct Answers: **a) Time-bound** and **c) Indefinite**

---

## Explanation of Choices

- **a) Time-bound** ✅  
  - A retention rule type where you specify a **fixed duration** (e.g., 30 days, 5 years).  
  - Objects cannot be deleted until the retention period ends.  

- **b) Unlimited**  
  - Not a valid rule type in OCI Object Storage.  
  - The correct term for permanent retention is **Indefinite**, not Unlimited.  

- **c) Indefinite** ✅  
  - A retention rule type where objects are **retained forever**, until the rule is explicitly deleted.  
  - Useful for compliance or long-term preservation.  

- **d) Duration-bound**  
  - Not a valid OCI retention rule type.  
  - The correct term is **Time-bound**, not Duration-bound.  

---


# Question 03

**In OCI IAM, which authentication method enables compute instances to access resources securely without storing credentials directly?**

- a) API keys  
- b) Federated Identity  
- c) OAuth 2.0 tokens  
- d) Instance Principal  

---

## ✅ Correct Answer: **d) Instance Principal**

---

## Explanation of Choices

- **a) API keys**  
  - API keys allow users or apps to authenticate against OCI, but they **require storing keys** on the instance or in configuration files.  
  - This introduces a security risk if the keys are exposed.  

- **b) Federated Identity**  
  - Used for integrating external identity providers (e.g., Microsoft Active Directory, Oracle IDCS).  
  - It’s intended for **human users**, not compute instances.  

- **c) OAuth 2.0 tokens**  
  - Used in certain integrations and third-party apps.  
  - Not the standard OCI mechanism for instance authentication.  

- **d) Instance Principal** ✅  
  - Allows a compute instance to call OCI services **without storing credentials**.  
  - The instance is assigned an identity directly in IAM and uses **dynamic authentication tokens** from the OCI Metadata service.  
  - This is the recommended secure approach for automation on compute instances.  

---

# Question 04

**Examine this policy:**

```text
Allow group GroupMgr to manage volumes in tenancy where request.permission != 'VOLUME_DELETE'
```

Which three actions can a user belonging to the GroupMgr group perform?

- a) Create volumes.
- b) Update volumes.
- c) Move volumes.
- d) Delete volumes.

## ✅ Correct Answers: a) Create volumes, b) Update volumes, c) Move volumes

## Explanation of Choices

- **a) Create volumes** ✅
  - The manage verb in IAM policies includes permissions to create, update, move, and delete.
  - Since the condition only blocks VOLUME_DELETE, creation is still allowed.

- **b) Update volumes** ✅
  - Updating metadata, size, or tags is included in manage.
  - Not blocked by the conditional statement, so updates are permitted.

- **c) Move volumes** ✅
  - Moving resources between compartments is part of manage.
  - This is also permitted since the condition does not exclude it.

- **d) Delete volumes**
  - Blocked because the condition where request.permission != 'VOLUME_DELETE' explicitly denies deletion of volumes.

---

# Question 05

**Your application or workload includes big data, analytics, media processing, or content management. You require Portable Operating System Interface (POSIX)-compliant file system access semantics and concurrently accessible storage. Which storage service must you use?**

- a) Vault Storage  
- b) Block Storage  
- c) Object Storage  
- d) File Storage  

---

## ✅ Correct Answer: **d) File Storage**

---

## Explanation of Choices

- **a) Vault Storage**  
  - Refers to **OCI Vault**, which manages encryption keys and secrets.  
  - Not a data storage service, so it does not provide POSIX-compliant access.  

- **b) Block Storage**  
  - Provides **high-performance volumes** attached to compute instances.  
  - Suitable for databases and boot volumes but does **not support concurrent multi-instance access**.  

- **c) Object Storage**  
  - Designed for **unstructured data** (e.g., backups, images, logs).  
  - Accessed via REST APIs, not POSIX-compliant.  
  - Does not provide file system semantics.  

- **d) File Storage** ✅  
  - Fully managed **network file system (NFS)**.  
  - POSIX-compliant, supports concurrent access by multiple compute instances.  
  - Best suited for **big data, analytics, media processing, and content management workloads**.  

---


# Question 06

**Which two statements are true about boot volumes?**

- a) You can delete the boot volume that is currently attached to an instance.  
- b) You can detach a boot volume from a running instance.  
- c) You can launch another instance by using an unused boot volume.  
- d) You can create a backup of boot volumes.  

---

## ✅ Correct Answers: **c) You can launch another instance by using an unused boot volume** and **d) You can create a backup of boot volumes**

---

## Explanation of Choices

- **a) You can delete the boot volume that is currently attached to an instance**  
  - ❌ Incorrect.  
  - OCI does not allow deleting a boot volume while it’s still attached to a running or stopped instance.  
  - You must detach or terminate the instance first.  

- **b) You can detach a boot volume from a running instance**  
  - ❌ Incorrect.  
  - A boot volume cannot be detached from a **running** instance.  
  - To detach it, the instance must be **stopped** first.  

- **c) You can launch another instance by using an unused boot volume** ✅  
  - Correct.  
  - You can take an existing boot volume (not in use) and use it as the boot source to launch a new instance.  

- **d) You can create a backup of boot volumes** ✅  
  - Correct.  
  - Boot volumes can be backed up manually or through automated backup policies for disaster recovery and cloning purposes.  

---

# Question 07

**For maximum cost efficiency, when launching compute instances, which capacity type must you select for workloads that run periodically or for short periods of time and don’t require continuous availability?**

- a) On-demand capacity  
- b) Pre-emptible capacity  
- c) Reserved capacity  
- d) Dedicated capacity  

---

## ✅ Correct Answer: **b) Pre-emptible capacity**

---

## Explanation of Choices

- **a) On-demand capacity**  
  - Standard compute instances launched without reservation.  
  - Cost-effective for general use but **more expensive** than pre-emptible instances.  

- **b) Pre-emptible capacity** ✅  
  - Offered at a **significantly lower price** than on-demand.  
  - Suitable for workloads that are **fault-tolerant, periodic, or short-lived**, such as big data processing, CI/CD jobs, and batch workloads.  
  - Can be **terminated by OCI at any time** when capacity is needed elsewhere.  

- **c) Reserved capacity**  
  - Provides guaranteed compute availability and discounted pricing for long-term commitment.  
  - Best for **steady, predictable workloads**, not short-term or periodic tasks.  

- **d) Dedicated capacity**  
  - Dedicated physical servers for compliance or performance isolation.  
  - More costly, intended for workloads that require **isolation and security**, not cost efficiency.  

---

# Question 08

**Which four layers of access control are used by the File Storage service?**

- a) Oracle Cloud Infrastructure (OCI) policy  
- b) Network security  
- c) NFS export option  
- d) NFS v.3 UNIX security  
- e) Key management  
- f) Web application firewall  

---

## ✅ Correct Answers: **a) Oracle Cloud Infrastructure (OCI) policy, b) Network security, c) NFS export option, d) NFS v.3 UNIX security**

---

## Explanation of Choices

- **a) Oracle Cloud Infrastructure (OCI) policy** ✅  
  - IAM policies define **who can access and manage file systems** at the service level.  
  - Example: allowing groups to create or delete file systems.  

- **b) Network security** ✅  
  - Virtual Cloud Network (VCN) security rules and security lists control **which instances can connect** to the File Storage mount targets.  

- **c) NFS export option** ✅  
  - Defines **which clients or subnets** can mount file systems and with what permissions (read-only or read/write).  

- **d) NFS v.3 UNIX security** ✅  
  - Provides file- and directory-level access control through **UIDs, GIDs, and permission bits**.  

- **e) Key management**  
  - OCI Vault or key management services are used for **encryption**, not for access control.  
  - Protects data at rest, but does not govern who can access files.  

- **f) Web application firewall**  
  - Applies to **web applications** to filter traffic.  
  - Not relevant to NFS-based File Storage access control.  

---

# Question 09

**An organization plans to create an identity domain in the US East (Ashburn) region for a development team. However, some developers might occasionally need access to resources in the Germany (Frankfurt) region. How can OCI IAM be configured to facilitate such cross-region access?**

- a) No additional configuration is needed; users can access resources in all regions by default.  
- b) The identity domain automatically replicates to the Germany (Frankfurt) region.  
- c) The administrator can grant users permissions to access specific resources in the Germany (Frankfurt) region.  
- d) Identity domain replication must be enabled for the development domain to allow access to other regions.  

---

## ✅ Correct Answer: **c) The administrator can grant users permissions to access specific resources in the Germany (Frankfurt) region.**

---

## Explanation of Choices

- **a) No additional configuration is needed; users can access resources in all regions by default.**  
  - ❌ Incorrect.  
  - Users must be explicitly granted permissions through IAM policies to access resources across regions.  

- **b) The identity domain automatically replicates to the Germany (Frankfurt) region.**  
  - ❌ Incorrect.  
  - Identity domains are **region-specific constructs** and do not automatically replicate.  

- **c) The administrator can grant users permissions to access specific resources in the Germany (Frankfurt) region.** ✅  
  - ✔ Correct.  
  - IAM policies are **global in scope** and apply across all regions in a tenancy.  
  - By writing a policy that grants access to Frankfurt resources, users in the Ashburn domain can access them.  

- **d) Identity domain replication must be enabled for the development domain to allow access to other regions.**  
  - ❌ Incorrect.  
  - There’s no concept of enabling replication for domains. Access is managed via IAM policies, not replication.  

---

# Question 10

**Which two statements are true about site-to-site VPN?**

- a) It provides a site-to-site IPSec connection between your on-premises network and your virtual cloud network (VCN).  
- b) It encrypts IP traffic before the packets are transferred from the source to the destination and decrypts the traffic when it arrives.  
- c) You cannot use multiple site-to-site connections between your on-premises network and virtual cloud network (VCN).  
- d) The communication between the source and destination sites is unencrypted.  

---

## ✅ Correct Answers: **a) and b)**

---

## Explanation of Choices

- **a) It provides a site-to-site IPSec connection between your on-premises network and your virtual cloud network (VCN).** ✅  
  - Correct.  
  - Site-to-Site VPN in OCI uses **IPSec tunnels** to connect your on-premises network securely with your VCN.  

- **b) It encrypts IP traffic before the packets are transferred from the source to the destination and decrypts the traffic when it arrives.** ✅  
  - Correct.  
  - IPSec ensures that all data in transit is encrypted and secure.  

- **c) You cannot use multiple site-to-site connections between your on-premises network and virtual cloud network (VCN).**  
  - ❌ Incorrect.  
  - You can configure **multiple tunnels** for redundancy and high availability.  

- **d) The communication between the source and destination sites is unencrypted.**  
  - ❌ Incorrect.  
  - IPSec ensures that all traffic between the sites is **encrypted**.  
