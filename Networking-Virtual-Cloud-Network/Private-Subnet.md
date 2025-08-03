# 🔒 Lesson: Private Subnet in OCI

## 🧠 Understanding Subnet Access Options

When creating a subnet in OCI, you choose one of the following **Subnet Access** options:

- ✅ **Public Subnet** – allows instances to receive public IPs  
- 🔒 **Private Subnet** – disallows public IPs for instances

We already covered public subnets in the previous lesson. Let's now dive into **private subnets**.

---

## 📌 What Happens When You Create a Private Subnet?

- When a **private subnet** is created, any **Virtual Machine (VM) Instances** launched within it will **only have private IP addresses**.
- ❌ **No public IP addresses** are allowed for instances in a private subnet.

> This restriction is built-in to ensure the subnet remains **isolated from the public internet**.

---

## 🌐 Connecting to the Internet or On-Premises

So, what if a VM in the private subnet needs to:
- Access the **Internet**?
- Connect to an **on-premises environment**?

Here’s how you enable those:

| Requirement                  | Solution              |
|-----------------------------|------------------------|
| Internet access             | **NAT Gateway**        |
| On-prem connectivity        | **Dynamic Routing Gateway (DRG)** |

- 🔁 **NAT Gateway**: Enables **outbound-only** communication to the internet  
- 🏢 **DRG (Dynamic Routing Gateway)**: Enables **connectivity to on-premises** networks

> We’ll cover DRG in detail in a separate lesson.

---

## 🧭 Route Table for Private Subnet

Here's what the **route table** would typically include:

- **Destination CIDR**: `0.0.0.0/0` (Internet)
  - **Target**: NAT Gateway
- **Destination CIDR**: On-prem CIDR (e.g. `192.168.0.0/16`)
  - **Target**: DRG

---

## 🖼️ Diagram Summary
```graph
VCN
├── Private Subnet
│ ├── VM Instance (Private IP only)
│ └── Route Table:
│ ├── NAT Gateway → Internet (for outbound traffic)
│ └── DRG → On-Premises Network
```


---

## ✅ Key Takeaways

- Instances in **private subnets** **do not get public IPs**
- Use:
  - **NAT Gateway** for outbound internet access
  - **DRG** for on-prem connectivity
- Enhances security by **isolating instances from direct public access**
