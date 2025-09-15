# 🛠️ Lesson: Infrastructure Maintenance in OCI

## 🔄 Migration Options
OCI offers **three migration methods** during infrastructure maintenance:

1. **Live Migration** ⚡  
2. **Reboot Migration** 🔁  
3. **Manual Migration** 🧑‍💻  

---

## ⚡ Live Migration
- During a maintenance event, supported VM instances are automatically moved from the affected physical host to a **healthy host**.  
- **Minimal disruption** to running instances.  
- Infrastructure maintenance events are **emitted at the start and end** of migration.  
- **Supported only on Linux OS** and **specific shapes**.  

---

## 🔁 Reboot Migration
- If **live migration is not supported**, OCI schedules a **reboot migration** within **14–16 days**.  
- A **notification** is sent with a due date.  
- If you do not reboot proactively:
  - OCI will stop the instance  
  - Migrate it to a healthy host  
  - Restart it automatically  

⚠️ Important:  
- **Downtime occurs** during reboot migration.  
- You can control when downtime happens by reboot migrating **before the due date**.  
- **OS-level reboot ≠ Instance reboot** from Console/CLI/API (OS reboot does not trigger migration).  

---

## 🧑‍💻 Manual Migration
- Required when the **reboot maintenance field is empty**.  
- You must:
  - **Terminate** the instance  
  - **Recreate** it on a new host  
- 🔑 **Preserve the boot volume** when terminating, to avoid data loss.  

---

## 🔄 Automatic Recovery
When underlying infrastructure fails:  
- **Standard VMs** → recovered using **reboot migration** to a healthy host.  
- **Dense I/O VMs** → rebooted on the **same physical host**.  

⚠️ If recovery on the same host fails:  
- OCI notifies you to **delete/terminate** the instance within **14 days**.  
- If not deleted:  
  - OCI **disables the instance** on the deadline  
  - Deletes it within the next **7 days**  

✅ **Boot and data volumes are preserved**.  

---

## 🎯 Summary
- **Live Migration** → Minimal disruption, supported on Linux and specific shapes  
- **Reboot Migration** → Short downtime, due date scheduled, requires proactive reboot  
- **Manual Migration** → Terminate and recreate, preserve boot volume  
- **Automatic Recovery** → Ensures VM continuity, but may require manual action for Dense I/O VMs  
