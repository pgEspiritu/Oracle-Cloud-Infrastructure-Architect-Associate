# Creating a VCN Using the VCN Wizard in OCI


## Step-by-Step Instructions

### 1. Accessing the VCN Wizard
- Log in to your **OCI Console**.
- Click on the **Navigation Menu**.
- Go to **Networking > Virtual Cloud Networks**.
- Click on **Start VCN Wizard**.

---

## 2. Choose VCN Wizard Option

There are two options:

### ✅ Option 1: Create VCN with Internet Connectivity
This option creates the following automatically:
- A **VCN**
- A **Public Subnet** (connects to Internet via **Internet Gateway**)
- A **Private Subnet** (connects to Internet via **NAT Gateway**)
- A **Service Gateway** (for Oracle Services Network access)

### 🔐 Option 2: Add Internet Connectivity and Site-to-Site VPN
- Includes everything in Option 1
- Additionally creates a **Site-to-Site VPN** between your on-prem network and the VCN

---

## 3. Create VCN with Internet Connectivity

- Select **Create VCN with Internet Connectivity**
- Click on **Start VCN Wizard**
- Enter VCN Name: `ociaavcn`
- Choose Compartment: *(use the default or your desired one)*
- Accept or modify the default CIDR blocks
- Click **Next**
- Review configuration
- Click **Create**

---

## 4. What Gets Created

After creation, the following resources are provisioned:

- ✅ **VCN**
- ✅ **Public Subnet**
- ✅ **Private Subnet**
- ✅ **Internet Gateway**
- ✅ **NAT Gateway**
- ✅ **Service Gateway**
- ✅ **Route Tables**
  - One for Public Subnet (with route to Internet Gateway)
  - One for Private Subnet (with routes to NAT and Service Gateway)
- ✅ **Security Lists** (configured for both subnets)

---

## 5. Verifying Resources

- Click on **View VCN** to inspect the details.
- Check the **Subnets**: Public and Private
- Go to **Route Tables**:
  - Public Subnet Route Table → Internet Gateway
  - Private Subnet Route Table → NAT Gateway, Service Gateway
- Check the **Gateways** tab to verify:
  - Internet Gateway
  - NAT Gateway
  - Service Gateway

---

## ✅ Conclusion

Using the **VCN Wizard** simplifies the process of provisioning a fully functional network in OCI by automatically setting up all necessary components.
