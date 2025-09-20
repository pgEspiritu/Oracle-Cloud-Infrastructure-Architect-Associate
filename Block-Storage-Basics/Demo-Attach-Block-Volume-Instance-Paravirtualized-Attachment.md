# 📦 OCI Block Volume Attachment (Paravirtualized) Demonstration  

Hello, and welcome. In this demonstration, I will show you how to **attach a block volume to an instance using the paravirtualized attachment type**. 🚀  

---

## 🖥️ Setup  
- **Block Volume** → `blockvolume-pvdemo` (in AD-1).  
- **Instance** → `instance2-paravirtualizeddemo` (running in AD-1).  
- Attachment type: **Paravirtualized**.  

---

## 1️⃣ Verify Existing Block Devices  
- Connect to the instance via SSH.  
- Run:  

```bash
lsblk
```
👉 Only the boot disk is visible initially.

---

## 2️⃣ Attach Block Volume in Console
1. Go to Block Volume → blockvolume-pvdemo → Attach Instance.
2. Click Attach to Instance.
3. Select:
  - Attachment Type → Paravirtualized
  - Access Type → Read/Write
  - Instance → instance2-paravirtualizeddemo
  - Device Path → enable consistent device path
4. Click Attach.
📌 Unlike iSCSI, no iscsiadm commands are required.

---

## 3️⃣ Verify the Attached Volume

Run again:
```bash
lsblk
```
👉 You should now see sdb (new block device).

Verify device path:
```bash
readlink -f /dev/sdb
```

---

## 4️⃣ Partition, Format, and Mount Volume
Partition the Disk
```bash
sudo fdisk /dev/sdb
```
- Accept defaults and create /dev/sdb1.

Format the Partition
```bash
sudo mkfs.ext4 /dev/sdb1
```

Mount the Partition
```bash
sudo mkdir /mnt/pv-volume
sudo mount /dev/sdb1 /mnt/pv-volume
```

Verify:
```bash
df -h
```

---

## 5️⃣ Enable Auto-Mount on Reboot

Edit /etc/fstab:
```bash
/dev/sdb1   /mnt/pv-volume   ext4   defaults,nofail   0   2
```

---

## 6️⃣ Validate Setup

Create a test file:
```bash
cd /mnt/pv-volume
echo "OCI paravirtualized demo file" > demo.txt
ls -l
```
👉 File is created successfully, confirming the mount.

---

📊 Key Points
- Paravirtualized attachment → simpler setup, no iSCSI commands needed.
- Appears immediately after attaching in OCI Console.
- Recommended for ease of use, though iSCSI offers higher IOPS for performance-sensitive workloads.
- Configure fstab for persistence across reboots.
