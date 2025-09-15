# 🖥️ Demonstration: Creating an Instance Console Connection

In this demo, we’ll explore how to create and use **instance console connections** in OCI to troubleshoot malfunctioning instances.  
We’ll cover both **Cloud Shell console connection** and **Local console connection**.

---

## 🚀 Step 1: Navigate to Instance
1. Log in to the **OCI Console**  
2. Select your instance (example: `demoinstance_consoleconn`)  
3. Under **Resources**, click **Console Connection**

---

## ☁️ Step 2: Launch Cloud Shell Console Connection
1. Click **Launch Cloud Shell Connection**  
2. OCI automatically:
   - Creates the console connection  
   - Generates a temporary SSH key  
   - Connects without requiring credentials  

🔄 Status transitions: `Creating → Active`

✅ Now you have a live console view — just like sitting in front of the machine.

---

### 🛠️ What You Can Do
- Add or reset SSH keys for `opc` user 🔑  
- Edit system configuration files ⚙️  
- Boot into maintenance mode (bash shell) 🐧  

For example:
- Reboot the instance from console  
- Observe messages such as **“stopped dynamic system tuning daemon”** or **“started Open-iSCSI”**  

---

## 💻 Step 3: Create a Local Console Connection
> Note: Only **one console connection** can exist at a time. Delete the Cloud Shell connection first.

1. Click **Create Local Connection**  
2. Upload your **public key file** 🔑  
3. Once active, click **⋮ (options)** → **Copy VNC Connection for Windows**

---

## 🔑 Step 4: Update SSH Tunnel Command
- Replace the **private key path** in the copied command (appears twice in the string)  
- Example (adjust paths as needed):
  ```powershell
  ssh -i "C:\Users\YourName\.ssh\private_key.pem" -L 5900:localhost:5900 ocid@console.connection.ocid
  ```
- Run this command in PowerShell
- The background job establishes a secure tunnel ✅

---

## 🖥️ Step 5: Connect with VNC Client
1. Open your VNC Viewer
2. Connect using:
  - Host: localhost
  - Port: 5900
3. Click Continue
You now have a VNC console session 🎉

---

## 🎯 Summary
- Cloud Shell Connection: Fast, no keys required, text/serial console access
- Local Connection: Requires SSH keys, allows VNC-based GUI access
With both options, you can remotely troubleshoot, reset, and recover malfunctioning instances.
