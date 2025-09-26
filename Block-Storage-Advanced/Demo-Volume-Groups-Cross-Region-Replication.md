# Demonstration: Enabling Cross-Region Replication for a Volume Group

---

## Step 1: Enable Replication in Source Region
As you can see, I am inside the **OCI Console**.  
- Click on the **Volume Group** that I created.  
- Click **Edit**.  
- Enable **Cross-Region Replication**.  
- Select the target region as **Ashburn**.  
- Choose the target availability domain.  
- Provide a replica name: **volume group demo replica**.  

Click **Confirm**, then **Next**, and save the changes.  
This is how you enable cross-region replication for a volume group.

---

## Step 2: Verify in Target Region
Now let’s switch to the target region—**Ashburn**.  
- Go to **Volume Group Replicas** under Block Storage.  
- The replica is currently being provisioned.  
- Notice that the number of replicas is **five**.  

Why five?  
Volume group replicas don’t contain full source data. Instead, they reference **individual replicas** for each volume in the group.

- Under **Block Volume Replicas**, you’ll see replicas for **blockvolume-1, blockvolume-2, blockvolume-3**.  
- Under **Boot Volume Replicas**, you’ll see the two boot volume replicas.  

Returning to the **Volume Group Replica**, after a few moments, it becomes available.

---

## Step 3: Activate the Replica
Once available:  
- You can see both block volume replicas and boot volume replicas listed under resources.  
- Click **Activate**, confirm, and provide a name.  
- OCI creates new block volumes.  

Check under **Block Volumes**:  
- **blockvolume-1, blockvolume-2, blockvolume-3** are now available as activated volumes.

---

## Step 4: Disable Replication in Source Region
Switch back to the source region—**Phoenix**.  
- Go to the **Volume Group**, click **Edit**.  
- Go to **Step 3**.  
- Turn off **Asynchronous Cross-Region Replication**.  
- Confirm.  

You’ll see a message:  
> Replication for the volume group will continue for each volume individually.  

You can choose to disable replication for individual volumes if needed.  
Click **Save Changes**.

---

## Step 5: Verify Termination in Target Region
Back in the **Ashburn region**:  
- The **Volume Group Replica** is terminating.  
- The individual **Block Volume Replicas** and **Boot Volume Replicas** are also terminating.  
- **Activated block volumes remain available**.
