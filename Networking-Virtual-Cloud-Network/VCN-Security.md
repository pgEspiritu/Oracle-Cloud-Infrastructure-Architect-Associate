# 🛡️ Lesson: VCN Security in OCI

## 🔐 Security Strategies for VCN

There are multiple ways to enforce security within your VCN:

### 1. **Public and Private Subnets**
- Use **private subnets** to avoid assigning public IPs to instances.

### 2. **Security Constructs**
- **Security Lists**: Act like firewalls at the **subnet level**
- **Network Security Groups (NSG)**: Act like firewalls at the **VNIC level**

### 3. **Instance-Level Firewalls**
- You can define OS-level firewall rules directly on the virtual machine instances.

### 4. **IAM Policies**
- Use **Identity and Access Management (IAM)** to control:
  - Who can create/modify VCNs, subnets
  - Who can configure security lists and NSGs

### 5. **Security Zones**
- A **Security Zone** ensures your networking resources follow OCI best practices.
- Key traits:
  - **Only private subnets allowed**
  - **No public IPs permitted**
  - Bound to a **Compartment**

---

## 🏡 Analogy: Understanding Security Rules

Imagine a **Housing Society**:
- **Houses A, B, C, D** = Virtual Machine Instances
- **Main Gate Guard** = Security List (Subnet-level)
- **House Guards** = NSGs (Instance NIC-level)

A person (representing **traffic**) must pass:
1. The **Main Gate Guard** (Security List)
2. The **Specific House Guard** (Network Security Group)

> 🔄 Replace:
> - **Housing Society** → Subnet  
> - **Houses** → VM Instances  
> - **Main Guard** → Security List  
> - **House Guards** → Network Security Groups

---

## 🧱 Security Components Recap

| Feature                | Description |
|------------------------|-------------|
| **Security List**      | Controls traffic at **subnet** level |
| **Network Security Group (NSG)** | Controls traffic at **instance NIC** level |
| **IAM Policies**       | Controls who can manage networking components |
| **Firewall Rules**     | OS-level control inside instances |
| **Security Zone**      | Enforces secure configurations |
| **Route Table & Gateways** | Manage traffic flow in/out of VCN |

---

## 📌 Usage Guidelines

- You can use **Security List**, **NSG**, or **both**.
- A **Subnet** can have **up to 5 Security Lists**.
- A **VNIC** can be associated with **up to 5 NSGs**.
- Every VCN comes with:
  - A **Default Route Table**
  - A **Default Security List**
