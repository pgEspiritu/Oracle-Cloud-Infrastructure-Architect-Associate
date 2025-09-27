# Question 1

**You create a file system and then add a 2 GB file. You then take a snapshot of the file system.  
What would be the total `meteredBytes` shown by the File Storage service after the hourly update cycle is complete?**

- A) 2 GB  
- B) 2.5 GB  
- C) 3 GB  
- D) 4 GB  

---

## ✅ Correct Answer:  
**B) 2.5 GB**

---

## Explanation of Choices

- **A) 2 GB**  
  - ❌ Incorrect.  
  - This only accounts for the file data. Snapshots also consume additional storage.  

- **B) 2.5 GB** ✅  
  - ✔ Correct.  
  - The **snapshot of the file system is incremental** and stores metadata plus any new data blocks.  
  - For a single 2 GB file, the snapshot adds roughly **0.5 GB** of overhead (metadata + snapshot tracking), resulting in **2.5 GB total meteredBytes**.  

- **C) 3 GB**  
  - ❌ Incorrect.  
  - Overestimates the snapshot overhead for a single small file.  

- **D) 4 GB**  
  - ❌ Incorrect.  
  - This would be if snapshots duplicated all data entirely, but OCI uses **space-efficient snapshots**.  

---

## 🔑 Key Takeaway
OCI File Storage **meteredBytes includes actual data + snapshot overhead**. Snapshots are incremental and **do not double the storage**, but they do add some metadata overhead.

---

# Question 2

**You are migrating several legacy virtualized applications to OCI. The current CentOS version does not match any Oracle-provided images. How would you migrate your existing virtual server images?**

- A) Export in VDI format → Object Storage → Import as custom image, **native mode**  
- B) Export in VMDK format → Object Storage → Import as custom image, **native mode**  
- C) Export in QED format → Object Storage → Import as custom image, **emulated mode**  
- D) Export in QCOW2 format → Object Storage → Import as custom image, **emulated mode**  

---

## ✅ Correct Answer:  
**B) Export your current image in the VMDK format and copy to an Object Storage bucket. Import it as a custom image. Select native mode to ensure the best possible performance.**

---

## Explanation of Choices

- **A) VDI format, native mode**  
  - ❌ Incorrect.  
  - VDI (VirtualBox Disk Image) is **not supported** for direct OCI custom image imports.  

- **B) VMDK format, native mode** ✅  
  - ✔ Correct.  
  - OCI supports **VMDK (VMware disk format)** for importing custom images.  
  - Selecting **native mode** ensures the imported image runs efficiently with OCI hypervisor.  

- **C) QED format, emulated mode**  
  - ❌ Incorrect.  
  - QED is **not a standard disk format** for OCI imports. Emulated mode is only needed for older or incompatible drivers, which is unnecessary for standard Linux images.  

- **D) QCOW2 format, emulated mode**  
  - ❌ Incorrect.  
  - QCOW2 is primarily used in **KVM environments**; OCI prefers VMDK or raw formats for custom image imports.  
  - Emulated mode reduces performance and is unnecessary if drivers are compatible.  

---

## 🔑 Key Takeaway
For migrating **existing virtualized Linux servers** to OCI:  

1. Export in **VMDK format**.  
2. Upload to **Object Storage**.  
3. Import as a **custom image**.  
4. Use **native mode** for best performance.  

---

# Question 3

**You need to create multiple instances in OCI with identical configuration and software. You already have a running instance. Which image option allows you to achieve this with minimal effort?**

- A) Bring your own image and use it as a template  
- B) Select an image from the OCI Marketplace  
- C) Create a custom image and use it as a template  
- D) Use Oracle-provided images and customize via a third-party tool  

---

## ✅ Correct Answer:  
**C) Create a custom image and use it as a template for the new instances**

---

## Explanation of Choices

- **A) Bring your own image**  
  - ❌ Incorrect.  
  - BYOI involves importing an external OS image. Since you already have a running instance, creating a **custom image from it is faster and simpler**.  

- **B) OCI Marketplace image**  
  - ❌ Incorrect.  
  - Marketplace images are pre-built vendor images. They **won’t include your specific installed software and configuration**, so additional setup would be required.  

- **C) Create a custom image** ✅  
  - ✔ Correct.  
  - A **custom image** captures the current instance **with all installed software and configuration**.  
  - It can then be used as a template to launch **identical new instances** with minimal effort.  

- **D) Oracle-provided image + third-party tool**  
  - ❌ Incorrect.  
  - This would require **manual customization** for each new instance, which is **more work than using a custom image**.  

---

## 🔑 Key Takeaway
When you need **identical instances quickly**, use a **custom image of a configured running instance** as a template.

---

# Question 4

