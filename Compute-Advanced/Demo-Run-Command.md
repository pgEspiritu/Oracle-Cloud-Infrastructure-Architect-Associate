# 🚀 Demo: Using Run Command in OCI

In this demo, we’ll walk through how to configure policies, dynamic groups, and use **Run Command** to execute scripts remotely on an OCI compute instance.

---

## 🛠️ Prerequisites
- Access to the **OCI Console**  
- Logged in as **Tenancy Administrator** initially  
- A running **compute instance** in your compartment  

---

## 🔑 Step 1: Create IAM Policy for Run Command
1. Navigate to **Identity & Security → Identity → Domains → Default → Groups**.  
   - Ensure the **computeadmins** group exists.  

2. Go to **Policies → Create Policy**.  
   - Name: `RunCommandPolicy`  
   - Compartment: **Root**  
   - Add the following statement in **Manual Editor**:  

   ```hcl
   Allow group computeadmins to manage instance-agent-command-family in tenancy
   ```
   
---

## 👥 Step 2: Create a Dynamic Group
  1. Go to Identity → Domains → Default → Dynamic Groups.
  2. Click Create Dynamic Group.
     -  Name: demodg
     -  In the Rule Builder, add a rule using your instance OCID:
     ```hcl
     instance.id = '<INSTANCE_OCID>'
     ```
   3. Save the dynamic group.

---
      
## 📜 Step 3: Update Policy for Dynamic Group
Edit the RunCommandPolicy and add this statement:
```hcl
Allow dynamic-group demodg to use instance-agent-command-execution-family in tenancy 
where request.instance.id = target.instance.id
```

---

## 👤 Step 4: Switch to Compute Admin User
- Sign out from Tenancy Administrator.
- Log in as a user from the computeadmins group.

---

## ⚙️ Step 5: Verify OCI Agent Plugin
- Go to your compute instance → Oracle Cloud Agent → Plugins.
- Ensure Command Plugin is enabled and running.

---

## 🖥️ Step 6: Configure Sudo Permissions

SSH into the instance and configure permissions for the oci_run user:
```bash
echo "oci_run ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/oci_run
sudo visudo -c  # ✅ Ensure syntax check passes
```

---

## ▶️ Step 7: Create and Run Command
1. Go to Compute Instance → Resources → Run Command.
2. Click Create Command:
  - Name: runcommanddemo
  - Timeout: 3600s (default)
  - Script:
  ```bash
  sudo yum install -y httpd
  sudo systemctl start httpd
  echo "This is a test page" | sudo tee /var/www/html/index.html
  ```
3. Choose Output as text (or Object Storage if needed).
4. Click Create Command.

---

## 📊 Step 8: Monitor Execution
- Delivery Status: Acknowledged
- Execution Status: Succeeded ✅
Open the instance’s public IP in a browser → you should see:
```bash
This is a test page
```

---

## 📄 Step 9: View Command Details
- From the console, click View Command Details.
- You can see the execution logs and output of the script.

---

🎯 Summary
Using Run Command, you can:
- Run scripts without SSH access
- Automate installations (e.g., Apache web server)
- View outputs directly in the OCI Console
