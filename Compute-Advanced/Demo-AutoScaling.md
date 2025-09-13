# OCI Autoscaling Demonstration 🚀

In this demonstration, a walk through how to set up **autoscaling** in Oracle Cloud Infrastructure (OCI).  
1. Creating an **Instance Configuration**  
2. Creating an **Instance Pool**  
3. Creating an **Autoscaling Configuration**  

---

## Step 1: Create an Instance Configuration ⚙️
- An **Instance Configuration** is a template for launching compute instances.  
- **Prerequisite IAM Policies**:  
  - Allow users to manage instance configurations, pools, and cluster networks.  
  - Allow users to manage autoscaling configurations.  
- **Steps**:  
  1. Go to **Compute → Instance Configurations → Create**.  
  2. Name it (e.g., `demo-instance-config`).  
  3. Select compartment, AD, image, and shape.  
  4. Configure networking and add SSH keys.  
  5. Click **Create**.  

✅ Instance configuration created successfully.  

---

## Step 2: Create an Instance Pool 🖥️🖥️
- An **Instance Pool** manages multiple compute instances as a group.  
- **Steps**:  
  1. From the instance configuration, click **Create Instance Pool**.  
  2. Name it (e.g., `demo-instance-pool`).  
  3. Define initial instance count (e.g., 2).  
  4. Select ADs, VCN, and subnets.  
  5. Click **Create**.  

📌 The pool provisions instances across the selected availability domains.  

---

## Step 3: Create an Autoscaling Configuration 📈
- Go to **Compute → Autoscaling Configurations → Create**.  
- Attach the instance pool and name it (e.g., `demo-auto-scaling-config`).  
- **Choose Policy Type**:  
  - **Metric-based** → Triggered by CPU or memory utilization.  
  - **Scheduled-based** → Triggered by Cron expressions at set times.  

### Example Metric-Based Policy
- Scale **out**: Add 1 instance if CPU > **85%**.  
- Scale **in**: Remove 1 instance if CPU < **60%**.  
- Limits:  
  - Minimum = 1  
  - Maximum = 3  
  - Cooldown = 300 seconds  

✅ Autoscaling configuration is now enabled.  

---

## Scaling in Action ⚡

### Scale In 🔻
- If CPU utilization drops below 60%, autoscaling terminates an instance.  
- Example: Pool size reduces from **2 → 1 instance**.  

### Scale Out 🔺
- Simulate high load by installing and running the `stress` package.  
- If CPU rises above 85%, autoscaling provisions a new instance.  
- Example: Pool size increases from **1 → 2 instances**.  

---

## Key Takeaways 📝
- **Instance Configurations** = reusable templates.  
- **Instance Pools** = managed groups of instances.  
- **Autoscaling Configurations** = dynamic scale-in and scale-out policies.  
- Scaling can be **metric-driven** or **schedule-driven**.  