**Which THREE protocols are supported by the Oracle Cloud Infrastructure (OCI) private Network Load Balancers (NLBs)?**

- A) HTTP  
- B) UDP  
- C) ICMP  
- D) TCP  
- E) iSCSI  
- F) BGP  

---

## ✅ Correct Answers:  
**B) UDP**  
**C) ICMP**  
**D) TCP**

---

## Explanation of Choices

- **A) HTTP**  
  - ❌ Incorrect.  
  - HTTP is a **layer 7 protocol** and is supported by **Application Load Balancers**, not Network Load Balancers.  

- **B) UDP** ✅  
  - ✔ Correct.  
  - OCI NLB supports **UDP traffic**, which allows load balancing for services like DNS or VoIP.  

- **C) ICMP** ✅  
  - ✔ Correct.  
  - NLBs support **ICMP** for network-level connectivity testing (ping/traceroute).  

- **D) TCP** ✅  
  - ✔ Correct.  
  - NLBs support **TCP traffic**, which includes custom applications using TCP ports.  

- **E) iSCSI**  
  - ❌ Incorrect.  
  - iSCSI requires **direct access**, not NLB load balancing.  

- **F) BGP**  
  - ❌ Incorrect.  
  - BGP is a routing protocol and is **not supported** by NLBs.  

---

## 🔑 Key Takeaway
OCI **Network Load Balancers** operate at **layer 4**, supporting **TCP, UDP, and ICMP** traffic, while **HTTP/HTTPS** is handled by **Application Load Balancers**.

---

# Question 5

**You have an instance in OCI that cannot be live-migrated during maintenance. OCI schedules a maintenance due date within 14–16 days and sends a notification.  
What happens if you choose not to proactively reboot the instance before the scheduled maintenance due date?**

- A) You will receive another notification to reboot within the next 14 days  
- B) The instance will get terminated  
- C) The instance is either reboot-migrated or rebuilt in place for you  
- D) You will receive another notification to reboot within the next 7 days  

---

## ✅ Correct Answer:  
**C) The instance is either reboot-migrated or rebuilt in place for you**

---

## Explanation of Choices

- **A) Another notification in 14 days**  
  - ❌ Incorrect.  
  - OCI does **not simply resend notifications**; the maintenance action will proceed automatically after the due date.  

- **B) Instance termination**  
  - ❌ Incorrect.  
  - OCI will **not terminate the instance**; it ensures maintenance by either **reboot-migrating or rebuilding in place**.  

- **C) Reboot-migrated or rebuilt in place** ✅  
  - ✔ Correct.  
  - If the instance cannot be live-migrated, OCI **automatically takes care of it** by either:  
    - Reboot-migrating it to new hardware, or  
    - Rebuilding it in place while retaining the boot and block volumes.  

- **D) Another notification in 7 days**  
  - ❌ Incorrect.  
  - OCI maintenance notifications do **not follow a fixed 7-day reminder cycle**.  

---

## 🔑 Key Takeaway
For **instances that cannot live-migrate**, OCI ensures maintenance completion automatically by **reboot-migrating or rebuilding the instance** after the scheduled due date. No manual reboot is strictly required, but proactive action can avoid downtime.

---

# Question 6

**A financial firm wants high availability and fault tolerance for financial data stored in OCI Object Storage. Data should survive even if an entire region fails. What should the architect do?**

- A) Create a lifecycle policy to regularly send data from Standard to Archive storage  
- B) Create a replication policy to send data to a different bucket in another OCI region  
- C) Copy the Object Storage bucket to a block volume  
- D) Create a new Object Storage bucket in another region and configure a lifecycle policy to move data every 5 days  

---

## ✅ Correct Answer:  
**B) Create a replication policy to send data to a different bucket in another OCI region**

---

## Explanation of Choices

- **A) Lifecycle policy from Standard → Archive**  
  - ❌ Incorrect.  
  - Lifecycle policies only manage **storage tiers within the same region**.  
  - They do **not protect against regional outages**.  

- **B) Replication policy to another region** ✅  
  - ✔ Correct.  
  - **Cross-region replication** copies objects automatically to a bucket in another OCI region.  
  - This ensures **high durability and availability**, even if the original region becomes unavailable.  

- **C) Copy bucket to block volume**  
  - ❌ Incorrect.  
  - Block volumes are **AD-specific** and not suitable for Object Storage replication or high availability across regions.  

- **D) New bucket + lifecycle every 5 days**  
  - ❌ Incorrect.  
  - Copying data manually every 5 days does **not provide real-time durability** and risks data loss between copies.  

---

## 🔑 Key Takeaway
To achieve **high availability and regional fault tolerance** in OCI Object Storage, use **cross-region replication** rather than lifecycle policies or manual copies.

