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
