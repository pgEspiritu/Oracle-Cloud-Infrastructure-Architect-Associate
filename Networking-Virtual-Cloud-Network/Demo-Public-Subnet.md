# 🚀 Demonstration: Creating a Public Subnet in OCI

## 🔍 Step-by-Step: Inside the OCI Console

### 1. Select the Demo VCN

- Navigate to **VCNs**
- Choose `demo VCN`
- Notice the following are already created:
  - Internet Gateway
  - NAT Gateway
  - Service Gateway
  - Default Route Table

---

### 2. Create a Public Subnet

- Go to **Subnets** → Click **Create Subnet**
- Enter:
  - **Name**: `publicsubnet`
  - **Subnet Type**: `Regional` (recommended)
  - **CIDR Block**: `10.0.1.0/24`  
    _(This is a subset of the VCN's CIDR)_
  - **Subnet Access**: `Public Subnet` (default)

> ✅ Creating a public subnet allows instances within it to receive **public IP addresses**.

Click **Create Subnet**

---

### 3. Modify Route Table

- Navigate to **Default Route Table**
- Click **Add Route Rules**
  - **Target Type**: `Internet Gateway`
  - **Destination CIDR Block**: `0.0.0.0/0` (Internet)
  - **Target Gateway**: Select existing Internet Gateway

Click **Add Route Rules**

---

### 4. Launching a VM in the Public Subnet

- Go to **Compute → Instances** → Click **Create Instance**
  - **Name**: `publicsubnet-demo`
  - Select existing **VCN**: `demo VCN`
  - Choose **Subnet**: `publicsubnet`

> 📝 You will now see two key options:
> - **Private IPv4 Address**: Auto-assigned
> - **Public IPv4 Address**: ✅ Available — because the subnet is public

If this were a private subnet, the **public IP address option would be grayed out**.

---

## 📌 Summary

- ✅ Created a public subnet in `demo VCN`
- ✅ Configured it to allow public IPs for instances
- ✅ Set up a route to the Internet Gateway
- ✅ Observed public IP option during instance provisioning