---

# Question 7

**You need to create a fully redundant connection from your on-premises data center to your VCN in the us-ashburn-1 region. Which TWO options accomplish this?**

- A) Configure two FastConnect virtual circuits to us-ashburn-1 region, terminate on diverse on-prem hardware  
- B) Configure one FastConnect virtual circuit to us-ashburn-1 region and the second to us-phoenix-1 region  
- C) Configure a Site-to-Site VPN from a single on-prem CPE  
- D) Configure one FastConnect virtual circuit to us-ashburn-1 region and a Site-to-Site VPN to us-ashburn-1 region  

---

## ✅ Correct Answers:  
**A) Configure two FastConnect virtual circuits to us-ashburn-1 region, terminate on diverse on-prem hardware**  
**D) Configure one FastConnect virtual circuit to us-ashburn-1 region and a Site-to-Site VPN to us-ashburn-1 region**

---

## Explanation of Choices

- **A) Two FastConnect circuits, diverse on-prem hardware** ✅  
  - ✔ Correct.  
  - Provides **full redundancy** at the circuit level and ensures high availability if one physical path fails.  

- **B) FastConnect to two different regions** ❌  
  - ❌ Incorrect.  
  - This does **not provide redundancy for connectivity to the same region**. Each region has separate VCNs.  

- **C) Single Site-to-Site VPN** ❌  
  - ❌ Incorrect.  
  - A single VPN **does not provide redundancy**. It is a backup option but not fully redundant on its own.  

- **D) FastConnect + Site-to-Site VPN** ✅  
  - ✔ Correct.  
  - Combining **FastConnect with VPN** provides redundancy in case the dedicated FastConnect link fails.  
  - The VPN acts as a **failover path** to maintain connectivity.  

---

## 🔑 Key Takeaway
For **fully redundant connectivity** to a single OCI region:  

- Use **multiple FastConnect circuits** terminating on diverse hardware **OR**  
- Combine **FastConnect with a Site-to-Site VPN** as a backup/failover.

---

# Question 9

**Which TWO statements are true about performing a multipart upload using the Multipart Upload API in OCI Object Storage?**

- A) You do not have to commit the upload after uploading all parts  
- B) You do not need to split the object into parts  
- C) Each part can be as large as 50 GiB  
- D) You can keep adding parts as long as the total number is less than 10,000  

---

## ✅ Correct Answers:  
**C) Each part can be as large as 50 GiB**  
**D) You can keep adding parts as long as the total number is less than 10,000**

---

## Explanation of Choices

- **A) You do not have to commit the upload** ❌  
  - ❌ Incorrect.  
  - After uploading all parts, you **must commit (complete) the multipart upload** to assemble the final object.  

- **B) You do not need to split the object into parts** ❌  
  - ❌ Incorrect.  
  - Multipart upload **requires splitting the object into parts** before uploading them.  

- **C) Each part can be as large as 50 GiB** ✅  
  - ✔ Correct.  
  - OCI Object Storage allows **each part of a multipart upload up to 50 GiB**.  

- **D) Total number of parts can be up to 10,000** ✅  
  - ✔ Correct.  
  - You can keep adding parts until the **total number of parts reaches 10,000**, allowing very large objects to be uploaded efficiently.  

---

## 🔑 Key Takeaway
**Multipart uploads** are used for uploading large objects efficiently:  

- **Split the object into parts** (≤50 GiB per part)  
- **Upload each part separately**  
- **Commit the upload** to finalize the object  
- **Up to 10,000 parts** are allowed  

---

# Question 10

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
  - DRG can terminate **FastConnect virtual circuits**, enabling connectivity to on-premises networks.  

- **B) Subnet** ❌  
  - ❌ Incorrect.  
  - **Subnets attach to VCN**, not directly to DRG.  

- **C) VNIC** ❌  
  - ❌ Incorrect.  
  - **VNICs are part of compute instances**, not attached directly to a DRG.  

- **D) Remote Peering Connections** ✅  
  - ✔ Correct.  
  - DRG can connect to another DRG in a different region via **Remote Peering**.  

- **E) IPSec Tunnel** ✅  
  - ✔ Correct.  
  - DRG terminates **IPSec VPN connections**, providing secure site-to-site connectivity.  

- **F) Local Peering Connection** ❌  
  - ❌ Incorrect.  
  - **Local Peering Connections (LPCs)** are between VCNs, not attached directly to DRG.  

---

## 🔑 Key Takeaway
A **DRG** in OCI can attach:  

- **Virtual Circuits** (FastConnect)  
- **IPSec Tunnels** (VPN)  
- **Remote Peering Connections** (cross-region VCN connectivity)  

