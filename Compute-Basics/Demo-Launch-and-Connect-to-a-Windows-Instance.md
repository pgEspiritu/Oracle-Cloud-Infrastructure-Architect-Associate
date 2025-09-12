# 🖥️ Demonstration: Launch and Connect to a Windows Instance in OCI  

## Step 1: Create the Instance  
1. Log in to the **OCI Console** as the `computeadmin` user.  
2. Click **Create Instance**.  
3. Provide a name for your instance (e.g., `demoinstance-windows`).  

---

## Step 2: Placement Options  
- Choose an **Availability Domain (AD)**.  
- Under **Advanced Options**, you can:  
  - Select a **capacity type** (on-demand, preemptible, capacity reservation, or dedicated host).  
  - Specify a **Fault Domain**.  

---

## Step 3: Image and Shape  
1. Under **Image and Shape**, click **Change Image**.  
2. Select a **Windows image** (for example, **Windows Server 2019 Standard**).  
3. Accept the **Oracle & Microsoft Windows Terms of Use**.  
4. Click **Select Image**.  
5. Choose the appropriate **shape** for the instance.  

---

## Step 4: Networking  
- Select an existing **Virtual Cloud Network (VCN)** and **subnet**.  
- Ensure a **public IPv4 address** is assigned.  

---

## Step 5: Login Credentials  
- For Windows instances, **SSH keys are not used**.  
- Instead, an **initial password** is automatically generated.  
- The password will be available on the **instance details page** after creation.  
- On first login, you must **reset this password**.  

---

## Step 6: Create the Instance  
- Leave remaining options as default.  
- Click **Create**.  
- The instance status will change from **Provisioning → Running**.  

---

## Step 7: Security List Configuration  
- Before connecting, update the **VCN Security List**.  
- Allow inbound traffic on **TCP port 3389** for **RDP access**.  

```text
Source CIDR: 0.0.0.0/0  
Destination Port Range: 3389  
Protocol: TCP  
```

---

### Step 8: Connect via RDP
- Copy the instance’s public IP address.
- Use an RDP client (Remote Desktop Connection) and connect to the public IP.
- Enter the username (shown on the instance details page) and the initial password.
- On first login, you will be prompted to reset the password.

---

### Step 9: Verify Access
- After resetting the password, you should successfully connect to the Windows desktop. ✅
