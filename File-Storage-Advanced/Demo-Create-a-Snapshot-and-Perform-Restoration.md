# Demonstration: Creating and Restoring File System Snapshots

## Step 1: Navigate to File System in OCI Console
- Logged in as **storageadmin**.  
- Multiple file systems are available; for this demo, we will use **demofs**.  
- Under **Resources**, you can see:
  - Export Information  
  - Snapshots  
  - Metrics  

---

## Step 2: Create Snapshot from OCI Console
1. Click on **Snapshots**.  
2. Click **Create Snapshot**.  
3. Enter a name → `snapshot-12may2022`.  
4. Click **Create**.  

✅ Snapshot is now created and listed under the Snapshots tab.  

---

## Step 3: Locate Snapshots in File System
- Snapshots are created under a **hidden directory** at the root of your file system.  
- Since the file system is already mounted, you can verify:  
```text
ls -a /mnt/mountpoint
```

- You will see the hidden **.snapshot/** directory containing your snapshot.  

---

## Step 4: Create Snapshot from CLI
You can also create a snapshot using the **OCI CLI**:  
```bash
oci fs snapshot create --file-system-id <file_system_OCID> --name snapshot-12may2022-second
```
- After execution, list snapshots:
```bash
ls .snapshot/
```
✅ Both snapshot-12may2022 and snapshot-12may2022-second are visible.

---

## Step 5: Validate Snapshot Contents
- Navigate into snapshot:
```bash
cd .snapshot/snapshot-12may2022
ls
```
- Files from the file system are visible inside the snapshot.

---

## Step 6: Restore Data from Snapshot

You can restore:
1. Entire Snapshot
   ```bash
   sudo cp -r .snapshot/snapshot-12may2022/* /mnt/mountpoint/
   ```
2. Individual Files
   ```bash
   sudo cp .snapshot/snapshot-12may2022/demofile.txt /mnt/mountpoint/
   ```

✅ After restoring, verify with:
```bash
ls /mnt/mountpoint
```
You should see both demofile.txt and testfile.txt.

---

Summary

- Creating snapshots from OCI Console and OCI CLI
- Locating snapshots under the hidden .snapshot/ directory
- Restoring entire snapshots or individual files
