# Question 01  

**You need to implement automatic backups for your database system. You can easily check “Enable Automatic Backup” in the web console. Before you do that though, you need to have which of the following TWO prerequisites in place?**  

- a) Access to the OCI Object Storage service  
- b) Private SSH key to the database  
- c) VCN configured with VPN for secure access to the Oracle Cloud Infrastructure (OCI) Object Storage service  
- d) Connectivity to Swift endpoints  

---

## ✅ Correct Answer: **a) Access to the OCI Object Storage service** and **d) Connectivity to Swift endpoints**  

---

## Explanation of Choices  

- **a) Access to OCI Object Storage** ✅  
  - Required because automatic backups store database backups in Object Storage.  

- **b) Private SSH key**  
  - Not required for enabling automatic backups via the console.  

- **c) VCN with VPN**  
  - Not necessary for automatic backup; connectivity is handled by OCI.  

- **d) Connectivity to Swift endpoints** ✅  
  - Required because the backup service communicates with Object Storage through Swift-compatible endpoints.  

---

# Question 02  

**A customer’s webserver runs a complicated application on three Baremetal instances behind an OCI public Load Balancer. If one instance fails, what will the OCI Load Balancer do?**  

- a) It will send an SOS notification  
- b) It will fix the failing Baremetal instance  
- c) It will delete the failing Baremetal instance  
- d) It will launch an API call  
- e) It will no longer send traffic to it  

---

## ✅ Correct Answer: **e) It will no longer send traffic to it**  

---

## Explanation of Choices  

- **a) Send an SOS notification**  
  - Incorrect; Load Balancer does not send SOS alerts.  

- **b) Fix the failing instance**  
  - Incorrect; OCI cannot auto-repair a Baremetal instance.  

- **c) Delete the failing instance**  
  - Incorrect; deletion is not automatic.  

- **d) Launch an API call**  
  - Incorrect; Load Balancer only manages traffic.  

- **e) No longer send traffic** ✅  
  - Correct; OCI Load Balancer performs health checks and stops routing traffic to unhealthy instances.  

---

# Question 03  

**Which THREE protocols are supported by the OCI Network Load Balancer?**  

- a) HTTP  
- b) UDP  
- c) BGP  
- d) TCP  
- e) ICMP  
- f) iSCSI  

---

## ✅ Correct Answer: **b) UDP**, **d) TCP**, and **a) HTTP**  

---

## Explanation of Choices  

- **a) HTTP** ✅  
  - Supported at the application layer via NLB listener.  

- **b) UDP** ✅  
  - Supported by Network Load Balancer for traffic routing.  

- **c) BGP**  
  - Not supported by NLB; routing protocol, not a load balancer protocol.  

- **d) TCP** ✅  
  - Supported; NLB can handle TCP traffic.  

- **e) ICMP**  
  - Not supported; used for ping/traceroute, not for load balancing.  

- **f) iSCSI**  
  - Not a supported protocol for NLB.  

---

# Question 04  

**In which TWO ways does Cloud Guard help improve the overall security posture for your tenancy?**  

- a) Monitors unauthorized or suspicious user activity  
- b) Allows you to centrally manage encryption keys  
- c) Prevents you from creating misconfigurations on your resources  
- d) Masks sensitive data and monitors security controls on your Oracle databases  
- e) Helps detect misconfigured resources, such as publicly accessible Object Storage buckets, instances, and restricted ports on security lists  

---

## ✅ Correct Answer: **a) Monitors unauthorized or suspicious user activity** and **e) Helps detect misconfigured resources**  

---

## Explanation of Choices  

- **a) Monitors suspicious activity** ✅  
  - Cloud Guard monitors security violations or unusual user actions.  

- **b) Manage encryption keys**  
  - Done by OCI Vault, not Cloud Guard.  

- **c) Prevents misconfigurations**  
  - Cloud Guard detects but does not prevent creation of misconfigurations.  

- **d) Masks sensitive data**  
  - Not a function of Cloud Guard.  

- **e) Detects misconfigured resources** ✅  
  - Cloud Guard evaluates resources for security risks and policy violations.  

---

# Question 05  

**Your storage administrator cannot associate an encryption key from an existing Vault to a new Object Storage bucket. What could be a possible reason?**  

- a) The Object Storage bucket policy lacks the necessary Access Control List (ACL)  
- b) The storage administrator forgot to select "Encrypt using Oracle managed keys" while creating the bucket  
- c) There is no IAM policy that allows the Object Storage service to use the key  
- d) The secret for the key was not created beforehand  

---

## ✅ Correct Answer: **c) There is no IAM policy that allows the Object Storage service to use the key**  

---

## Explanation of Choices  

- **a) Bucket ACL**  
  - Not related to associating Vault keys.  

- **b) Forgot to select Oracle managed keys**  
  - This is the alternative encryption; not required if using a Vault key.  

