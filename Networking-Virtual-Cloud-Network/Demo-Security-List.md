# 🔒 Demonstration: Security Lists in OCI

## 📍 Step 1: Navigating to the Security List

- Inside the **OCI Console**, go to your **VCN (Virtual Cloud Network)**.
- Under **Resources**, click on **Security Lists**.
- You will see a **default Security List** already created when the VCN was provisioned.

---

## 🔍 Step 2: Understanding Default Security List Rules

### 🔐 Ingress Rules

| Rule | Protocol | Port | Source | Description |
|------|----------|------|--------|-------------|
| 1 | TCP | 22 | `0.0.0.0/0` | Allows **SSH access** to instances from the internet. |
| 2 | ICMP | Type 3, Code 4 | Authorized Source IPs | Used for **path MTU discovery**. |
| 3 | ICMP | Type 3 | VCN CIDR Block | Allows **connectivity error messages** within the VCN. |

> ✅ These rules enable you to:
> - Create a new **VCN**
> - Add a **public subnet**
> - Launch a **Linux instance**
> - Immediately **SSH into it** without adding custom rules

### 📤 Egress Rules

| Rule | Protocol | Port | Destination | Description |
|------|----------|------|-------------|-------------|
| 1 | All | All | `0.0.0.0/0` | Allows **all outbound traffic** from the instance |

---

## ❌ No Port 80 (HTTP) Access by Default

- The default **ingress rules do NOT allow traffic on port 80**
- Hence, if your instance runs a **web server**, it won’t be reachable unless port 80 is explicitly allowed

---

## 🧪 Step 3: Test Without NSG

1. Navigate to your **Compute Instance**
2. Click on **Edit** under **Primary VNIC**
3. **Remove the associated Network Security Group (NSG)**
4. Copy the instance’s **Public IP**
5. Open a web browser and paste the IP

> ❌ Web page will **fail to load**, as port 80 is not open

---

## 🔧 Step 4: Add Ingress Rule to Default Security List

1. Go back to your **VCN**
2. Open the **Default Security List**
3. Click **Add Ingress Rule**
4. Configure the following:

```text
Direction: Ingress
Stateful: Yes
Source Type: CIDR
Source CIDR: 0.0.0.0/0
Protocol: TCP
Destination Port Range: 80
```


5. Save the rule

---

## ✅ Step 5: Retest Access

- Return to your browser and **refresh the IP**
- The web server page should now **load successfully**

---

## 🎯 Key Takeaways

- OCI creates **default security rules** with every VCN
- **Port 80** is not open by default—you must explicitly allow it
- **Security Lists** apply to **all instances in the associated subnet**
- You can **modify existing security lists** to add custom rules
