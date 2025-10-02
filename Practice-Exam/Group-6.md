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
  - Assigns a fixed quota (e.g., `set compute quota vm-standard2-1 count to 5`).  
  - Limits resources but does **not** completely block access.  

- **b) Unset**  
  - Removes a previously applied quota policy.  
  - Restores default service limits, so access remains.  

- **c) Zero** ✅  
  - Explicitly sets the quota to **0**, blocking creation of that resource type.  
  - Example: `set compute quota vm-standard2-1 count to zero`.  

- **d) All statements have the same effect**  
  - Incorrect, since each has a unique function.  

---

# Question 02  

**Oracle Cloud Agent is a lightweight process that manages plugins running on compute instances. Which is NOT a valid Oracle Cloud Agent plugin name?**  

- a) Live Migration Agent  
- b) OS Management Service Agent  
- c) Compute Instance Run Command  
- d) Bastion  

---

## ✅ Correct Answer: **a) Live Migration Agent**  

---

## Explanation of Choices  

- **a) Live Migration Agent** ✅  
  - No such plugin exists. Live migration is handled by OCI infrastructure, not an agent plugin.  

- **b) OS Management Service Agent**  
  - Valid plugin used to manage updates and patches.  

- **c) Compute Instance Run Command**  
  - Valid plugin that allows execution of scripts/commands remotely.  

- **d) Bastion**  
  - Valid service and accessible through Cloud Agent plugin for secure connectivity.  

---

# Question 03  

**You are managing workload instances on-premises. OCI Logging is required to archive Info-level logs into Object Storage. Which TWO OCI features help achieve this?**  

- a) Cloud Agent Plugin  
- b) Grouping Function  
- c) Service Connectors  
- d) Agent Configuration  
- e) ObjectCollectionRule  

---

## ✅ Correct Answer: **a) Cloud Agent Plugin** and **c) Service Connectors**  

---

## Explanation of Choices  

- **a) Cloud Agent Plugin** ✅  
  - Collects logs from on-premises/instances and sends them to OCI Logging.  

- **b) Grouping Function**  
  - Used in monitoring queries, not for log collection or archiving.  

- **c) Service Connectors** ✅  
  - Moves logs from Logging service to Object Storage.  

- **d) Agent Configuration**  
  - Controls how an agent operates, but does not directly archive logs.  

- **e) ObjectCollectionRule**  
  - Not a valid OCI logging/archiving feature.  

---

# Question 04  

**You create a file system and add a 1 GB file. Then you take a snapshot. What would be the total meteredBytes shown after the update?**  

- a) 2 GB  
- b) 1.5 GB  
- c) 4 GB  
- d) 1 GB  

---

## ✅ Correct Answer: **a) 2 GB**  

---

## Explanation of Choices  

- **a) 2 GB** ✅  
  - File system (1 GB) + snapshot copy (1 GB) = 2 GB metered.  

- **b) 1.5 GB**  
  - Incorrect; OCI does not compress or partially meter in this way.  

- **c) 4 GB**  
  - Too high; no duplicate snapshot beyond initial copy.  

- **d) 1 GB**  
  - Wrong; snapshot storage is also metered.  

---

# Question 05  

**Which is NOT a valid statement regarding OCI Audit service?**  

- a) Retention period for Audit logs is 365 days and it cannot be changed.  
- b) Changes within the objects stored in an Object Storage bucket are collected as Audit logs.  
- c) Audit service can record REST API calls executed by a custom client.  
- d) Audit logs are displayed for Compartments.  

---

## ✅ Correct Answer: **b) Changes within the objects stored in an Object Storage bucket are collected as Audit logs.**  

---

## Explanation of Choices  

- **a) Retention period for Audit logs is 365 days**  
  - Correct and fixed by OCI.  

- **b) Changes within objects in Object Storage** ✅  
  - Incorrect — Audit records **API calls**, not the internal changes to objects.  

- **c) REST API calls by custom client**  
  - True; Audit logs capture all API calls.  

- **d) Logs are compartment-specific**  
  - True; Audit logs are viewable by compartment.  

---

