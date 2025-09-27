# Lesson: In-Transit Encryption in OCI File Storage

## What is In-Transit Encryption?
- Provides a way to **secure data between instances and mounted file systems** using **TLS (Transport Layer Security)**.  
- Ensures **end-to-end security**.  

---

## Prerequisite
- Open rules for **TCP port 2051** (required for encrypted access).  
- If you want to **enforce encrypted access only**, disable the standard access ports.  

---

## Enabling In-Transit Encryption
To enable in-transit encryption, you need the **OCI File Storage Service Client Utility**:

### Step 1: Install Utility
- Package name: **`oci-fss-utils`**  
- Installing this package will:  
  - Create a **network namespace**  
  - Create a **virtual network interface**  
  - Provide a **local NFS endpoint**  
  - Start a background process → **OCI FSS forwarder**

---

### Step 2: Mount File System with Encryption
- Use the **special in-transit encryption mount command**.  
- After mounting:  
  - The **OCI FSS forwarder** connects the local NFS client to the NFS endpoint.  
  - Requests are encrypted and sent to the mount target over a **TLS tunnel**.  

---

## Process Flow
1. Download **`oci-fss-utils`** package.  
2. Install the package.  
3. Run the **encrypted mount command**.  
4. Forwarder process handles:  
   - Encrypting NFS client requests.  
   - Sending them securely to the mount target.  

---

## Summary
- In-transit encryption secures data with **TLS** between instances and mounted file systems.  
- Requires **TCP port 2051**.  
- Uses the **OCI FSS Client Utility** (`oci-fss-utils`) and **FSS forwarder**.  
- Mount command enables encryption → requests flow securely via TLS tunnel.  
