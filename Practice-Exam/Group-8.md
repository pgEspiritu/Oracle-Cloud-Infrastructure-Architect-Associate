# Question 01  

**Your cloud developer is using the OCI Vault service to encrypt plaintext via CLI and encounters a service error. What is the most likely reason?**  

- a) The developer forgot to specify the region  
- b) The developer should pass the key version OCID instead of the key OCID  
- c) The developer has the wrong endpoint  
- d) The plaintext needs to be in JSON form  

---

## ✅ Correct Answer: **b) The developer should pass the key version OCID instead of the key OCID**  

---

## Explanation of Choices  

- **a) Forgot to specify region**  
  - Incorrect; region is derived from the endpoint URL.  

- **b) Use key version OCID** ✅  
  - Correct; encryption operations require the **key version OCID**, not the parent key OCID.  

- **c) Wrong endpoint**  
  - Endpoint seems correct in the example.  

- **d) Plaintext must be JSON**  
  - Incorrect; plaintext is passed as base64-encoded text, not JSON.  

---

# Question 02  

**You want to run compute VM instances and have these requirements: 1) No shared infrastructure, 2) Node-based licensing. Which compute capacity type would you select?**  

- a) Dedicated host  
- b) Preemptible capacity  
- c) Capacity reservation  
- d) On-demand capacity  

---

## ✅ Correct Answer: **a) Dedicated host**  

---

## Explanation of Choices  

- **a) Dedicated host** ✅  
  - Provides a physical server dedicated to a single tenancy; meets licensing and isolation requirements.  

- **b) Preemptible capacity**  
  - Lower cost, shared infrastructure, can be reclaimed.  

- **c) Capacity reservation**  
  - Reserves OCPUs, but may not meet licensing requirements.  

- **d) On-demand capacity**  
  - Shared infrastructure; does not meet isolation requirement.  

---

# Question 03  

**Regarding multipart upload of a 3 TiB file to OCI Object Storage, which TWO statements are true?**  

- a) You do not need to split the object; Object Storage does it automatically  
- b) You can keep adding parts as long as total number < 10,000  
- c) You do not have to commit the upload after uploading all parts  
- d) Each part can be as large as 50 GiB  

---

## ✅ Correct Answer: **b) You can keep adding parts as long as total number < 10,000** and **d) Each part can be as large as 50 GiB**  

---

## Explanation of Choices  

- **a) Object Storage splits automatically**  
  - Incorrect; the client must split the object into parts.  

- **b) Keep adding parts** ✅  
  - Correct; a multipart upload supports up to 10,000 parts.  

- **c) Do not have to commit**  
  - Incorrect; you must commit (complete) the multipart upload to assemble the object.  

- **d) Each part max 50 GiB** ✅  
  - Correct; each part can be up to 50 GiB.  

---

# Question 04  

**What security consideration should you be mindful of before performing a database migration?**  

- a) Place the database in restricted mode during migration  
- b) Migration can only be done via web interface  
- c) Encrypt all files used for migration  
- d) Backup and restore TDE wallets from source to target  

---

## ✅ Correct Answer: **d) Backup and restore TDE wallets from source to target**  

---

## Explanation of Choices  

- **a) Restricted mode**  
  - Not mandatory; may be optional depending on method.  

- **b) Web interface only**  
  - Incorrect; migration can use CLI, Data Pump, RMAN, or other tools.  

- **c) Encrypt files**  
  - Good practice, but TDE wallets are critical for encryption.  

- **d) Backup/restore TDE wallets** ✅  
  - Correct; required to maintain encrypted database integrity after migration.  

---

# Question 05  

**You have a block volume with Cross Region Replication enabled. How do you create a new volume from the replica in the destination region?**  

- a) Activate the replica  
- b) Trigger the replica  
- c) No action required  
- d) Initiate the replica  

---

## ✅ Correct Answer: **c) No action required**  

---

## Explanation of Choices  

- **a) Activate**  
  - Not required; replica is automatically usable.  

- **b) Trigger**  
  - Triggering applies to replication schedule; not needed to create a new volume.  

- **c) No action required** ✅  
  - Correct; the replica can be directly used to create a volume.  

- **d) Initiate**  
  - Incorrect; initialization not required.  

---

# Question 06  

**You need daily backups for boot volumes and 6-hour backups for block volumes. How can you meet this requirement?**  

- a) Create clones of all volumes one at a time  
- b) Group boot volumes into a volume group and create a custom backup policy; group block volumes similarly  
- c) On-demand full backups for block volumes and custom images for boot volumes, run via function  
- d) Group multiple storage volumes in a volume group and create volume group backups  

