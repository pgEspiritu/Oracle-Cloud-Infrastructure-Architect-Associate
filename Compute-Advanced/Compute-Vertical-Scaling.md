# 📈 Compute Vertical Scaling

## 🔍 What is Vertical Scaling?
Vertical scaling (also called **scale up** or **scale down**) means adding or removing resources to an instance so that it meets demand.  

- **Scale Up** → Increase performance.  
- **Scale Down** → Reduce resources to save costs.  

You can change the **shape** of a VM instance without needing to rebuild or redeploy applications.  

---

## ⚙️ How It Works
- In the OCI Console, you can **Edit Shape** of an instance.  
- The **shape series** and **image** of the original instance determine which target shapes are available.  
- If the instance is **running** when the shape is changed, it will be **rebooted**.  

---

## ✅ What Remains Unchanged
- Public & private **IP addresses**  
- **Volume attachments**  
- **VNIC attachments**  

---

## 🔄 What Changes After Scaling
- **OCPUs** (increase/decrease)  
- **Memory allocation**  
- **Network bandwidth**  
- **Maximum number of VNICs**  

---

## 📌 Key Considerations
1. **Automation via Monitoring Service**  
   - Use metrics & alarms.  
   - Alarms can trigger a **Function** to adjust the VM shape automatically.  

2. **Reboot Required**  
   - Scaling a VM always causes a **reboot**.  

---

## 📝 Summary
- Vertical scaling lets you **adjust resources** for a VM by changing its shape.  
- Scaling up improves performance, while scaling down reduces cost.  
- Some settings remain the same (IP, volumes, VNICs), while CPU, memory, bandwidth, and VNIC limits are affected.  
- You can automate scaling decisions using **monitoring + functions**.  
