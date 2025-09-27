# 🔒 Lesson: File Storage Security

The **File Storage Service** uses **four different layers of access control**. Let’s explore each one:

---

## 1️⃣ IAM Service (Identity and Access Management)
- Uses **policies** to control what users can do within OCI.  
- Examples:  
  - Creating instances  
  - Creating a Virtual Cloud Network (VCN) and its security rules  
  - Creating mount targets and file systems  

---

## 2️⃣ Network Security
- Controls which **instance IP addresses or CIDR blocks** can connect to a file system.  
- Uses **VCN security list rules** to allow or deny traffic to the **mount target** (and therefore access to all associated file systems).  
- You can apply:  
  - **Network Security Groups (NSGs)**  
  - **Security rules** to block specific ports, IPs, or CIDR blocks  
- ⚠️ Note: Access is **all-or-nothing** at this layer.  
  - If a client can access the mount target, it can access **all file systems** associated with it.  

---

## 3️⃣ Export Options (Interface Layer)
- Applies access control to a **file system export** based on **source IP address**.  
- Provides finer granularity on top of the **network security** and **NFS/UNIX security layers**.  

---

## 4️⃣ UNIX Security Layer
- Governs what users can do **inside the instance**.  
- Examples:  
  - Installing applications  
  - Mounting external file systems  
  - Creating directories  
  - Reading and writing files  

---

## ✅ Summary
File storage security in OCI is enforced through **four layers**:
1. **IAM Policies** (who can perform actions in OCI)  
2. **Network Security** (which IPs/CIDRs can access the mount target)  
3. **Export Options** (access per file system export)  
4. **UNIX Security** (permissions at the operating system level)  

Together, these layers provide **defense-in-depth** for protecting file storage.  
