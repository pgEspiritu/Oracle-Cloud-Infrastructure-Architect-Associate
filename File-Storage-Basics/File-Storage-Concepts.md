# Lesson: File Storage Concepts

Hello and welcome. In this lesson, we are going to discuss **file storage concepts** in Oracle Cloud Infrastructure (OCI).

---

## 🔑 Core Constructs

There are **three key constructs** in File Storage:

1. **File System**  
   - The actual storage where your files reside.  

2. **Mount Target**  
   - An **NFS endpoint** that lives in a subnet and is highly available.  
   - Provides an **IP address or DNS name** used in the `mount` command.  
   - **Exports** file systems to NFS clients.  
   - Supports **multiple file systems** using different exports.  

3. **Exports & Export Information**  
   - Control how NFS clients access file systems when connected to a mount target.  
   - Each mount target has an **export set** containing one or more exports.  
   - A file system must have **at least one export** to be mountable.  

---

## 📂 Export Details

- **Export Set**  
  A collection of one or more exports within a mount target.  

- **Export Path**  
  The **unique path** that identifies the file system within the mount target.  
  Enables **multiple file systems** to be associated with one mount target.  

- **Export Options**  
  Parameters that define **access levels** for NFS clients.  
  - Example: read/write, read-only, root squash.  
  - Up to **100 export options** per export.  

---

## 🖥️ Conceptual Flow

- **File System** → Stores files.  
- **Export** → Controls access rules (NFS layer).  
- **Mount Target** → Provides endpoint for clients to connect.  

---

## ⚙️ Steps to Mount a File System

1. **Open Ports**  
   - Update **security lists** or **network security groups** for NFS traffic.  

2. **Launch an OCI Instance**  
   - Use SSH to connect.  

3. **Install NFS Client**  
   ```bash
   sudo yum install nfs-utils -y    # On Oracle Linux / RHEL
   sudo apt-get install nfs-common  # On Ubuntu/Debian
   ```
4. Create Mount Point Directory
   ```bash
   sudo mkdir /mnt/myfss
   ```
5. Check Mount Targets in OCI Console
- Locate the mount target IP address or DNS name.

6. Mount the File System
   ```bash
   sudo mount -t nfs <MountTargetIP>:/<ExportPath> /mnt/myfss
   ```
   
---

✅ Summary
- Mount Target: The NFS endpoint in a subnet.
- Export: Controls how clients access the file system.
- File System: The storage backend.
- You can easily mount the file system to an OCI instance by installing NFS, creating a mount directory, and running the mount command.
