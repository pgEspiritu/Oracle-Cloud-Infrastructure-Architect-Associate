# 📑 OCI Object Storage Logging

## 🔎 Overview

- You can configure **read** and **write access events** to be sent to the **OCI Logging Service**.  
- **Service Logs** are logs emitted by OCI services (e.g., Object Storage).  
- Logs follow the **open-source Fluentd format**.  
- Logging integrates with **OCI Logging Analytics Service** for enrichment and visualization.  

---

## 📂 Logging Configuration

- **Enabled at the bucket level**.  
- Two log categories:
  - 📖 **Read Access Events** → actions: `GET`, `LIST`, `HEAD`  
  - ✍️ **Write Access Events** → actions: `PUT`, `POST`, `DELETE`  

---

## ⚙️ Enabling Logs

1. Navigate to **Logs** under **Resources**.  
2. Enable **Read** and/or **Write** access logs.  
3. Alternatively, enable logs via **Observability & Management**.  
4. Specify:  
   - **Log Group**  
   - **Log Name**  

---

## ✅ Key Takeaways

- Logging provides visibility into **bucket-level operations**.  
- Read and Write events are tracked **separately**.  
- Logs can be further analyzed with **Logging Analytics**.  
