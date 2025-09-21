# ⚡ OCI Demo – Multiple Instance Volume Attachments (Part 2)

## 🛠 Kernel Configuration for Cluster Operations
On **each instance** configure kernel panic and oops handling:

```bash
# Reboot after panic (in seconds)
sudo sysctl -w kernel.panic=30

# Panic on kernel oops
sudo sysctl -w kernel.panic_on_oops=1
```

➡️ To make changes persistent across reboots, add to /etc/sysctl.conf:
```bash
kernel.panic = 30
kernel.panic_on_oops = 1
```

---

## 📦 Creating the OCFS2 Volume (Performed on Instance-1 Only)
```bash
sudo mkfs.ocfs2 -L "sharedvol" /dev/sdb
```

- Create mount directory:
  ```bash
  sudo mkdir /sharedvol
  ```

- Add to /etc/fstab with netdev option for auto-mount:
  ```bash
  /dev/sdb   /sharedvol   ocfs2   defaults,_netdev   0 0
  ```

- Mount:
  ```bash
  sudo mount -a
  ```

- Verify
  ```bash
  lsblk
  df -h
  ```

---

## 📂 Configuration on Instance-2

- Create the same mount directory:
  ```bash
  sudo mkdir /sharedvol
  ```

- Add same line in /etc/fstab:
  ```bash
  /dev/sdb   /sharedvol   ocfs2   defaults,_netdev   0 0
  ```

- Mount:
  ```bash
  sudo mount -a
  ```

- Verify:
  ```bash
  lsblk
  df -h
  ```

---

## 🔄 Testing Shared Access

- On instance-1:
  ```bash
  cd /sharedvol
  echo "Hello from Instance 1" > sample.txt
  ls -l
  ```

- On instance-2:
  ```bash
  cd /sharedvol
  ls -l
  cat sample.txt
  ```
✅ File created on instance-1 is visible on instance-2.

---

## ✅ Demo Summary
- Configured kernel panic settings for cluster safety.
- Created and mounted an OCFS2 shared volume on both nodes.
- Verified shared file access across instances.
👉 With OCFS2, multiple instances can safely perform Read/Write operations on the same block volume without data corruption.
