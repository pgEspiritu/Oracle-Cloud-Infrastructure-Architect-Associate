# 🖥️ Demonstration: Configuring OCI File System Replication

## 🌍 Regions Used
- **Source Region:** US West (Phoenix)  
- **Target Region:** US East (Ashburn)  

---

## 📖 Step 1: Review Allowed Target Regions
Refer to the official [OCI documentation](#) for the list of **supported target regions**.  
Example: If the source is Phoenix, only specific regions (like Ashburn) are eligible as replication targets.  

---

## 📖 Step 2: Create Networking
1. Create a **VCN** named `demovcn` with a CIDR block.  
2. Create a **public subnet** within the VCN.  

---

## 📖 Step 3: Create the Source File System
1. In the **Phoenix** region, go to **File Systems**.  
2. Select **File System for NFS**.  
3. Name it `sourcefilesystem`.  
4. Click **Create**.  
✅ Source file system is now active.  

---

## 📖 Step 4: Create the Target File System
1. Switch to the **Ashburn** region.  
2. Create a new file system, but this time choose **File System for Replication**.  
   - ⚠️ Remember: this must be an **unexported file system**.  
3. Name it `targetfilesystem`.  
4. Click **Create**.  
✅ Target file system is created.  

---

## 📖 Step 5: Configure Replication
1. Return to the **Phoenix** region.  
2. Open `sourcefilesystem`.  
3. Under **Resources**, select **Replications** → **Create Replication**.  
4. Provide a name, e.g., `demoreplication`.  
5. Enter the **OCID** of the target file system (`targetfilesystem` in Ashburn).  
   - Alternatively, you could create a new target file system here.  
6. Set the **Replication Interval**:  
   - Must be **≥ 60 minutes** (e.g., `480`).  
7. Click **Create**.  

✅ Replication created successfully.  
- Initial status = **Idle** with **0% progress**.  
- Once base copy completes = **100% progress** and status returns to **Idle**.  

---

## 📖 Step 6: Verify Replication on Target
1. Go to **Ashburn** region.  
2. Open `targetfilesystem`.  
3. Check **Snapshots**.  
   - You should see the **replication snapshot** created by the process.  

---

## 📖 Step 7: Failover Scenario (Disaster Recovery)
If the **source region (Phoenix)** is unavailable:
1. Navigate to the **Target region (Ashburn)**.  
2. Open the **Replication Target** (`demoreplication`).  
3. Select the **last replication snapshot**.  
4. Click **Clone** → creates a **new file system** from that snapshot.  
5. Create an **Export** + associate a **Mount Target** to enable access.  

✅ Target file system is now available for use in DR scenarios.  

---

## ✅ Summary
In this demonstration, we:
- Created **source** and **target** file systems.  
- Configured **replication** between Phoenix and Ashburn.  
- Verified snapshots on the target.  
- Reviewed **failover steps** for disaster recovery.  


