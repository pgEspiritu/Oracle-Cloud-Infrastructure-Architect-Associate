# Demo: OS Management Hub Service 🖥️☁️

Welcome to the demo on the **OS Management Hub (OSMH)** service.  
We will continue with the previous scenario where compute instances in our working compartment need management for:  
- OS updates  
- Patches  
- Bug fixes  
- Security updates 🔒  

This ensures that instances remain protected and free from vulnerabilities.  

---

## Demo Workflow 🛠️
In this demo, we will:  
1. **Enable OSMH** using the Policy Analyzer  
2. **Create software sources** (vendor + custom)  
3. **Create profiles** to apply common settings across instances  
4. **Register a compute instance** with OSMH  
5. **Explore reports, jobs, and updates** in the console  

We’ll demonstrate with:  
- One **pre-created instance**  
- One **new instance**  

---

## Step 1: Enable OS Management Hub ✅
- Navigate: **Menu → Observability & Management → OS Management Hub**  
- Select the **compartment** (e.g., root)  
- Click **Enable OS Management Hub**  

🔎 This triggers the **Policy Advisor**, which checks existing policies and groups.  
It will automatically create:  
- **OSMH Admins**  
- **OSMH Operators**  
- **OSMH Instances**  
- **OSMH Policies**  

⚠️ Note: The **dynamic group** only applies to instances in the selected compartment.  
For subcompartments, repeat the Advisor setup.  

---

## Step 2: Create Software Sources 📦

### Vendor Source 🏢
- Choose: **Vendor → OS version → Architecture**  
- Select required sources and click **Add**  
- Instances can now access vendor updates/patches  

### Custom Source ✂️
- Click **Create Custom Source**  
- Example: `Linux 8 Custom Source`  
- Options:  
  - **Enable automatic updates** from vendor  
  - Or **lock version** (useful for lifecycle management)  
- Base it on an existing vendor source  
- Apply filters:  
  - **Include** groups (e.g., Network Servers, Security Tools)  
  - **Exclude** unnecessary packages  
- Submit and finalize  

---

## Step 3: Create Profiles 📋
Profiles define how instances register with OSMH.  

- Click **Create Profile**  
- Choose **OCI Instances** (or on-prem/third-party with management station)  
- Set:  
  - **Software sources**  
  - **Groups**  
  - **Lifecycle environment stage** (Dev, Test, Prod)  
- Option: Set as **default profile** (auto-applied if no profile specified)  
- Click **Create**  

---

## Step 4: Register Instances 🖥️

### New Instance 🚀
1. **Create Instance** → select OS image (e.g., Oracle Linux 8), shape, network (VCN + subnet), and SSH keys  
2. In **Advanced Settings**, enable **OSMH Agent plugin**  
3. Select the profile created earlier → applies software sources + lifecycle stage  
4. Launch instance → verify plugin is **running** in Oracle Cloud Agent  
5. In **OS Management section**, check for scanning → indicates successful registration  

---

### Existing Instance 🔄
1. **SSH into instance** (via Cloud Shell or SSH key)  
2. Check Oracle Cloud Agent version: must be **≥ 1.40.0**  
   ```bash
   sudo yum info oracle-cloud-agent
   ```
3. If outdated → update agent:
   ```bash
   sudo yum install -y oracle-cloud-agent
   ```
4. In OCI Console → go to Instance → Oracle Cloud Agent
  - Enable OSMH plugin
  - Wait until status = Running
5. Instance now appears in OSMH as Registered & Active

---

## Step 5: Monitor & Automate 🔍⚡
### Reports 📊
- Navigate: OSMH → Reports
- View:
  - Required updates
  - Pending patches
  - Compliance details

### Jobs 🗓️
- Go to Jobs → Create Job
- Define:
  - Compartment
  - Schedule (e.g., nightly/weekly updates)
- System scans instances and applies updates automatically

### Instance-Specific Updates 🔧
- Navigate: Instances → Select Instance → Resources → Jobs
- View completed jobs and update history

---

## Key Benefits 🌟
- Centralized, automated OS management
- Secure and consistent patching across fleet
- Flexible setup for both new and existing OCI instances
- Reduced manual effort with scheduled jobs and real-time reports

---

## Wrap Up 🎬
- With just a few initial configurations, OS Management Hub:
  - Simplifies OS lifecycle management
  - Automates patching and updates
  - Provides compliance visibility across your environment
👉 This demo showed how to enable, configure, and use OSMH for both new and existing instances.
