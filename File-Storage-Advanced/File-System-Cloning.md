# Lesson: File System Cloning

## What is File System Cloning?
- A **clone** is a new file system created based on a **snapshot** of an existing file system.  
- By taking snapshots at regular intervals, you can create clones representing the file system at multiple points in its lifetime.  
- At the time of creation:
  - The clone’s data is **identical** to the snapshot’s data.  
  - After creation, changes to the **clone** do not affect the **original file system**, and vice versa.  

⚡ **Note:** Creating a clone does not replicate or move data.  
Instead, the clone **references the parent file system** for any shared data.

---

## Example
- Snapshot created: **22AprilSnapshot**  
- From this snapshot, a new file system was cloned → **clonedfilesystem**.  
- In the clone’s details:
  - **Source Snapshot** → `22AprilSnapshot`  
  - **Hydration** → In progress (shows whether the clone is copying metadata).  
  - **Parent File System** → `ociarcassfilesystem`  
  - **Clone Root** → Indicates if the file system is the root of a cloned tree.  
  - **Descendants** → Indicates if this file system itself has been cloned.  
  - In this case, both **Clone Root** and **Descendants** = **False**.  

---

## Key Concepts of File System Cloning
### 1. Source Snapshot
- The snapshot used as a **blueprint** for creating a clone.  
- Represents a **point-in-time reference** of a file system.  

### 2. Parent File System
- The original file system that contains data referenced by one or more clones.  
- Clones continue to reference the parent for any shared data.  

### 3. Hydration
- Indicates whether the clone is **copying metadata** from the source.  
- Clones are usable even while hydration is in progress.  

### 4. Clone Tree
- A group of clones that descend from the same **root file system**.  
