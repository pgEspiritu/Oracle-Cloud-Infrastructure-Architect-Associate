# Lesson: NFS Export Options

## 📌 What are NFS Export Options?
- NFS Export Options enable **granular access control**.  
- You can specify **access levels** for **IP addresses or CIDR blocks** connecting through exports in a mount target.  
- Access can be restricted so that each client’s file system is **isolated** and **invisible** to others.  
- Export Options define the **level of access** granted to NFS clients.  

---

## 🖼️ Example Scenario
We have:  
- **File System A** and **File System B**  
- **Client X** (`10.0.0.0/24`)  
- **Client Y** (`10.0.1.0/24`)  

### Requirements
- Client X → **Read-Write** access to **File System A**, **no access** to **File System B**  
- Client Y → **Read-Only** access to **File System B**, **no access** to **File System A**  

### Implementation
- Export Options for **File System A**:  
  - Source: `10.0.0.0/24`  
  - Access: **Read-Write**  

- Export Options for **File System B**:  
  - Source: `10.0.1.0/24`  
  - Access: **Read-Only**  

🔑 **Tip**: To **completely deny access**, ensure the client’s IP or CIDR block is **not included** in any export for the mount target.  

---

## ⚠️ First-Match Behavior
- File Storage Service applies the **first matching export option** for the client source IP.  
- Once matched, the **rest are ignored**.  

### Example:
- Entry 1: Source `10.0.0.0/16`, Access = **Read-Only**  
- Entry 2: Source `10.0.0.8`, Access = **Read-Write**  

If a client from `10.0.0.8` connects:  
- The **first entry matches** (`10.0.0.8` ∈ `10.0.0.0/16`).  
- Access = **Read-Only**, even though the second entry specifies Read-Write.  

---

## 🔧 Export Options Parameters
1. **Source**  
   - IP address or CIDR block of the connecting NFS client.  

2. **Ports**  
   - Can be **Privileged** (root-only) or **Any**.  

3. **Access**  
   - **Read-Only (RO)**  
   - **Read-Write (RW)**  

4. **Squash**  
   - Controls user/group ID mapping to anonymous values.  
   - Options:  
     - **All** → All users & groups remapped  
     - **Root** → Only root UID/GID remapped  
     - **None** → No remapping  

---

## 🎉 Conclusion
- NFS Export Options allow **fine-grained access control** for clients.  
- Use **CIDR-based rules** to permit or deny access.  
- Remember: **First match wins**.  
- Key options include **Source, Ports, Access, and Squash**.  
