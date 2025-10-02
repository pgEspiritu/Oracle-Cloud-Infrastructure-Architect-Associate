# Question 01  

**Which TWO statements about the OCI File Storage Service are accurate?**  

- a) Communication with file systems in a mount target is encrypted via HTTPS  
- b) File systems use Oracle-managed keys by default  
- c) Customer can encrypt data in their file system using their own Vault encryption key  
- d) Mount targets use Oracle-managed keys by default  
- e) Customer can encrypt the communication to a mount target via export options  

---

## ✅ Correct Answer: **b) File systems use Oracle-managed keys by default** and **c) Customer can encrypt data in their file system using their own Vault encryption key**  

---

## Explanation of Choices  

- **a) Communication encrypted via HTTPS**  
  - Incorrect; NFS communication is not over HTTPS, but can be encrypted using NFSv4.1 or export options.  

- **b) Oracle-managed keys by default** ✅  
  - File Storage uses Oracle-managed keys unless the customer specifies a Vault key.  

- **c) Customer Vault encryption key** ✅  
  - Correct; users can provide their own encryption key stored in OCI Vault.  

- **d) Mount targets use Oracle-managed keys**  
  - Incorrect; mount targets themselves do not have encryption keys.  

- **e) Encrypt communication via export options**  
  - Partially correct; encryption is done via NFSv4.1 options, not general export options.  

---

# Question 02  

**Which TWO are key benefits of setting up Site-to-Site VPN on OCI?**  

- a) Creates a private connection that provides consistent network experience  
- b) Customers can configure it to use static or dynamic routing (BGP)  
- c) OCI provisions redundant VPN tunnels  
- d) Customers can expect bandwidth above 2 Gbps  

---

## ✅ Correct Answer: **b) Customers can configure static or dynamic routing (BGP)** and **c) OCI provisions redundant VPN tunnels**  

---

## Explanation of Choices  

- **a) Private connection with consistent network**  
  - Incorrect; VPN uses public internet, so network performance may vary.  

- **b) Static or dynamic routing** ✅  
  - Correct; supports both static and BGP-based routing.  

- **c) Redundant VPN tunnels** ✅  
  - Correct; OCI automatically provisions two tunnels for redundancy.  

- **d) Bandwidth above 2 Gbps**  
  - Incorrect; bandwidth is limited by internet connection and VPN device, not guaranteed.  

---

# Question 03  

**You need to retain logs 60 days (15 days on boot volume, 60 days total). What is the most cost-effective solution?**  

- a) Terminate instance while preserving boot volume and create DenseIO instance  
- b) Create Object Storage bucket, move logs older than 15 days, use lifecycle rule  
- c) Do not delete logs; resize boot volume as needed  
- d) Attach block volume, move logs older than 15 days, delete after 60 days  

---

## ✅ Correct Answer: **b) Create Object Storage bucket, move logs older than 15 days, use lifecycle rule**  

---

## Explanation of Choices  

- **a) Terminate instance**  
  - Overkill and unnecessary.  

- **b) Object Storage + lifecycle rule** ✅  
  - Correct; keeps 15 days on boot volume, remaining 45 days in Object Storage, cost-efficient.  

- **c) Resize boot volume**  
  - Inefficient and costly over time.  

- **d) Attach block volume**  
  - Extra cost; Object Storage is cheaper for long-term retention.  

---

# Question 04  

**To create a fully redundant connection from on-premises to OCI in us-ashburn-1, which TWO options work?**  

- a) Configure two FastConnect virtual circuits to us-ashburn-1 on diverse hardware  
- b) Configure a Site-to-Site VPN from a single on-prem CPE  
- c) Configure one FastConnect to us-ashburn-1 and one to us-phoenix-1  
- d) Configure one FastConnect to us-ashburn-1 and a Site-to-Site VPN to us-ashburn-1  

---

## ✅ Correct Answer: **a) Two FastConnect circuits to us-ashburn-1 on diverse hardware** and **d) FastConnect + Site-to-Site VPN to us-ashburn-1**  

---

## Explanation of Choices  

- **a) Two FastConnect circuits** ✅  
  - Correct; provides redundancy within the same region.  

- **b) Single VPN**  
  - Incorrect; single VPN not redundant.  

- **c) FastConnect to two regions**  
  - Incorrect; cross-region circuits do not provide redundancy in a single region.  

- **d) FastConnect + VPN** ✅  
  - Correct; combination provides redundancy if one link fails.  

---

# Question 05  

**You have a memory-intensive application on a Linux instance pool. How to autoscale to prevent poor performance?**  

- a) Install OCI SDK and trigger autoscaling via script  
- b) Configure autoscaling policy to monitor memory usage  
- c) Install monitoring agent to trigger autoscaling  
- d) Configure autoscaling policy to monitor CPU usage  