- **c) No IAM policy for Object Storage to use the key** ✅  
  - Correct; the service needs explicit permissions to access the Vault key.  

- **d) Secret not created**  
  - Vault key secret exists automatically; not required to create separately.  

---

# Question 06  

**You want to protect a VM.Standard2.24 instance from low-level threats such as rootkits or bootkits. What should you do?**  

- a) Use in-transit encryption  
- b) Use Vulnerability Scanning Service  
- c) Create a burstable instance  
- d) Create a shielded instance  

---

## ✅ Correct Answer: **d) Create a shielded instance**  

---

## Explanation of Choices  

- **a) In-transit encryption**  
  - Protects network traffic, not firmware or OS threats.  

- **b) Vulnerability Scanning**  
  - Detects vulnerabilities, does not prevent firmware-level attacks.  

- **c) Burstable instance**  
  - Cost/performance type, unrelated to security.  

- **d) Shielded instance** ✅  
  - Designed to protect against rootkits/bootkits using secure boot and hardware protections.  

---

# Question 07  

**You want to reserve the following compute capacity across at least two Availability Domains: 10 VM.Standard2.2 and 6 VM.Standard.E4.Flex. At a bare minimum, how many capacity reservations should you create?**  

- a) Two  
- b) Three  
- c) One  
- d) Four  

---

## ✅ Correct Answer: **a) Two**  

---

## Explanation of Choices  

- **a) Two** ✅  
  - Minimum one per Availability Domain; two ADs cover high availability.  

- **b) Three**  
  - More than needed; only two ADs required.  

- **c) One**  
  - Not sufficient for two ADs; violates high availability requirement.  

- **d) Four**  
  - Over-provisioning; unnecessary.  

---

# Question 08  

**Before enabling automatic backups for a database in the web console, which TWO prerequisites must be in place?**  

- a) Access to the OCI Object Storage service  
- b) Private SSH key to the database  
- c) VCN configured with VPN for secure access to OCI Object Storage service  
- d) Connectivity to Swift endpoints  

---

## ✅ Correct Answer: **a) Access to the OCI Object Storage service** and **d) Connectivity to Swift endpoints**  

---

## Explanation of Choices  

- **a) Access to Object Storage** ✅  
  - Required for storing backups.  

- **b) Private SSH key**  
  - Not required; backup handled by OCI.  

- **c) VCN with VPN**  
  - Not mandatory for backup functionality.  

- **d) Connectivity to Swift endpoints** ✅  
  - Needed for backup communication with Object Storage.  

---

# Question 09  

**Which statement is true regarding the run command feature in OCI Compute service?**  

- a) The run command feature does not require any Oracle Cloud Agent plugins to be enabled and running  
- b) The run command feature is not supported on compute instances that use Windows Server images  
- c) You cannot run commands on an instance if the instance does not have SSH access or open inbound ports  
- d) The maximum size for a script file uploaded directly to an instance in plain text is 4 KB  

---

## ✅ Correct Answer: **d) Maximum script size is 4 KB**  

---

## Explanation of Choices  

- **a) Agent not required**  
  - Incorrect; Cloud Agent must be enabled and running.  

- **b) Not supported on Windows**  
  - Incorrect; supported on both Linux and Windows.  

- **c) Cannot run without SSH/open ports**  
  - Incorrect; run command works even without SSH/open inbound ports.  

- **d) Max script size 4 KB** ✅  
  - Correct; plain text scripts uploaded directly cannot exceed 4 KB.  

---

# Question 10  

**Which TWO statements are NOT correct regarding OCI burstable instances?**  

- a) If the instance's average CPU utilization over the past 24 hours is below the baseline, the system allows it to burst above the baseline  
- b) Baseline utilization is a fraction of each CPU core, either 25% or 75%  
- c) Burstable instances cost less than regular instances with the same total OCPU count  
- d) Burstable instances are designed for scenarios where an instance is not typically idle and has high CPU utilization  
- e) Burstable instances are charged according to the baseline OCPU  

---

## ✅ Correct Answer: **d) Burstable instances are designed for scenarios where an instance is not typically idle** and **e) Burstable instances are charged according to the baseline OCPU**  

---

## Explanation of Choices  

- **a) Bursts above baseline if average utilization below baseline** ✅  
  - Correct; allows temporary higher CPU usage.  

- **b) Baseline utilization fraction** ✅  
  - True; usually 25% or 75% per CPU.  

- **c) Cost less than regular instances** ✅  
  - True; billed based on baseline and burst capability.  

- **d) Designed for high CPU, not idle** ✅  
  - Incorrect; burstable is intended for **low-utilization workloads**.  

- **e) Charged according to baseline OCPU** ✅  
  - Incorrect; charges are based on consumed burstable CPU credits, not strictly baseline.  
