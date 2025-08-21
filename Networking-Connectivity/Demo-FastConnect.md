# Lesson: Creating a FastConnect Connection (Console Walkthrough)
  
There are two main options:

1. **FastConnect Partner**  
2. **FastConnect Direct** (includes both **Third-Party Provider** and **Co-Location** models)

---

## 🔹 Option 1: FastConnect Partner

1. **Select a Partner**
   - In the Console, choose **FastConnect Partner**.
   - Based on your region, you’ll see a list of available partners (e.g., **Equinix**).
   - Select the partner of your choice.

2. **Provide Connection Details**
   - **Name**: Enter a name for your connection.  
   - **Compartment**: Choose the compartment for the resource.  
   - **Virtual Circuit Type**:
     - **Private** (requires a Dynamic Routing Gateway).  
     - **Public** (for accessing OCI public services).  

3. **Traffic Options**
   - Choose whether you want:  
     - **All traffic**, or  
     - **Only IPSec over FastConnect traffic** (encryption option).

4. **Routing and Bandwidth**
   - Select the **Dynamic Routing Gateway (DRG)** (if using private peering).  
   - Configure **provisioned bandwidth** (1 Gbps to 10 Gbps).  

5. **BGP Configuration**
   - Enter your **BGP Peering IP Address** (from /28 to /31 range).  
   - (Optional) Provide **Oracle BGP IPv4 address**.  
   - Provide your **ASN** (Autonomous System Number), either public or private.  

⚠️ Note: The partner handles the physical connectivity, so you do not deal with cabling or LOA in this case.  

---

## 🔹 Option 2: FastConnect Direct  
(*Includes both **Third-Party Provider** and **Co-Location**.*)

1. **Select Direct**
   - In the Console, choose **FastConnect Direct**.  
   - Notice that the **partner selection option disappears**.  

2. **Create Connection**
   - Provide a **name** for the connection.  
   - Select whether you want a **Cross-Connect Group** or a **Single Cross-Connect**.  

3. **Configure Physical Connection**
   - Choose **port speed** (depends on available options in your location).  
   - Select the **FastConnect location** (the physical data center site).  

4. **Letter of Authorization (LOA)**
   - After creating the cross-connect, **Oracle provides an LOA**.  
   - You must hand over the LOA to the **data center provider** or **third-party carrier**.  

5. **Cabling and Activation**
   - The data center personnel complete the cabling.  
   - Once done, you can **activate the cross-connect** in OCI Console.  

---

## ✅ Summary

- **Partner Model**:
  - Easy to set up.  
  - Select partner → Provide connection + BGP details → Partner provisions connectivity.  
  - **No LOA needed**.

- **Direct Model** (Third-Party Provider / Co-Location):
  - Create cross-connect → Receive **LOA** → Hand it to data center/carrier → Cabling → Activate.  
  - Provides more control and flexibility but requires manual coordination.  