---

## ✅ Correct Answer: **b) Configure autoscaling policy to monitor memory usage**  

---

## Explanation of Choices  

- **a) OCI SDK + script**  
  - Manual, not recommended.  

- **b) Monitor memory usage** ✅  
  - Correct; memory metric triggers scale-up to prevent performance degradation.  

- **c) Monitoring agent triggers autoscaling**  
  - Agent collects metrics; policy still needed.  

- **d) Monitor CPU usage**  
  - Incorrect; memory-intensive application may need memory-based scaling.  

---

# Question 06  

**Which OCI Object Storage tier is suitable for backups retained ≥31 days and accessible immediately?**  

- a) Infrequent Access tier  
- b) Archive tier  
- c) Standard tier  
- d) Auto-Tiering tier  

---

## ✅ Correct Answer: **c) Standard tier**  

---

## Explanation of Choices  

- **a) Infrequent Access**  
  - Cheaper but has slightly higher access latency; may not be immediate.  

- **b) Archive**  
  - Retrieval delay; not suitable for immediate access.  

- **c) Standard tier** ✅  
  - Correct; immediately accessible and reliable for 31+ day retention.  

- **d) Auto-Tiering**  
  - Optimizes cost automatically; could introduce latency.  

---

# Question 07  

**Which TWO statements are TRUE about Private IP addresses in OCI?**  

- a) Each VNIC can only have one private IP  
- b) Primary VNIC of an instance has one primary private IP by default  
- c) Primary VNIC has one primary and one secondary IP by default  
- d) Private IP can have an optional public IP if in a public subnet  

---

## ✅ Correct Answer: **b) Primary VNIC has one primary private IP by default** and **d) Private IP can have an optional public IP in a public subnet**  

---

## Explanation of Choices  

- **a) Only one private IP per VNIC**  
  - Incorrect; secondary private IPs are allowed.  

- **b) Primary private IP** ✅  
  - Correct; every primary VNIC has one default private IP.  

- **c) One primary + one secondary**  
  - Incorrect; secondary IPs are optional.  

- **d) Optional public IP** ✅  
  - Correct; public IP can be assigned to private IP in a public subnet.  

---

# Question 08  

**Which is a valid RFC 1918 CIDR prefix for creating an OCI VCN?**  

- a) 192.168.0.0/16  
- b) 172.16.0.0/12  
- c) 10.0.0.0/8  
- d) 0.0.0.0/0  
- e) 192.268.0.0/24  
- f) 189.215.154.89/32  

---

## ✅ Correct Answer: **a) 192.168.0.0/16**, **b) 172.16.0.0/12**, **c) 10.0.0.0/8**  

---

## Explanation of Choices  

- **a, b, c** ✅  
  - Correct; all are valid private RFC 1918 prefixes.  

- **d) 0.0.0.0/0**  
  - Incorrect; represents all addresses, not private.  

- **e) 192.268.0.0/24**  
  - Invalid; octet 268 > 255.  

- **f) 189.215.154.89/32**  
  - Public IP; not private CIDR.  

---

# Question 09  

**How to ensure Object Storage data survives an AD or region outage for a financial application?**  

- a) Create replication policy to another bucket in a different region  
- b) Copy bucket to a block volume  
- c) Lifecycle policy to move data from Standard to Archive  
- d) Create new bucket in another region and move data every 5 days  

---

## ✅ Correct Answer: **a) Create replication policy to another bucket in a different region**  

---

## Explanation of Choices  

- **a) Replication to another region** ✅  
  - Correct; ensures cross-region redundancy for high availability and durability.  

- **b) Copy to block volume**  
  - Incorrect; block volumes are AD-specific, not cross-region.  

- **c) Lifecycle to Archive**  
  - Only changes storage tier; does not protect against AD/region failures.  

- **d) Move every 5 days**  
  - Manual and costly; replication policy is automated.  

---

# Question 10  

**Which statement is NOT true about OCI Object Storage?**  

- a) Object Versioning is enabled at the namespace level  
- b) Object Storage resources can be shared across tenancies  
- c) Object lifecycle rules can archive or delete objects  
- d) Immutable option can be set via retention rules  

---

## ✅ Correct Answer: **b) Object Storage resources can be shared across tenancies**  

---

## Explanation of Choices  

- **a) Object Versioning at namespace level**  
  - True; versioning is namespace-level setting.  

- **b) Shared across tenancies** ❌  
  - False; buckets and objects are tenancy-specific; cannot be shared across tenancies.  

- **c) Lifecycle rules for archive/delete**  
  - True; supports both actions.  

- **d) Immutable via retention rules**  
  - True; retention rules enforce immutability for specified period.  
