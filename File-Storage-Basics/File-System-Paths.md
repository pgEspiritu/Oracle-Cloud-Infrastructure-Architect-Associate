# Lesson: File System Paths

## Types of File System Paths

File Storage Service uses **three kinds of paths**:

1. **Export Paths**
2. **Mount Point Paths**
3. **File System Paths**

---

### 1. Export Paths
- Export path uniquely identifies the file system within the **mount target**.  
- You can associate **up to 100 file systems** behind a single mount target.  
- This path is unrelated to any path within the file system or the client instance.  
- The export path is used by an instance to **mount (logically attach) to the file system**.  
- **Important:** Export paths **cannot be edited** after the export is created.  

**Example:**  
An export path like `/cifs_export` uniquely identifies a file system within a target.

---

### 2. Mount Point Paths
- Mount point paths are **within a client instance**.  
- They point to a **locally accessible directory** to which the remote file system is mounted.  

**Example Command:**  
```bash
mount 10.0.0.25:/cifs_export /mnt/mountpointA
```
Here, /mnt/mountpointA is the mount point path on the client instance.

---

### 3. File System Paths
- File system paths are directories within the file system.
- They contain the actual contents of the file system.
- Once the file system is mounted, you can create any directory structure within it.
Snapshots Example:
Snapshots can be accessed using the file system path under the root directory:
```bash
/.snapshot/<snapshot_name>
```
If you create a snapshot called April22, you can access it at:
```bash
/.snapshot/April22
```

---

Summary
In this lesson, we discussed:
- Export Paths – identify file systems within a mount target
- Mount Point Paths – directories on client instances where file systems are mounted.
- File System Paths – internal directory paths containing data and snapshots.

