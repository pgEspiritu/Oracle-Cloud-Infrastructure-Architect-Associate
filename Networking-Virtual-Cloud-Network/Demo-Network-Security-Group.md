# 🔐 Demonstration: Network Security Group in OCI

## 🎯 Objective

We will perform the following steps:

1. **Create a Network Security Group (NSG)**
2. **Add an Ingress Rule**  
   - Source: Anywhere (0.0.0.0/0)  
   - Protocol: TCP  
   - Destination Port: 80 (HTTP)
3. **Associate NSG with the Compute Instance's VNIC**
4. **Install Apache Web Server**
5. **Test Web Server Accessibility from the Internet**

---

## 🏗️ Environment Setup

- Existing:
  - VCN: `demovcn`
  - Subnets: `public`, `private`
- To Create:
  - NSG: `demoNSG`

---

## 🛠️ Step-by-Step Walkthrough

### 🔹 1. Create Network Security Group

Go to **VCN → Network Security Group**:

- Name: `demoNSG`
- Add Ingress Rule:
  - **Rule Type:** Stateful
  - **Source Type:** CIDR
  - **Source CIDR:** `0.0.0.0/0` (Internet)
  - **Protocol:** TCP
  - **Destination Port:** 80

✅ **NSG created with HTTP access rule.**

---

### 🔹 2. Launch Compute Instance

Navigate to **Compute → Instances → Create Instance**:

- Name: `demonsg-instance`
- VCN: `demovcn`
- Subnet: `public`
- Public IP: Auto-assigned
- Add SSH Key
- Leave all other settings as default

🚀 Wait until instance is in `Running` state.

---

### 🔹 3. Install Apache Web Server

Use Cloud Shell or SSH into the instance:

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
sudo firewall-cmd --add-service=http --permanent
sudo firewall-cmd --reload
echo "This is a compute demo test page." | sudo tee /var/www/html/index.html
```

---

### 🔹 4. Test Access – Fails Initially
Visit the Public IP in your browser.

❌ You won’t see the page, because the NSG is not yet associated with the instance's VNIC.

---

###  5. Associate NSG to VNIC
- Go to Instance → Primary VNIC
- Click Edit Network Security Groups
- Select `demoNSG`
- Save changes

✅ Now try accessing the Public IP again — the Apache page should load.

---

### 🔎 Verify NSG Association
Go to:
- VCN → Network Security Group → demoNSG → VNICs
You’ll now see the instance's VNIC listed, confirming the association.

---

## ✅ Summary
- NSGs are not created by default with a VCN.
- You must manually create and associate them with VNICs.
- They provide fine-grained control over traffic at the VNIC level.
- Ingress rule for port 80 enabled internet traffic to reach the web server.

> 🧠 Tip: Always verify both security list rules and NSG rules when troubleshooting connectivity issues.
