# Lesson: Cross-Availability Domain Replication

## What is Cross-AD Replication?
Cross availability domain (AD) replication allows you to replicate:  
- 🔹 Block volumes  
- 🔹 Boot volumes  
- 🔹 Volume groups  

…to another availability domain **within the same region**.

---

## Cost Considerations
- 💰 You will be billed for **storage costs** of the replica in the destination AD.  
- ✅ Replica is billed using the **lower-cost block storage option**, regardless of the source volume type.  
- 🌐 Unlike cross-region replication, **no network costs** apply for cross-AD replication.  
- ⚠️ Important: Cross-region replication does incur network costs between regions.

---

## Limitations
- ⛔ **Cannot resize a volume** while cross-AD replication is enabled.  
  - To resize: disable replication → resize volume → re-enable replication.  
- 🔒 Not supported for volumes encrypted with **customer-managed vault keys**.  

---

## Replica Activation
- To create a new volume from a replica, you must **activate the replica**.  
- Activation creates a **new volume by cloning the replica**.  
- ✅ Replication **does not cause downtime** or impact source volumes.

---

## How to Enable Cross-AD Replication
Example:  
- 📍 Source region: **Ashburn**  
- ➡️ Destination region: **Ashburn** (same region)  
- 🏷️ Select a different **availability domain** (e.g., AD-2).  
- ✏️ Provide a name for the volume replica.  

📌 Difference from cross-region replication:  
- Region name is the **same** (Ashburn → Ashburn).  
- You only select another **availability domain**.
