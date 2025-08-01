# 🎥 How to Create a NAT Gateway in OCI

## 📍 Step-by-Step Demonstration

In this demonstration, we’ll walk through how to **create a NAT Gateway** in Oracle Cloud Infrastructure (OCI). Let’s get started!

---

## 🧭 Navigate to Your VCN

1. **Log in** to the **OCI Console**.
2. Go to **Networking > Virtual Cloud Networks**.
3. Select your **Demo VCN**.
4. Under **Resources**, click on **NAT Gateways**.

At this point, you'll see there are **no NAT Gateways** created yet.

---

## ➕ Create a NAT Gateway

1. Click **Create NAT Gateway**.
2. Enter a **Name** for your NAT Gateway.
3. Choose the appropriate **Compartment**.

### 🌐 Public IP Options

You must choose one of the following:

- **Ephemeral Public IP Address**:
  - A temporary IP assigned **only for the lifetime** of the NAT Gateway.
  - Automatically released once the NAT Gateway is terminated.
- **Reserved Public IP Address**:
  - A persistent IP that you **manage separately**.
  - Can be reused even after NAT Gateway termination.

> ✅ In this demo, we’ll select **Ephemeral Public IP Address**. OCI will auto-assign a temporary public IP.

4. Click **Create NAT Gateway**.

---

## ✅ NAT Gateway Created

- Status will show as **Available**.
- The assigned **Public IP Address** will be visible.
- Since we chose the ephemeral option, this IP is temporary and managed by Oracle.

---

## 🛣 Add Route Rule for NAT Gateway

Now that the NAT Gateway is ready:

1. Go to **Route Tables** in your VCN.
2. Select **Default Route Table for the VCN**.
3. Click **Add Route Rules**.

### Configure Route Rule:
- **Target Type**: NAT Gateway  
- **Destination CIDR Block**: `0.0.0.0/0` (for internet-bound traffic)  
- **Target NAT Gateway**: Select the NAT Gateway you just created  
- Click **Add Route Rules**

---

## 🔗 Associate the Route Table to a Private Subnet

Ensure that the **private subnet** you want to provide outbound internet access uses the **Default Route Table** (or the one with the NAT Gateway rule).

---

## 🏁 Conclusion

That’s it! 🎉

You’ve successfully:
- Created a **NAT Gateway**
- Configured a **route rule** to direct outbound traffic
- Linked the route table to a **private subnet**

> 🚀 This setup enables instances in private subnets to access the internet **outbound only**, without exposing them to inbound connections.
