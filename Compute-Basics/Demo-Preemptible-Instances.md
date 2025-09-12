# ⚡ Demonstration: Creating a Preemptible Instance  

In this demonstration, we will learn how to create a **preemptible instance** in OCI and configure notifications for preemption events.  

---

## 🖥️ Steps to Create a Preemptible Instance  

1. **Login** to the OCI Console as `computeadmin`.  
2. Go to **☰ Hamburger Menu → Compute → Instances**.  
3. Click **Create Instance**.  
4. Enter a name: `preemptible-demoinstance`.  
5. Choose the desired **compartment**.  

### 📍 Placement & Capacity  
- Click **Edit** to select an **Availability Domain**.  
- Expand **Advanced Options**.  
- Under **Capacity Type**, select **Preemptible Capacity** (instead of On-demand).  
- Option available: **Permanently delete boot volume** when capacity is reclaimed (enabled by default).  
- Fault Domain → Let Oracle choose or select manually.  

### 🖼️ Image & Shape  
- Choose your required **Image** (e.g., Oracle Linux, Windows, etc.).  
- Select the desired **Shape**.  

### 🌐 Networking  
- Select existing **VCN** (e.g., `demovcn`).  
- Select **Subnet** (e.g., `subnetA`).  
- Optionally, assign a **Public IP Address**.  

### 🔑 SSH Keys  
- Generate a new SSH key pair:  
  ```bash
  ssh-keygen
  ```
- Copy the public key and paste it in the console.

### 💾 Boot Volume Options
- Default size = 46.6 GB
- Custom size allowed = 50 GB – 32 TB
- Options:
  - ✅ In-transit encryption
  - 🔐 Customer-managed encryption keys

### ▶️ Launching the Instance
- Click Create Instance.
- The instance will first show as Provisioning → Running.
🔹 Note: Some actions are not available for preemptible instances:
   - ❌ Start
   - ❌ Stop
   - ❌ Reboot
⏳ If capacity is reclaimed in less than 1 minute → No charge is applied.

### 🔗 Connecting to the Instance
- Copy the Public IP Address.
- Use opc as the username:
  ```bash
  ssh opc@<public-ip>
  ```
- Once connected, verify in the Instance Information that the Capacity Type = Preemptible.

---

## 📢 Event Notifications for Preemption
To receive alerts before OCI reclaims the instance:
1. Log in as Tenancy Administrator.
2. Go to ☰ Hamburger Menu → Observability & Management → Events Service → Rules.
3. Click Create Rule.
4. Rule Name: preemptiblerule.
5. Description: Send a notification when a preemptible instance is terminated.

⚙️ Rule Conditions
- Service Name: Compute
- Event Type: Instance → Preemption Action

📩 Rule Actions
- Choose Notifications (or Streaming / Functions).
- Select Compartment and Topic.
- Save the rule.

📌 OCI emits an Instance Preemption Action Event
⏳ Sent 30 seconds before termination begins.

---

## ✅ Summary
- Created a Preemptible Instance.
- Learned restrictions (cannot stop/start/reboot, auto-termination possible).
- Configured Event Service to notify when the instance is about to be terminated.
