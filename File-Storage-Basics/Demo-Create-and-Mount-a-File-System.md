# Demonstration: Creating and Mounting a File System in OCI

Hello and welcome. In this demonstration, I will show you how to **create and mount a file system** in Oracle Cloud Infrastructure (OCI).  

---

## 🖥️ Step 1: Access the OCI Console
- Log in as **Storage Admin**.  
- Open the **hamburger menu → Storage → File Storage → File Systems**.  
- Ensure you are in the correct **compartment** (e.g., `archassociatecompartment`).  
- Click **Create File System**.  

---

## 🔑 Step 2: Verify Environment
- An instance `fsdemo-instance` is already running:  
  - **Availability Domain**: AD1  
  - **Region**: Phoenix  
  - **VCN**: `ocivcn`  
  - **Subnet**: `subnetA`  

- Ensure SSH access to the instance.  

---

## 👤 Step 3: Required IAM Policies
Add the following policies for file storage management:  

```text
Allow group storage-admins to manage file-family in tenancy
Allow group managers to manage file-systems in tenancy
Allow group managers to read mount-targets in tenancy
```
Additionally, since mount targets are network endpoints, you also need permissions to use VNICS, private IPs, private DNS zones, and subnets.

---

## 🗂️ Step 4: Create a File System

- Click Create File System.
- Edit details → name it: demo file system.
- Availability domain: same as instance.
- Keys: Oracle-managed (default).

Export Information
- Export Path: `demofs`
- Optionally enable Secure Export Options (requires privileged source ports for added security).

Mount Target
- Create a new mount target: demo-mount-target.
- VCN: `ocivcn`
- Subnet: subnetA (same subnet as the instance).
Click Create File System.

---

## 🔒 Step 5: Configure Security Rules
When mount target and instance are in the same subnet, add these rules to the subnet’s security list:

Ingress Rules
- TCP: Allow ports 111, 2048, 2049, 2050
- UDP: Allow ports 111, 2048

Egress Rules
- TCP: Allow ports 111, 2048, 2049, 2050
- UDP: Allow port 111
Confirm rules in SubnetA → Default Security List.

---

## ✅ Step 6: Verify Creation
- File system status: Active.
- Mount target created inside ocivcn in subnetA.

---

## 📂 Step 7: Mount the File System
1. Install NFS Client
```bash
sudo yum install nfs-utils -y      # Oracle Linux / RHEL
# OR
sudo apt-get install nfs-common    # Ubuntu / Debian
```

2. Create Mount Point Directory
```bash
sudo mkdir -p /mnt/myfss
```

3. Mount the File System
```bash
sudo mount <mount-target-IP>:/demofs /mnt/myfss
```

4. Verify Mount
```bash
df -h | grep myfss
```

---

## 📝 Step 8: Test the File System

Create a test file to confirm read/write functionality:
```bash
echo "This is a test file" | sudo tee /mnt/myfss/testfile.txt
cat /mnt/myfss/testfile.txt
```

---

🎉 Conclusion
- We successfully created a file system.
- Configured IAM and network policies.
- Mounted the file system to an OCI instance.
- Verified functionality with a test file.
