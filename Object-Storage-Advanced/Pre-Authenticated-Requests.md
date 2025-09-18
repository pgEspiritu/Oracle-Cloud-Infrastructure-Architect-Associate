# 🔑 Pre-Authenticated Requests in OCI Object Storage

## 📌 Why Use Pre-Authenticated Requests?

- Making a **bucket public** is **not a best practice**.  
- Instead, you can use a **Pre-Authenticated Request (PAR)** to:  
  - Allow users temporary access **without requiring OCI credentials**.  
  - Example: Share financial reports with a business partner **without API keys**.  
- A **unique URL** is generated and can be shared.  
- Accessible with standard tools (e.g., `cURL`, SDKs, etc.).  

---

## 📅 Expiration & Limitations

- **Expiration Date** → Required, but can be set far into the future.  
- **Non-Editable** → You **cannot modify** a PAR after creation.  
  - To change options → create a **new PAR**.  
- **Dependency on Creator** →  
  - If the **creator is deleted** or loses permissions, the PAR stops working.  

---

## 🔒 Access Types

A Pre-Authenticated Request can grant:  
- **Read** access  
- **Write** access  
- **Read/Write** access  

---

## 🎯 Scope Options

When creating a PAR, you can grant access to:  
- **Entire Bucket** → All objects.  
- **Specific Object** → A single object only.  
- **Object Prefix** → All objects with a given prefix.  

⚠️ **Important Restriction**: PARs **cannot** be used to **delete buckets or objects**.  

---

## ✅ Key Takeaways

- Use **PARs** instead of making buckets public.  
- Share access securely via a **time-bound URL**.  
- Access depends on the **creator’s permissions**.  
- Choose the right **access type** (read, write, or both) & **scope** (bucket, object, or prefix).  
