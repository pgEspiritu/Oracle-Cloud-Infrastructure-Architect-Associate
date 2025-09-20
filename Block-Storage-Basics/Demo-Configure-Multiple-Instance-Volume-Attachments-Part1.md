# ⚡ OCI Demo – Configure Multiple Instance Volume Attachments

## 📦 Resources Setup
- **Block Volume**
  - Name: `sharedvolume`
  - Size: **1024 GB**
  - Performance: **Balanced**
  - Availability Domain: **AD-1**

- **Instances**
  - `instance-1`: Public + Private IP available
  - `instance-2`: Public + Private IP available
  - Both running in the **same AD**

---

## 🔗 Attaching Shared Block Volume
1. Navigate to **sharedvolume** → **Attach Instance**.
2. Select **Paravirtualized** attachment type.
3. Set **Access Type** to `Read/Write-Shareable`.
   - ⚠️ Warning: Risk of data corruption without a **clustered file system**.
4. Attach volume to:
   - `instance-1`
   - `instance-2`

Now the volume is attached to **both instances** with **Read/Write-Shareable** access.

---

## 🔍 Verifying Attachments
- On **instance-1**:
  ```bash
  lsblk
  ```
→ Volume detected (size: 1 TB)

- On **instance-2**:
  ```bash
  lsblk
  ```
→ Same shared volume detected.

---

## 🔧 Prerequisites for OCFS2 Setup
- Open required ports in VCN security list:
  - 7777
  - 3260
- Open the same ports in OS firewall for each instance:

```bash
sudo firewall-cmd --add-port=7777/tcp --permanent
sudo firewall-cmd --add-port=3260/tcp --permanent
sudo firewall-cmd --reload
```

--- 

## ⚙️ Installing OCFS2 Packages
Run on both nodes:
```bash
sudo yum install ocfs2-tools -y
```

## 🖧 Cluster Configuration
1. On instance-1, create cluster definition:
```bash
sudo o2cb add-cluster OCI-OCFS2
sudo o2cb add-node OCI-OCFS2 instance-1 --ip=10.0.0.21
sudo o2cb add-node OCI-OCFS2 instance-2 --ip=10.0.0.36
```

2. Copy cluster config to instance-2:
- Create config directory
- Paste contents from instance-1 cluster file

---

## 🔄 Cluster Stack Configuration
Run on both nodes:
```bash
sudo o2cb register-cluster OCI-OCFS2
sudo o2cb enable-cluster OCI-OCFS2
sudo o2cb online-cluster OCI-OCFS2
```

- Verify cluster:
  ```bash
  sudo o2cb list-cluster
  ```
  → `OCI-OCFS2` online (heartbeat inactive until later setup)

---

## 🚀 Auto-Start Services
On both nodes:

```bash
sudo systemctl enable o2cb
sudo systemctl enable ocfs2
```

---

## ✅ Demo Summary
- Configured shared block volume with Read/Write-Shareable mode.
- Attached to two instances.
- Opened required ports in network + OS firewall.
- Installed OCFS2 packages and set up cluster definition.
- Configured cluster stack and enabled services at boot.
👉 Next Part: Configure the cardinal for cluster operations, then create and mount volumes.
