# 🚦 Dynamic Routing Gateway (DRG) – Part 3

## 📥 Dynamic Route Import Distribution
- Defines **how route advertisements from DRG attachments are inserted** into DRG route tables.  
- Works using **statements with match criteria**.  
- Example:  
  - If you create a statement with **match = all traffic**, then **all route advertisements** from attachments will be imported into the DRG route table.  

### 🔑 Flow of Import Distribution
1. Create a **statement** with a **match condition**.  
2. If the condition matches (e.g., attachment), all associated routes for that attachment are **imported dynamically** into the DRG route table.  
3. Remember:  
   - Statements have **numbers (priorities)**.  
   - **Lower number = higher priority**.  

---

## 📤 Dynamic Route Export Distribution
- The reverse of import distribution.  
- Defines **how routes are advertised to attachments from their assigned route tables**.  

### 🚫 Exceptions
- Routes imported from an **IPsec tunnel** will **never** be exported to:
  - Other IPsec tunnels  
  - Virtual Circuit attachments  

### ⚙️ Default
- By default, **one export distribution** is automatically created with every DRG.  

---

## ⚖️ ECMP (Equal Cost Multi-Path Routing)
- **Disabled by default**, but can be enabled **per DRG route table**.  
- Provides **load balancing** of network traffic across:  
  - Multiple **FastConnect virtual circuits**  
  - Multiple **IPsec tunnels**  
- Works using **Border Gateway Protocol (BGP)**.  

---

## ⚔️ Route Conflict Resolution
When there are conflicts between routes:  

1. **Static routes > Dynamic routes** (always highest preference).  
2. Between dynamic routes → resolved using **AS path** (Autonomous System path).  

### Priority Order (highest → lowest):
1. **Static routes**  
2. **VCN routes**  
3. **Virtual Circuit routes**  
4. **IPsec tunnel routes**  
5. **Remote Peering Connection (RPC) routes**  

---

## 📊 Example Scenario

### Initial State
- DRG is created with **two default route tables**:
  1. **VCN Route Table**  
  2. **Other Attachments Route Table** (RPC, IPsec, Virtual Circuit, etc.)  
- No static routes.  
- No dynamic routes.  

### After Attaching VCN + RPC
- **VCN Route Table**:  
  - **Static routes**: none  
  - **Dynamic routes**: learns from **VCN + RPC**  

- **Other Attachments Route Table (RPC)**:  
  - **Static routes**: none  
  - **Dynamic routes**: learns only from **VCN**  
  - If VCN has 2 subnets → 2 dynamic route entries  

✅ **Default behavior**:  
- VCN route table learns routes from **all attachment types**.  
- Other attachments (RPC, IPsec, Virtual Circuit) learn **only VCN routes**.  

💡 Note: You can override this with **custom import distributions** and **custom DRG route tables per attachment**.  

---

## ✅ Summary
- **Import Distribution** → governs how routes are **inserted into DRG tables**.  
- **Export Distribution** → governs how routes are **advertised to attachments**.  
- **ECMP** → optional, enables **load balancing** across multiple tunnels or FastConnect circuits.  
- **Route Conflicts** → resolved by **priority (static > VCN > Virtual Circuit > IPsec > RPC)**.  
- **Default behavior**:  
  - VCN route table learns from all attachments.  
  - Other attachments’ route tables only learn VCN routes.  
