# 📘 Lesson: Run Command in OCI

## 🔎 What is Run Command?
Run Command allows you to **remotely configure, manage, and troubleshoot** compute instances by running scripts **within the instance**.  

- 🛠️ You can run commands even when the instance **does not have SSH access** or **open inbound ports**.  
- 💻 Supported on **platform images**:
  - Oracle Autonomous Linux  
  - Oracle Linux  
  - CentOS  
  - Windows Server  
- 🚫 **Not supported**: Ubuntu  

## ⚙️ Execution Details
- 🐧 On **Linux instances**, scripts run in a **bash shell** by default.  
- 🪟 On **Windows instances**, scripts run as a **batch file**.  
- 📏 **Size limits**:
  - Script size (plain text upload): **4 KB**  
  - Script output (plain text): **1 KB**  
- ☁️ For larger scripts or outputs, use **Object Storage** to upload or save results.  

## 💡 Example Use Cases
- 🔄 Automating configuration of **secondary virtual network interface cards (VNICs)**  
- 🔍 Troubleshooting **SSH connectivity issues**  

---

✅ **Summary:**  
The **Run Command** feature is a secure and efficient way to manage compute instances **without relying on SSH**, helping administrators automate tasks and resolve issues quickly.  
