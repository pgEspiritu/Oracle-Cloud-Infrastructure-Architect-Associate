# Demonstration: Setting Up In-Transit Encryption in OCI File Storage

Hello and welcome.  
In this demonstration, I'll show you how to set up **in-transit encryption** to secure your data between instances and mounted file systems using **TLS (Transport Layer Security)**.

---

## 📘 Oracle Documentation
Oracle provides documentation for setting up in-transit encryption.  
The process involves **four steps**:

1. ✅ Ensure prerequisites are met (security rules).  
2. 📥 Download the **OCI FSS Utils** package.  
3. ⚙️ Install the package.  
4. 🔒 Use the **in-transit encryption command** to mount the file system.  

---

## 🔑 Step 1: Prerequisites
- Standard access rules used earlier are **not required**.  
- To enforce **encrypted access only**, disable standard access ports.  
- Only **TCP port 2051** rules are required:  

**Ingress Rule**  
- Source: `10.0.0.0/24`  
- Destination Port Range: `2051`  

**Egress Rule**  
- Destination: `10.0.0.0/24`  
- Source Port Range: `2051`  

---

## 📦 Step 2: Download OCI FSS Utils
- Utility: **`oci-fss-utils`**  
- Secures data between **instances and mounted file systems** using **TLS encryption**.  
- Download based on Oracle Linux version.  

```bash
# Example (download and verify)
ls
oci-fss-utils.rpm
```

---

## ⚙️ Step 3: Install OCI FSS Utils
Connect to your instance via SSH and install the package:
```bash
# Example installation
sudo yum install -y oci-fss-utils.rpm
```
✅ After installation:
- A mount point can be created.
- File system access is enabled through this directory.

---

## 🔒 Step 4: Mount File System with Encryption

From the OCI Console → View Mount Commands.
Instead of the standard command, use the special encryption mount command:
```bash
sudo mount -t oci-fss <MOUNT_TARGET_IP>:<EXPORT_PATH> <MOUNT_POINT>
```
- <MOUNT_TARGET_IP> → IP address of the mount target
- <EXPORT_PATH> → Example: /demofs
- <MOUNT_POINT> → Directory you created

✅ After mounting, check with:
```bash
df -h
```

---

## ⚡ How It Works

- The special mount command initiates encryption.
- The OCI FSS Forwarder:
  - Connects the local NFS client to the NFS endpoint.
  - Encrypts requests from the NFS client.
  - Sends them securely to the mount target via a TLS tunnel.

---

## 🎯 Summary
- In-transit encryption secures communication with TLS.
- Requires TCP port 2051 only.
- Uses the OCI FSS Utils package.
- Mounted file systems are encrypted end-to-end.****
