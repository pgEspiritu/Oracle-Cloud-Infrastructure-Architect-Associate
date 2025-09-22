# 📦 OCI Demonstration – Resizing a Block Volume & Extending the Partition

## 🖥️ Setup
- Created a block volume: **demo-volume (1024 GB / 1 TB)**.  
- Attached to an instance: **demo-instance**.  
  - Attachment type: **Paravirtualized**  
  - Access: **Read/Write**  
  - Device path configured.  
- Connected to instance via **SSH**.  

---

## 🔹 Step 1 – Verify Block Device
```bash
lsblk
```
- Confirms block device available at 1024 GB.

---

## Step 2 – Create Partition & Mount
```bash
fdisk /dev/sdX    # n → p → defaults
mkfs.ext4 /dev/sdX1
mkdir /mnt/demo
mount /dev/sdX1 /mnt/demo
```
- Partition created, formatted, and mounted.
- Size confirmed: 1 TB.

---

## Step 3 – Resize Volume in OCI Console
- In OCI Console → Edit Volume.
- Change size: 1 TB → 2 TB (2048 GB).
- Save changes.
- Console reflects new size (2 TB) but inside instance still shows 1 TB.

---

## Step 4 – Rescan Device
```bash
# Example rescan command
echo 1 > /sys/class/block/sdX/device/rescan
```
- After rescan:
  - Disk now shows 2 TB.
  - Partition still 1 TB (1024 GB).
 
--- 

## Step 5 – Extend Partition
```bash
parted /dev/sdX
(parted) print             # Note Start value (e.g., 2048)
(parted) rm 1              # Remove old partition
(parted) mkpart primary ext4 2048s 100%
(parted) quit
```
- Partition table updated.
- Partition size now reflects 2 TB.

---

## Step 6 – Grow File System
```bash
resize2fs /dev/sdX1
```
- File system extended to match new partition size.
- Verified with:
```bash
df -h /mnt/demo
```
- Shows 2 TB usable space.

---

## Final Result
- Volume successfully resized from 1 TB → 2 TB.
- Partition extended and file system grown.
- Instance now recognizes full 2 TB volume.
