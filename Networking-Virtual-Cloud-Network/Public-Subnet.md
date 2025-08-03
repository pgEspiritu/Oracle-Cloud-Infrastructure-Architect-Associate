# 🌐 Understanding Public Subnet in OCI

## 🔄 Types of Subnets

- **Public Subnet** – Allows assigning **public IP addresses** to instances
- **Private Subnet** – Does **not** allow public IP assignment (covered in the next lesson)

---

## 🧱 Creating a Public Subnet

When creating a subnet in the OCI Console:

- Under **Subnet Access**, select `Public Subnet` (this is the **default** option)
- This setting allows instances deployed in the subnet to be assigned **public IP addresses**

---

## 🖧 Instance Deployment

Example scenario:

- You create a public subnet
- Deploy VM instances such as:
  - `VM 1`
  - `VM 2`

These instances get public IP addresses assigned to their **Virtual NIC (VNIC)** if public IP is enabled.

> ⚠️ If you don't select *Public Subnet*, public IPs **cannot be assigned**.

---

## 🛣️ Route Table Configuration

To allow public subnet instances to reach the internet:

1. Create or use a **Route Table**
2. Add a **route rule** with:
   - **Destination CIDR**: `0.0.0.0/0` (Internet)
   - **Target**: `Internet Gateway`

---

## 🔐 Security Configuration

Make sure to:

- Configure **Security Lists** (associated with the subnet) **or**
- Use **Network Security Groups (NSGs)**

Open necessary **ports** (e.g., TCP 22 for SSH) to allow traffic to/from the internet.

---

## 🧭 Architecture Overview
```graph
VCN
├── Private Subnet
└── Public Subnet
├── VM Instance (with Public IP)
└── Route Table
└── 0.0.0.0/0 → Internet Gateway
```


---

## ✅ Summary

- Public subnet allows assigning **public IPs** to instances
- Enables **internet communication** via **Internet Gateway**
- Requires:
  - Public IP assignment on instance VNIC
  - Route table pointing to Internet Gateway
  - Security rules allowing relevant traffic

