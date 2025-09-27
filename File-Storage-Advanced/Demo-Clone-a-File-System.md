# Demonstration: Cloning a File System

## Step 1: Select a Snapshot
1. Navigate to your **File Systems**.  
2. Click on the file system → **demofs**.  
3. Under **Resources**, go to **Snapshots**.  
4. Select a snapshot (example: a specific dated snapshot).  
5. Click on **Clone**.  

⚡ **Note:** A clone is a copy of the file system data as it existed at the date and time of the snapshot.

---

## Step 2: Create the Clone
1. Provide a name for the clone (e.g., `Demo File System Clone`).  
2. Click **Create Clone**.  

➡️ This action creates a **new file system** from the snapshot.

---

## Step 3: Enable Access to the Clone
A clone is a new file system, but to **enable access**, you must associate it with a **mount target** by creating an **export**:

1. Go to the clone → **Exports**.  
2. Click **Create Export**.  
3. Accept the default export path or edit as needed.  
4. Under **Mount Target Information**, select an existing mount target.  
5. Click **Create**.  

Now the cloned file system is accessible.

---

## Step 4: Review Clone Details
Within the cloned file system (`demofs clone`), observe:

- **Hydration** → *In Progress*  
  - Indicates the clone is copying metadata from the source.  

- **Source Snapshot** → A link to the snapshot used to create the clone.  

- **Parent File System** → `demofs` (the original file system).  

- **Clone Root** → `False`  
  - Indicates this clone is not the root of a clone tree.  

- **Descendants** → `False`  
  - Indicates this clone itself has not been cloned.  

If you go to the **parent file system (`demofs`)**, you’ll see:
- **Clone Root** → `True`  
- **Descendants** → `True` (since it has been cloned).  

