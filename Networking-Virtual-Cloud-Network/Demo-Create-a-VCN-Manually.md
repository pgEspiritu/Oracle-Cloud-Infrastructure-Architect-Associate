# 🛠️ Manual VCN Creation Demo in Oracle Cloud Infrastructure

## 🎯 Objective

We will:
- Create a VCN named `demovcn`
- Assign the CIDR block: `10.0.0.0/16`

---

## ✅ Steps

### 1. Navigate to the OCI Console
- Click on **Navigation Menu**
- Go to **Networking** → **Virtual Cloud Networks**

### 2. Create the VCN
- Click on **Create VCN**
- Enter **Name**: `demovcn`
- Select the **Compartment**
- Input **IPv4 CIDR Block**: `10.0.0.0/16` and press **Enter**

> ℹ️ You can add up to **5 IPv4 CIDR Blocks**, but at least **1** is required.

- Enable: ✅ **Use DNS hostnames in this VCN** (default)
- Skip: ❌ **Assign IPv6 Prefix**
- Click **Create VCN**

---

## 🧾 Result

Once created, the following default resources are automatically provisioned:

- 🛣️ **Route Table**
- 🛡️ **Default Security List**
- 📦 **DHCP Options**

You will also see the assigned **CIDR block**: `10.0.0.0/16`.

> 🚫 Note: Since this is a manual VCN creation, **no subnet** is created by default.

---

## 📌 Summary

We demonstrated how to:
- Manually create a VCN named `demovcn`
- Assign a CIDR range
- Observe the default resources that OCI provisions automatically
