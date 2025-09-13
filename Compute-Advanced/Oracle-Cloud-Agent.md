# Oracle Cloud Agent 🛰️

## What is Oracle Cloud Agent? 🤔
- A lightweight process that manages **plugins** running on compute instances.  
- **Installed by default** on current platform images.  
- Plugins are bundled with Oracle Cloud Agent.  

👉 **Role of Plugins**:  
- Collect performance metrics 📊  
- Install OS updates 🔄  
- Perform instance management tasks ⚙️  

---

## Requirements ✅
To use plugins on an instance:
1. **Oracle Cloud Agent** software must be installed.  
2. Plugins must be **enabled**.  
3. Plugins must be **running**.  

---

## Plugin Examples 🔌

### 🔒 Bastion
- **OCI Bastion Service** → Provides restricted, time-limited secure access to resources without a public endpoint.  
- Requires the **Bastion plugin** to be enabled and running.  

### 🛠️ OSMS Agent
- **Operating System Management Service (OSMS)** → Manages patches and updates for OS environments.  
- Requires the **OSMS plugin** to be enabled and running.  

### 📜 Compute Instance Run Command
- Facilitates running scripts within the instance using the **Run Command** feature.  

---

## Plugin Management ⚡
- You can **enable or disable** plugins as needed.  
- When creating an instance from a **current platform image**, Oracle Cloud Agent is installed by default.  
- If using another supported image, you can **manually install** Oracle Cloud Agent.  

---

## Key Takeaways 📝
- Oracle Cloud Agent = process for managing plugins.  
- Plugins handle monitoring, updates, and management.  
- Bastion, OSMS, and Run Command are common plugins.  
- Installed by default, but can also be manually installed.  
