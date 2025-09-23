# 🌍 Cross-Region Replication in OCI

## 🔑 Key Concepts
- Cross-region replication provides **ongoing automatic asynchronous replication** of block volumes to another region.  
- Supports both **boot** and **block volumes**.  
- Replication is **asynchronous** → data is not mirrored in real time.  

---

## 📌 Replication vs Backup
- **Backups** → Point-in-time snapshot of a volume.  
- **Replication** → Current version of the volume continuously copied to another region.  
- Replication **complements backups**, not replaces them.  

---

## ⚙️ How It Works
1. **Initial Sync**: Full data copy from source → destination region (may take hours depending on size & writes).  
2. **Ongoing Replication**: Continuous, automatic sync with no downtime or performance impact on the source volume.  
3. **Activation**: To use the replica, you must **activate** it, which creates a new volume by cloning the replica.  

---

## 🚫 Limitations
- ❌ Cannot resize a volume with replication enabled → must disable replication first.  
- ❌ Not supported for **customer-managed encryption keys**.  
- Re-enabling replication after resize → full sync starts again.  

---

## 💰 Cost Model
- **Storage Costs**: Replica billed at **lower-cost block storage pricing** in the destination region (regardless of source tier).  
- **Network Costs**: Cross-region data transfer charges apply.  

---

## 🌎 Supported Region Pairs (Examples)
- 🇬🇧 **UK West** → replicate to **UK South** or **London**.  
- 🇺🇸 **US West (Phoenix)** → replicate to **Ashburn** or **San Jose**.  

---

## 📂 Use Cases
- 🛡️ **Disaster Recovery** → activate replica in another region if primary is unavailable.  
- 🚀 **Migration** → move workloads to a different region.  
- 📈 **Business Expansion** → replicate data closer to new customers or teams.  

---

## 🛠️ Enabling Replication
1. Ensure subscription to the **target region**.  
2. Edit the **volume properties** in OCI Console.  
3. Select **Enable Cross-Region Replication**.  
4. Choose **destination region**, **availability domain**, and provide a **replica name**.  
