# 🔒 Demonstration: Creating a Private Subnet in OCI

## 🔧 Step 1: Navigate to the VCN

- Go to the **OCI Console**
- Select the **VCN** named `demo VCN`
- Observe that it currently contains a **public subnet**

---

## 🛠️ Step 2: Create a Private Subnet

1. Click **Create Subnet**
2. Provide the following values:
   - **Name**: `privatesubnet`
   - **Compartment**: Default or selected one
   - **Subnet Type**: `Regional`
   - **CIDR Block**: (e.g., `10.0.2.0/24`)
   - **Subnet Access**: Select **Private Subnet**

> 📌 When using a private subnet:
> - Instances **will NOT have public IPs**
> - Only **private IP addresses** are assigned

3. Click **Create Subnet**

---

## 🧭 Step 3: Create a Route Table for NAT Gateway

1. Go to **Route Tables**
2. Create a new route table:
   - **Name**: `privatert`
   - **Route Rule**:
     - **Target Type**: NAT Gateway
     - **Destination CIDR**: `0.0.0.0/0`
     - **Target NAT Gateway**: (select existing one)
3. Click **Create**

> ✅ This route enables outbound internet access **via NAT Gateway** for instances in the private subnet.

---

## 🖥️ Step 4: Launch a Compute Instance in Private Subnet

1. Navigate to **Compute > Instances**
2. Click **Create Instance**
   - **Name**: `privateinstance`
   - **Virtual Cloud Network**: `demovcn`
   - **Subnet**: `privatesubnet`
3. Observe the following:
   - ✅ **Private IPv4 Address** option is enabled
   - ❌ **Public IPv4 Address** option is **disabled**
   - 📘 Note: *"Because the selected subnet is private, public IP assignment is not allowed."*

---

## 🔐 Step 5: Accessing Private Instances

Since the instance does not have a public IP, there are **two ways** to connect:

1. **OCI Bastion Service** – secure SSH access to private instances
2. **Private Network Definition List** – feature of CloudShell for access

---

## ✅ Summary

- You successfully created a **private subnet**
- Attached it to a **NAT Gateway** via a custom route table
- Verified that **public IPs are not assignable**
- Learned secure access methods for private subnet instances
