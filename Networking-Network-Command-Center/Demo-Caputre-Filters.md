# 🎥 Demonstration: Capture Filters in OCI

## 📌 Introduction
In this demo, we will learn how to:
1. Create a **Capture Filter**  
2. Enable **Flow Logs** with the capture filter  
3. Observe how the filter affects captured traffic  

---

## 🛠️ Step 1: Create a Capture Filter
1. Navigate to **OCI Console → Networking → Network Command Center → Capture Filters**  
2. Click **Create Capture Filter**  
3. Fill in the details:
   - **Name**: `demo-capture-filter`  
   - **Filter Type**: `Flow log capture filter`  
   - **Sampling Rate**: `100%`  

4. Define Rules:
   - **Traffic disposition**: `All → Include`  
   - **Source IP / Destination IP**: *leave default*  
   - **IP Protocol**: `All`  

👉 Click **Create capture filter**  

---

## 🛠️ Step 2: Enable Flow Logs
1. Go to **Network Command Center → Traffic Monitoring → Flow Logs**  
2. Click **Enable flow logs**  
3. Fill in details:
   - **File name prefix**: (enter any name)  
   - **Flow log destination**: create a new **Log Group** if not available  

4. Select the **Capture Filter** created earlier  
5. Add **Enablement Points**:
   - Click **Add enablement point → Select VCN**  
   - Choose your VCN (e.g., `npademovcn`)  
   - Click **Add enablement points**  

6. Click **Next → Enable flow logs**  

✅ Flow logs are now enabled.  

---

## 🛠️ Step 3: View Logs
- Go to your **Log Group**  
- Wait a few moments, then you’ll see log events:  
```text
REJECT UDP ...
ACCEPT TCP ...
REJECT UDP ...
```
- Since the capture filter included **all traffic**, both `ACCEPT` and `REJECT` were captured.  

---

## 🛠️ Step 4: Modify Capture Filter Rules
Now let’s refine the filter to capture **only REJECT traffic**.

1. Go back to **Capture Filters → demo-capture-filter**  
2. Click **Manage Rules**  
3. Change:
 - **Traffic disposition** → `Reject`  

4. Save changes  

---

## 🧪 Step 5: Observe the Difference
- Return to your **Log Group**  
- Wait for new log entries  
- This time, only `REJECT` messages are captured:  
```text
REJECT UDP ...
REJECT TCP ...
REJECT UDP ...
```

📊 Previously → mix of **ACCEPT + REJECT**  
📊 Now → only **REJECT** traffic  

---

## ✅ Key Learning
- Capture Filters can be **applied to Flow Logs or VTAP**  
- By tweaking the **rules & disposition**, you can focus only on traffic relevant for troubleshooting  
- Example: Filtering only **rejected packets** helps diagnose network security issues quickly  
