# 🌐 Lesson: Network Sources in OCI

## 🔐 What are Network Sources?

**Network sources** are a mechanism to control access based on **originating IP addresses**.

> Think of it like a gatekeeper who allows access to your resources only if the request is from IP addresses that you have specified.

---

## 🧭 How Does It Work?

It’s a **two-step process**:

### ✅ Step 1: Define IP Addresses

- Create a **network source object**
- Add IP addresses to this object  
  - IPs can be from your **Virtual Cloud Network (VCN)**
  - Or **public IP addresses**
- You can:
  - Create a **long list** of IPs
  - Add just a **single IP address**

> This flexibility allows you to define access control according to your specific needs.

---

### ✅ Step 2: Write a Policy with Network Source Condition

- Write a policy to allow a **group of users** to perform actions on resources.
  Example:
  ```text
  allow group <domain>/<group> to manage <resource> in tenancy
  ```
- Add a **network source condition** to scope access further

### 🧩 How?

Use this syntax in your policy:

```text
request.networkSource.name = '<your-network-source-name>'
```

> This ensures that access is only granted if the request originates from the IP addresses listed in your network source object.


## 🎯 Why Use Network Sources?

Using network sources allows you to:

- 🛡️ **Protect critical resources**
- 📍 **Restrict access to specific locations**, such as:
  - Office IP ranges
  - Trusted public IPs
  - Specific VCNs

---

## ✅ Summary

- Use **network sources** to control access based on IP addresses
- Add a **condition** in your IAM policy to enforce IP-based restrictions
