# 🖥️ Demonstration: Launch and Connect to an OCI Compute Instance  

## Step 1: Navigate to the Instances Page  
- I’m logged into the OCI console as the **computeadmin** user in the **Ashburn region**.  
- To get to the **Instances** page, click the **hamburger menu → Compute → Instances**.  

---

## Step 2: Create a New Instance  
Click **Create Instance** and provide the details:  

1. **Name** – I’ll call it `demoinstance`. The name doesn’t need to be unique since the Oracle Cloud Identifier (OCID) uniquely identifies the instance.  
2. **Compartment** – select the appropriate compartment.  
3. **Placement** – choose the Availability Domain (AD1, AD2, or AD3).  
   - Under **Advanced options**, you can also choose the capacity type:  
     - **On-demand (default)**  
     - **Preemptible** – may be reclaimed anytime  
     - **Capacity reservation** – counts against a reservation  
     - **Dedicated host** – isolated infrastructure  
   - You may also choose a **Fault Domain** or let OCI decide.  

---

## Step 3: Configure Image and Shape  
- **Image**: The operating system. Options include:  
  - **Platform images** (Oracle Linux, Ubuntu, etc.)  
  - **Oracle images** (pre-built Oracle enterprise solutions)  
  - **Partner images**, **Custom images**, **Community images**, or an **Image OCID**.  
- For this demo, I’ll select **Oracle Linux 8**.  
- **Shape**: Virtual hardware configuration.  
  - Instance type can be **VM** or **Bare Metal**.  
  - For VMs, select the processor group (AMD, Intel, Ampere, etc.).  
  - I’ll go with a **flexible VM shape** and allocate **7 OCPUs + 38 GB RAM**.  

---

## Step 4: Networking  
- Select an existing **VCN** and **subnet**.  
- Ensure a **public IPv4 address** is assigned if you want external access.  

---

## Step 5: Add SSH Keys  
- Instances use **SSH keys** for authentication.  
- You can:  
  - Let OCI generate a key pair  
  - Upload a public key  
  - Paste a public key  
  - Choose “No SSH keys” (not recommended if you plan to connect)  
- I’ll **paste the public key** we generated in the previous demo.  

---

## Step 6: Storage  
- By default, the **boot volume size** is 46.6 GB.  
- Optionally, specify between **50 GB – 32 TB**, enable **in-transit encryption**, or encrypt with your own key.  

---

## Step 7: Advanced Options  
- **Management** – add initialization scripts (user-data), require auth headers for metadata, etc.  
- **Availability** – choose live migration behavior during maintenance.  
- **Cloud Agent** – enable plugins like monitoring or vulnerability scanning.  

---

## Step 8: Create and Verify  
- Click **Create**.  
- The instance status changes from **Provisioning → Running**.  
- Once running, note the **public IP address** and the default username (**opc**).  

---

## Step 9: Connect via SSH  
In **Cloud Shell**, run:  

```bash
ssh opc@<public-ip>
```

Accept the prompt with yes, and you’re inside the instance. ✅

---

## Step 10: Install Apache & Test
- Install Apache, then place a test page.
- Open the public IP in a browser and confirm the Apache test page loads.
🔑 Important: Allow inbound TCP traffic on port 80 in the VCN Security List for this to work.

---

## Step 11: Required Policies
- To allow the computeadmin user to launch instances, the following IAM policies must be in place:
- Grant permissions to manage instances, volumes, networking, etc.
