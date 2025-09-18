# 🔔 OCI Object Storage – Automation with Object State Changes  

## ⚙️ Step 1: Enable Object Events  
- Navigate to your **Bucket**.  
- Under **Features**, locate **Emit Object Events** (default: disabled).  
- Click **Enable** → **Save Changes**.  

👉 Once enabled, OCI can emit events for object state changes (e.g., object create, update, delete).  

---

## 📢 Step 2: Create a Notification Topic  
1. Go to **Developer Services → Application Integration → Notifications**.  
2. Create a **Topic** (e.g., `ociaa-topic`).  
3. Inside the topic, create a **Subscription**:  
   - Choose protocol: `Email`.  
   - Enter recipient email address.  
   - Confirm the subscription via the email received from **OCI Notification Service**.  

---

## 📡 Step 3: Create an Event Rule  
1. Go to **Observability & Management → Event Service → Rules**.  
2. Create a new **Rule** (e.g., `ocidemo-rule`).  
3. Define **Conditions**:  
   - **Service**: Object Storage  
   - **Event Type**: `Object Create` (can add multiple types such as `Object Delete`, `Object Update`)  
4. Define **Actions**:  
   - Select **Notifications**.  
   - Choose the **Compartment** and the **Topic** created earlier.  

---

## 🧪 Step 4: Test the Automation  
1. Upload a new object (e.g., `imageD.png`) into the bucket.  
2. The event is emitted and routed to the Notification Service.  
3. You’ll receive an **Email Notification** with details:  
   - 📦 Bucket Name  
   - 📂 Object Name  
   - 📑 Content Type  
   - ⏱ Timestamp  

---

## ✅ Key Takeaways  
- Enabling **Emit Object Events** allows integration of Object Storage with automation workflows.  
- 🔔 Notifications Service delivers events via **Email, PagerDuty, HTTPS endpoints, or Slack**.  
- ⚡ Event Rules can also trigger **Functions** or **Streaming** for advanced automation.  