# Question 06  

**Some Object Storage buckets must remain public, but Cloud Guard keeps flagging them. Which TWO ways solve this?**  

- a) Fix the baseline by configuring Conditional Groups for the detector.  
- b) Resolve or remediate the problems once; they won’t reappear.  
- c) Cloud Guard will always detect it since public buckets are risks.  
- d) Dismiss the problems associated with those resources.  

---

## ✅ Correct Answer: **a) Fix the baseline with Conditional Groups** and **d) Dismiss the problems**  

---

## Explanation of Choices  

- **a) Fix baseline with Conditional Groups** ✅  
  - Lets you define exceptions for expected configurations.  

- **b) Resolve/remediate once**  
  - Not valid — Cloud Guard will flag them again if still public.  

- **c) Cloud Guard will always detect**  
  - Incorrect — dismissals and conditional rules can prevent detection.  

- **d) Dismiss problems** ✅  
  - Valid way to prevent repeat alerts for known public buckets.  

---

# Question 07  

**You must quickly identify all users active in the last 6 hours and their REST API calls. Which OCI service do you use?**  

- a) Notifications  
- b) Service Connectors  
- c) Notifications (duplicate option)  
- d) Logging  
- e) Audit  

---

## ✅ Correct Answer: **e) Audit**  

---

## Explanation of Choices  

- **a) Notifications**  
  - Used for event alerts, not tracking API calls.  

- **b) Service Connectors**  
  - Move data between services; not for auditing.  

- **d) Logging**  
  - Captures system/application logs, not API calls.  

- **e) Audit** ✅  
  - Designed to capture **user actions + API calls**.  

---

# Question 08  

**You have an instance that cannot be live-migrated. OCI sends a maintenance due date (14–16 days). What happens if you don’t reboot before then?**  

- a) The instance will get terminated.  
- b) The instance is either reboot-migrated or rebuilt in place for you.  
- c) You will receive another notification to reboot within the next 14 days.  
- d) You will receive another notification to reboot within the next 7 days.  

---

## ✅ Correct Answer: **b) The instance is either reboot-migrated or rebuilt in place for you.**  

---

## Explanation of Choices  

- **a) Terminated**  
  - False; OCI won’t delete customer instances due to maintenance.  

- **b) Reboot-migrated or rebuilt** ✅  
  - Correct; OCI ensures availability by forcing one of these options.  

- **c) & d) More notifications**  
  - Incorrect; no extra notice, action is automatic at deadline.  

---

# Question 09  

**Which TWO components are optional in OCI Monitoring Query Language (MQL) expressions?**  

- a) Interval  
- b) Statistic  
- c) Dimensions  
- d) Grouping Function  
- e) Metric  

---

## ✅ Correct Answer: **a) Interval** and **d) Grouping Function**  

---

## Explanation of Choices  

- **a) Interval** ✅  
  - Optional; defaults to service-based value.  

- **b) Statistic**  
  - Required (e.g., avg, max, min).  

- **c) Dimensions**  
  - Required to identify which resource/metric.  

- **d) Grouping Function** ✅  
  - Optional (used to aggregate across resources).  

- **e) Metric**  
  - Mandatory; defines what is being monitored.  

---

# Question 10  

**Which statement is NOT correct regarding OCI File System snapshots?**  

- a) Even if nothing changed, a new snapshot consumes more storage.  
- b) Snapshots are accessible under `.snapshot/name` directory.  
- c) Before cloning a file system, at least one snapshot must exist.  
- d) Snapshots are consistent, point-in-time views.  

---

## ✅ Correct Answer: **a) Even if nothing changed, a new snapshot consumes more storage.**  

---

## Explanation of Choices  

- **a) New snapshot always consumes storage** ✅  
  - Incorrect — OCI snapshots are incremental; unchanged data is not duplicated.  

- **b) Accessible under `.snapshot/name`**  
  - True; snapshots are mounted under the file system.  

- **c) Clone requires at least one snapshot**  
  - Correct; cloning is snapshot-based.  

- **d) Consistent point-in-time view**  
  - True; OCI ensures consistency.  
