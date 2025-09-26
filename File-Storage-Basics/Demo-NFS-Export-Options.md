# Demonstration: Working with NFS Export Options

## 🔎 Recap
- NFS Export Options are a set of parameters within the export that **specify the level of access** granted to NFS clients when they connect to a mount target.  
- You can configure them under the **Export Path** of a file system.  

---

## 🖥️ Setup
- **Instance 1 (fsdemo-instance)** → will have **Read-Write access**.  
- **Instance 2 (fsdemo-instance-readonly)** → will have **Read-Only access**.  

Both instances have:  
- NFS client installed  
- A mount point directory created  
- The file system mounted  

---

## ⚙️ Configuring Export Options
1. Navigate to the file system → **Export Path → Edit**.  
2. Add Export Options for **Instance 1 (Read-Write)**:  
   - Source: Private IP of `fsdemo-instance`  
   - Access: **Read-Write**  

3. Add Export Options for **Instance 2 (Read-Only)**:  
   - Source: Private IP of `fsdemo-instance-readonly`  
   - Access: **Read-Only**  
   - Ports: Any  

Click **Update**.  

---

## 🧪 Testing Access
### ✅ Instance 1 (Read-Write)
- Create a file: success.  
- Verify files:  
```text
ls
demofile.txt testfile.txt
```
- Can **read and write**.  

### ❌ Instance 2 (Read-Only)
- Try creating a file: fails (`Permission denied`).  
- Can list and read files created by Instance 1:  
- `demofile.txt`  
- `testfile.txt`  
- Cannot modify content.  

---

## ➕ Creating Another File System with Same Mount Target
1. Go to **File Systems → Create File System**.  
2. Name: `demofstwo`  
3. Specify an **Export Path** (e.g., `/demofstwo`).  
4. Select the **existing mount target** (`demo-mount-target`).  
5. Create.  

Now:  
- Two file systems exist (`demofs`, `demofstwo`).  
- Both share the same mount target but have **different export paths**.  

---

## 🎉 Conclusion
- We configured **NFS Export Options** to grant different access (Read-Write vs Read-Only) to two instances.  
- Verified that access permissions worked as expected.  
- Demonstrated how to **create multiple file systems with the same mount target** using unique export paths.  
