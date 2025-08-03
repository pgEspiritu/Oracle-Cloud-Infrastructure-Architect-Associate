# 🧪 Service Gateway Demonstration – Part 2

Welcome to the **second part** of the demonstration on **Service Gateway**. In this part, we’ll:

- Install the **OCI CLI** on a private instance
- Upload a file to **Object Storage**
- Demonstrate how private communication works using a **Service Gateway**
- Remove the **NAT Gateway** to enforce private-only access

---

## ⚙️ Step 1: Install OCI CLI on Private Instance

Run the following command on the instance:

```bash
bash -c "$(curl -L https://raw.githubusercontent.com/oracle/oci-cli/master/scripts/install/install.sh)"
```

Once the installation completes, run the OCI setup:

```bash
oci setup config
```

The prompts will ask for:
- Config file location: Press Enter to use default
- User OCID: Paste your user OCID
- Tenancy OCID: Paste your tenancy OCID
- Region: For example, enter `50` for US Phoenix
- Generate API key pair: Type `yes`

The key pair will be generated in your working directory.

Add the public key `(*.pem)` to your OCI User Profile > API Keys.

---

## 📤 Step 2: Upload File to Object Storage
We’ll try to upload a file to Object Storage bucket from this private instance.

1. Create a test file:
```bash
echo "Hello from Service Gateway demo" > test.txt
```

2. Try uploading using OCI CLI:
  ```bash
oci os object put --bucket-name demobucket --file test.txt
```
> 🚫 Note: At this point, the upload will fail, because there's no valid route to Object Storage.

---

## 🛣️ Step 3: Add Service Gateway Route
Update the default route table of the private subnet:
- Target Type: `Service Gateway`
- Destination Service: `OCI Phoenix Object Storage`
- Target: Select the Service Gateway created earlier
✅ After adding this route rule, re-run the upload command:
```bash
oci os object put --bucket-name demobucket --file test.txt
```
🎉 The file uploads successfully!
You can now refresh the bucket in the OCI console and verify that `test.txt` has been added.

---

🔒 Step 4: Confirm Isolation from Internet
Try pinging an external host:
```bash
ping oracle.com
```

❌ You’ll get no response, because:
- No NAT Gateway
- No Internet Gateway
- Only Service Gateway route exists

---

✅ Summary
- The private instance can communicate privately with Oracle Services like Object Storage via Service Gateway
- No public IP, no NAT, and no internet needed
- All traffic stays within Oracle’s network fabric
> This completes the demonstration on private access using Service Gateway in Oracle Cloud Infrastructure.
