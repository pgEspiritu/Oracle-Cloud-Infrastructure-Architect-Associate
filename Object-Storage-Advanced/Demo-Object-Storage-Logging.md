# 🛠️ OCI Object Storage Logging Demonstration

---

## 🌐 Setup

- Logged in as **Storage Admin** in the **OCI Console**.  
- Working with the bucket: **`ociaabucket-console`**.  
- Bucket visibility: **Public**.  
- Objects are already uploaded to this bucket.  

---

## 🔧 Enabling Logs

### 📖 Option 1: Enable Read Access Events
1. Navigate to **Resources → Logs**.  
2. Enable **Read Access Events**.  
3. Choose a **Compartment**.  
4. Create a **Log Group** → `ReadLogGroup`.  
5. Provide a **Log Name** and set **Log Retention** (default: 1 month).  
6. Click **Enable Log**.  

✅ Read access log is now enabled.  

---

### ✍️ Option 2: Enable Write Access Events
1. Open a new tab → Go to **Observability & Management → Logs**.  
2. Click **Enable Service Log**.  
3. Select:
   - **Resource Compartment**  
   - **Service** → `Object Storage`  
   - **Resource** → `ociaabucket-console`  
4. Configure Log:
   - **Log Category** → Write Access Events  
   - **Log Name** → `writelogs`  
5. Click **Enable Log**.  

✅ Write access log is now enabled.  

---

## 🧪 Testing Logs

1. Open an **object detail page** (since bucket is public).  
2. Copy the **object link** and access it multiple times.  
3. Return to **Logs → Log Name** (e.g., `ReadLogGroup`).  
4. Under **Export Log**, entries appear:  
   - **Request Action** → `GET`  
   - **Bucket ID** → shows bucket identifier  
   - **Client IP Address** → captured  
   - **Pre-authenticated Request** → `false`  
   - **Status Code** → `200`  

✅ Logs are successfully capturing access activity.  

---

## ✅ Key Takeaways

- Two methods to enable logging:  
  - From **bucket resources**.  
  - From **Observability & Management → Service Logs**.  
- Separate logging for **Read** and **Write** events.  
- Logs provide visibility into bucket usage (actions, IPs, status codes, etc.).  
