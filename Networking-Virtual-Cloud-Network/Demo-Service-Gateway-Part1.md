# 🚀 Service Gateway Demonstration

## 📘 Scenario Overview

We will create a **VCN** containing:

- A **private subnet**
- A **virtual machine (VM) instance** within the private subnet (with a private IP only)
- An **Object Storage bucket**

We will also configure:

- A **NAT Gateway**
- A **Service Gateway**
- **Route tables** and **security lists**

We’ll use **Cloud Shell** with a private network definition list to connect to the VM (since it doesn’t have a public IP).

---

## 🛠️ Setup Steps

### 1️⃣ Create Service Gateway

- Go to VCN → Create Service Gateway  
- Name: any  
- Compartment: selected  
- Service: **OCI Phoenix Object Storage**  
- Click **Create Service Gateway**

### 2️⃣ Create NAT Gateway

- Select **Ephemeral Public IP Address**
- Click **Create NAT Gateway**

### 3️⃣ Configure Route Table

- Go to the **default route table** of the private subnet
- Click **Add Route Rule**
  - Target Type: **NAT Gateway**
  - Destination CIDR: `0.0.0.0/0` (Internet)
  - Select the NAT Gateway created
- Click **Add Route Rules**

✅ The private subnet is now associated with the default route table.

---

## 🪣 Create Object Storage Bucket

- Go to **Object Storage**
- Click **Create Bucket**
- Use default settings
- Click **Create**

(Note: We’ll upload an object later.)

---

## 🖥️ Create Compute Instance

- Name: `demoinstance-service-gateway`
- VCN: `demovcn`
- Subnet: **Private**
- Paste **public SSH key** generated from Cloud Shell
- Click **Create**

---

## 🌐 Set Up Private Network Definition List

- Go to **Private Network Definition List**
- Click **Create**
  - Name: `service-gateway-demo`
  - VCN: `demovcn`
  - Subnet: **Private**
- Click **Create**

➡️ Mark the new definition as the **active network** in Cloud Shell

---

## 🔐 Connect to the Private Instance

- Check that the instance is now **running**
- Confirm it has a **private IP** (e.g., `10.0.1.20`)
- Connect using:

```bash
ssh -i <private_key> opc@10.0.1.20
```
> ✅ You’re now connected to the private instance via the private network definition list.

---

## 📦 Verify Internet Access via NAT Gateway
- Go to VCN → Route Tables
- Confirm that the route table has an Internet route via NAT Gateway
- Now try to install the OCI CLI on the instance
> ✅ Since the route is configured, internet access works and CLI installation should succeed.

---

## 🧩 Next Steps
In the next part, we’ll:
- Install OCI CLI
- Remove the NAT Gateway
- Interact with Object Storage via Service Gateway
