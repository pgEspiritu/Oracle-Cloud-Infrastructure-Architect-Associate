# 🔗 OCI Block Volume Attachment (iSCSI) Demonstration  

Hello, and welcome. In this demonstration, I will show you how to **attach a block volume to an instance using the iSCSI attachment type**. 🚀  

---

## 🖥️ Setup  
- **Block Volume** → `blockvolume-iscsidemo` (1,024 GB, Balanced performance, AD1).  
- **Instance** → `instance1-iscsidemo` (running in AD1).  
- Attachment type: **iSCSI**.  

---

## 1️⃣ Verify Existing Block Devices  
- Connect to the instance via SSH.  
- Run:  

```bash
lsblk
```
👉 You will only see the boot disk since the block volume is not yet attached.

---

## 2️⃣ Attach Block Volume in Console

1. Go to Block Volume → blockvolume-iscsidemo → Attached Instances.
2. Click Attach to Instance.
3. Select:
   - Attachment Type → iSCSI
   - Access Type → Read/Write
   - Instance → instance1-iscsidemo
   - Device Path → enable consistent device path
4. Click Attach
📌 Volume is now attached, but not yet visible on the instance.

---

## 3️⃣ Run iSCSI Commands on Instance

After attaching, run the provided commands:
```bash
# 1. Register the volume with iscsiadm
sudo iscsiadm -m node -o new -T <target_iqn> -p <ip>:3260

# 2. Configure auto-connect on reboot
sudo iscsiadm -m node -o update -T <target_iqn> -n node.startup -v automatic

# 3. Login to iSCSI
sudo iscsiadm -m node -T <target_iqn> -p <ip>:3260 -l
```

👉 After success, verify the new disk:
```bash
lsblk
```
You should now see sdb (1 TB).

---

## 4️⃣ Partition, Format, and Mount Volume
Partition the Disk
```bash
sudo fdisk /dev/sdb
```
- Accept defaults and create a partition (/dev/sdb1).

Format the Partition
```bash
sudo mkfs.ext4 /dev/sdb1
```

Mount the Partition
```bash
sudo mkdir /mnt/iscsi-volume
sudo mount /dev/sdb1 /mnt/iscsi-volume
```

Verify:
```bash
df -h
```

---

## 5️⃣ Enable Auto-Mount on Reboot

Edit /etc/fstab:
```bash
/dev/sdb1   /mnt/iscsi-volume   ext4   defaults,_netdev,nofail   0   2
```

Test:
```bash
cat /etc/fstab
```

---

## 6️⃣ Validate Setup
Create a test file:
```bash
cd /mnt/iscsi-volume
echo "OCI iSCSI demo file" > demo.txt
ls -l
```
- Reboot instance → volume auto-mounts. ✅

---

## 📊 Key Points
- iSCSI requires manual iscsiadm setup before the block volume appears.
- Provides higher IOPS compared to paravirtualized attachment.
- Ensure to update fstab for persistence across reboots.
