# Internet Gateway Demo Walkthrough

## 🧭 Demo Objective

In our VCN, we have:
- **Two subnets**: one **private**, one **public**
- We'll:
  - Create a **Compute Instance** in the **public subnet**
  - Add an **Internet Gateway**
  - Update the **Route Table** to route traffic through the Internet Gateway
  - Associate the **Route Table** with the **public subnet**
  - Verify if the VM can access the internet

---

## 🔧 Step-by-Step Instructions

### 1. OCI Console: View Initial Configuration
- Navigate to the **VCN (`Demovcn`)**
- You'll see:
  - **Two subnets**: private and public
  - **Only one Route Table** exists — we need to create a second one for the public subnet

### 2. Create Public Route Table
- Go to Route Tables
- Click **Create Route Table**
- Name it appropriately (e.g., `PublicRouteTable`)

### 3. Create Internet Gateway
- Navigate to **Internet Gateways**
- Click **Create Internet Gateway**
- Name it (e.g., `DemoIGW`)
- Select the correct **compartment**
- Click **Create**

> ❗ Attempting to create a second Internet Gateway will result in an error: only **one Internet Gateway per VCN** is allowed.

---

## 📍 Configure Route Table for Internet Access

- Go to `PublicRouteTable`
- Click **Add Route Rule**
  - **Destination CIDR Block**: `0.0.0.0/0`
  - **Target Type**: Internet Gateway
  - **Target Internet Gateway**: Select `DemoIGW`
- Click **Add Route Rules**

---

## 🖥️ Create Compute Instance in Public Subnet

- Go to **Compute → Instances**
- Click **Create Instance**
- In the **Network settings**:
  - Select `Demovcn`
  - Select **Public Subnet**
  - Enable: **Automatically assign public and private IP addresses**
- Paste your **SSH public key**
- Click **Create**

---

## 🔗 Associate Route Table with Public Subnet

- Go to **VCN → Subnets → Public Subnet**
- You'll see it's associated with **Default Route Table**
- Change it to **PublicRouteTable**
- Click **Save Changes**

---

## 🔐 Connect to the Instance

- Copy the **public IP** of your instance
- Use SSH to connect:
  ```bash
  ssh -i <your-private-key.pem> opc@<public-ip>
  ```

---

## 🌐 Test Internet Access from Instance
Once connected, try:
```bash
curl oracle.com
```

or
```bash
ping oracle.com
```

>✅ Success means your instance can now reach the internet!

---

## ✅ Summary
This demo covered:
- Creating an Internet Gateway
- Updating Route Tables
- Creating and configuring a Compute Instance in a public subnet
- Associating the subnet with the correct Route Table
- Verifying internet connectivity
