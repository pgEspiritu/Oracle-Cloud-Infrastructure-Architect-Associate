# 🪣 Creating a Bucket in OCI

This demonstration shows how to create a bucket using:

- 🌐 **OCI Console**  
- 🖥️ **Cloud Shell**  
- 💻 **OCI CLI**

---

## ⚙️ Prerequisites
- Logged in with a **tenancy administrator** or **storage administrator** account.  
- User group (`storageadmins`) with policies:
  ```text
  Allow group storageadmins to manage buckets in tenancy
  Allow group storageadmins to manage objects in tenancy
  Allow group storageadmins to use Cloud Shell in tenancy
  ```

---

## 🌐 Step 1: Create Bucket via OCI Console
1. Log in to OCI Console
  → using storage admin user.
2. Navigate to: ☰ Menu → Storage → Object Storage & Archive Storage
3. Click Create Bucket
4. Provide a name (e.g., ociaabucket-console).
5. Choose Default Storage Tier:
  - 🟢 Standard → mix of objects
  - 🟡 Archive → only archive objects
> ⚠️ Note: This setting cannot be changed later.
6. Leave encryption as Oracle-managed keys.
> Click Create ✅.
Result: A new bucket with private visibility and standard tier.

---

## 🖥️ Step 2: Create Bucket via Cloud Shell
🔑 Required Policy:
  ```text
  Allow group storageadmins to use Cloud Shell in tenancy
  ```
1. From the Console (signed in as storage admin), launch Cloud Shell.
2. Run the bucket creation command:
   ```bash
   oci object storage bucket create \
   --name ociaabucket-cloudshell \
   --compartment-id <compartment_OCID>
   ```
3. Verify buckets:
   ```bash
   oci os bucket list
   ```
✅ Output should show both `ociaabucket-console` and `ociaabucket-cloudshell`.

---

## 💻 Step 3: Create Bucket via OCI CLI
🔧 Install and Configure CLI
1. Install OCI CLI
  - Example: Windows install (follow 5–6 setup steps).
2. Run setup:
  ```bash
  oci setup config
  ```
Provide:
  - User OCID (storage admin)
  - Tenancy OCID
  - Region (e.g., us-phoenix-1)
  - Generate API signing keys
3. Upload the public key:
  - Go to Identity → Users → storage admin → API Keys
  - Add the generated public key.

---

## 🪣 Create the Bucket
Run:
  ```bash
  oci object storage bucket create \
  --name ociaabucket-cli \
  --compartment-id <compartment_OCID>
  ```

---

✅ Summary
- 🌐 Console → quick and UI-driven
- 🖥️ Cloud Shell → no local install needed
- 💻 OCI CLI → flexible for automation

Each method successfully creates a bucket (ociaabucket-console, ociaabucket-cloudshell, ociaabucket-cli).