---

## ✅ Correct Answer: **b) Group boot volumes into a volume group and create a custom backup policy; group block volumes similarly**  

---

## Explanation of Choices  

- **a) Clone one at a time**  
  - Inefficient and not automated.  

- **b) Volume groups + custom backup policies** ✅  
  - Correct; allows different schedules for boot vs. block volumes.  

- **c) On-demand and custom images**  
  - Requires manual intervention; not ideal.  

- **d) Single volume group backup**  
  - Cannot set different schedules per type.  

---

# Question 07  

**After migrating to Autonomous Data Warehouse and Oracle Analytics Cloud, how can you separate month-end jobs and daily analytics into different consumer groups?**  

- a) High for analytics, low for month-end jobs  
- b) High for month-end jobs, medium for analytics  
- c) Medium for month-end jobs, low for analytics  
- d) High for both  

---

## ✅ Correct Answer: **b) High for month-end jobs, medium for analytics**  

---

## Explanation of Choices  

- **a) High for analytics, low for month-end**  
  - Month-end jobs are long-running; need higher priority.  

- **b) High for month-end jobs, medium for analytics** ✅  
  - Correct; month-end gets more resources, analytics uses medium.  

- **c) Medium for month-end, low for analytics**  
  - Month-end may starve with medium.  

- **d) High for both**  
  - Wasteful; medium priority is enough for analytics.  

---

# Question 08  

**Regarding scaling a Virtual Machine DB System during a workload spike, which TWO statements are true?**  

- a) You can only scale up, not down  
- b) You can scale storage without downtime  
- c) You can only scale OCPUs, not storage  
- d) Scaling operations only after DB system is down  
- e) You can change the shape to adjust OCPU cores  

---

## ✅ Correct Answer: **b) You can scale storage without downtime** and **e) You can change the shape to adjust OCPU cores**  

---

## Explanation of Choices  

- **a) Only scale up**  
  - Incorrect; you can scale up or down depending on shape.  

- **b) Scale storage without downtime** ✅  
  - Correct; OCI allows online storage scaling.  

- **c) Only scale OCPUs**  
  - Incorrect; storage scaling is also supported.  

- **d) Scaling only when DB down**  
  - Incorrect; many scaling operations can be online.  

- **e) Change shape to adjust OCPUs** ✅  
  - Correct; shape change allows increasing or decreasing CPU count.  

---

# Question 09  

**Which statement is true about cloning a database system?**  

- a) Cloning creates a copy as it exists at a later time  
- b) Cloning creates a copy as it exists at the time of scheduling  
- c) Cloning creates a copy as it exists at the time of cloning  
- d) Cloning creates a copy as it exists at an earlier time  

---

## ✅ Correct Answer: **c) Cloning creates a copy as it exists at the time of cloning**  

---

## Explanation of Choices  

- **a) Later time**  
  - Incorrect; clone reflects the database at cloning time.  

- **b) Time of scheduling**  
  - Incorrect; scheduling time may be earlier than actual cloning.  

- **c) Time of cloning** ✅  
  - Correct; clone captures DB state at cloning execution.  

- **d) Earlier time**  
  - Incorrect; clone is not a historical copy.  

---

# Question 10  

**In an Object Storage bucket, you have ObjectA (modified 6 months ago) and ObjectB (14 months ago). You create a retention rule of 1 year. What does the rule do?**  

- a) Prevents modification/deletion of ObjectA for 12 months, ObjectB for 14 months  
- b) Prevents modification/deletion of both for 12 months  
- c) Prevents modification/deletion of ObjectA for 6 months, allows ObjectB  
- d) Prevents modification/deletion of ObjectA for 6 months, ObjectB for 2 months  

---

## ✅ Correct Answer: **d) Prevents modification/deletion of ObjectA for 6 months, ObjectB for 2 months**  

---

## Explanation of Choices  

- **a) 12/14 months**  
  - Incorrect; retention counts from object creation/modification.  

- **b) 12 months for both**  
  - Incorrect; ObjectB already older than 12 months, rule only enforces remaining period.  

- **c) ObjectA 6 months, ObjectB allowed**  
  - Incorrect; ObjectB still has 2 months remaining for 1-year retention.  

- **d) ObjectA 6 months, ObjectB 2 months** ✅  
  - Correct; ObjectA: 12-6=6 months remaining; ObjectB: 12-14=-2 months → prevents modification/deletion for 2 more months.  
