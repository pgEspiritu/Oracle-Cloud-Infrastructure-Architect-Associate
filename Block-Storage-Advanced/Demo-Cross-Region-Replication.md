# 🚀 Demonstration: Enabling Cross-Region Replication in OCI

## 🎬 Walkthrough

### 1. Edit an Existing Volume
- Navigate to **Block Volumes**.  
- Select the demo block volume.  
- Click **Edit Volume** → scroll down to find **Cross-Region Replication**.  

📍 Example:  
- Current Region → **Phoenix (US West)**  
- Destination Region → **Ashburn**  
- Availability Domain → Select as needed  
- Replica Name → `demoblockvolume-replica`  

👉 Confirm changes → replication starts, with **cost implications** acknowledged.

---

### 2. Enable Replication at Volume Creation
- When creating a **new volume**, you can directly enable **Cross-Region Replication**.  
- Choose the **destination region** and **availability domain**, and provide a **replica name**.

---

### 3. Verify in Destination Region
- Switch to **Ashburn region**.  
- Go to **Block Volume Replicas** → Replica status = **Provisioning → Provisioned**.  
- Replica shows:  
  - **Source Region** = Phoenix  
  - **Last Sync Time**  
  - **Total Data Transferred (GB)**  

---

### 4. Activate a Replica
- Inside the replica details → Click **Activate Volume**.  
- Provide name (e.g., `demoblockvolume`).  
- Optionally customize **volume size** & **performance tier**.  
- Click **Create Clone**.  

📌 Result:  
- A new **block volume** is provisioned in Ashburn.  
- It is a **clone of the source volume**.  

---

### 5. Managing Activated Volumes
- Under the **Replica**, you can see the list of **Activated Volumes**.  
- Each activation creates a **new block volume clone**.  
- Multiple activations = multiple clones available in the destination region.  

---

## 📝 Key Takeaways
- Cross-region replication ensures **asynchronous ongoing sync** of a volume to another OCI region.  
- Replicas live in **Block Volume Replicas** section of the destination region.  
- To use a replica → **Activate → Clone → New Block Volume**.  
- Activation can be repeated, producing multiple clones.  
