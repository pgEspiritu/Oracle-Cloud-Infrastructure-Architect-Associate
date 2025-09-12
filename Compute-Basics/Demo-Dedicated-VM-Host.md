# 🖥️ Working with Dedicated Virtual Machine Hosts (DVH)

This guide walks you through creating a **Dedicated Virtual Machine Host** and launching VM instances on it in OCI.

---

## 1️⃣ Navigate to Dedicated VM Hosts
- Log in as **computeadmin**.  
- Go to ☰ **Hamburger Menu → Compute → Dedicated Virtual Machine Hosts**.  

---

## 2️⃣ Required IAM Policies
Before creating a DVH, ensure IAM policies are in place:

- To **manage DVHs**:
```bash
Allow group computeadmins to manage dedicated-vm-hosts in compartment <compartment-name>
Allow group computeadmins to manage instances in compartment <compartment-name>
```

- To **launch instances on DVHs**:
```bash
Allow group computeadmins to use dedicated-vm-hosts in compartment <compartment-name>
```

---

## 3️⃣ Create a Dedicated Virtual Machine Host
- Click **Create**.  
- Name: `DVH-demo`  
- Select **compartment** and **availability domain**.  
- Choose a **host shape** (determines capacity + supported VM shapes).  
- Example: `DVH.Standard2.52` → 52 OCPUs.  
- Click **Create** → Host status = **Active**.  

📊 **Note**:  
- `Total OCPUs = 52` (billed).  
- `Available OCPUs = 48` (some reserved for VM management).  
- You are billed for the **host**, not the individual VM instances (except image license costs).  

---

## 4️⃣ Launch a VM Instance on DVH
Two options:  

### Option A – From Instances
1. Go to **Compute → Instances → Create Instance**.  
2. Under **Placement → Show Advanced Options → Capacity Type**, select **Dedicated Host**.  
3. Pick the host (`DVH-demo`).  
 - Remaining OCPUs & memory are displayed.  
4. Select a compatible shape.  
 - Example: `VM.Standard2.4` (supported by `DVH.Standard2.52`).  
5. Click **Create**.  

### Option B – From Hosted Instances
- On the DVH details page → **Hosted Instances → Create Instance**.  
- Takes you to the same instance creation workflow.  

---

## 5️⃣ Verify Resource Usage
- Example:  
- Total OCPUs = 48  
- Remaining OCPUs = 44  
- Total Memory = 736 GB  
- Remaining Memory = 676 GB  

👉 The difference reflects the resources consumed by the new VM instance (`4 OCPUs` + `60 GB memory` in this case).  

---

## ✅ Summary
- Dedicated Virtual Machine Hosts provide **single-tenant isolation**.  
- IAM policies must allow **management** and **usage**.  
- VM instances consume host capacity (OCPUs & memory).  
