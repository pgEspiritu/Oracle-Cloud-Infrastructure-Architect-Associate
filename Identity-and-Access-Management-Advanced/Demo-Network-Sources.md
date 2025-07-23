# 🌐 Network Sources Demo – Restrict Access by IP

## 👋 Introduction

Hello, and welcome to this demo on **network sources**.

For this demo, we’ll consider a scenario where:

- We have a **user** who is part of the **storage-admin** group.
- The user has permission to **manage object-family** in the **Production** compartment.
- This means the user can **create/manage buckets** in the production compartment.

---

## 🔒 Goal

We want to **add a condition** that allows the user to **create buckets only from the office location**.

This ensures:

- 🚫 No unauthorized bucket creation from external networks
- ✅ All bucket activities occur in a **trusted environment**

We'll achieve this using **network sources** in a **simple 2-step process**:

---

## 🪜 Steps

### ✅ Step 1: Create a Network Source

1. Login as **tenancy admin** (with permissions to manage policies and network sources).
2. Go to:  
   **Main Menu → Identity & Security → Network Sources**
3. Click **Create Network Source**
4. Name it: `officenet`
5. Under **IP Addresses**:
   - Select **Public IP**
   - Enter a **random public IP address** for now (e.g., `1.1.1.1`) for testing
6. Click **Create**

✅ **Step 1 Complete**

---

### ✅ Step 2: Update IAM Policy

1. Go back to:  
   **Main Menu → Identity & Security → Policies**
2. Select the policy allowing storage-admin to manage object storage
3. Edit the policy statement:
   ```text
   Allow group 'Default'/'StorageAdmin' to manage object-family in compartment Production 
   where request.networkSource.name='officenet'
   ```
4. Click Save

This condition will now:

- ✅ Allow actions **only if** the request originates from IPs in `officenet`
- ❌ Deny all other external IPs

---

## 🧪 Test the Policy

### 🔄 As Storage Admin User

1. Login as a user from the `storage-admin` group  
2. Navigate to:  
   `Storage → Buckets → Production Compartment`  
3. Click **Create Bucket**  
4. Leave all default settings and click **Create**

#### 🔍 Expected Result

- ❌ **Authorization Error** — request not from whitelisted IP (`1.1.1.1`)

---

## 🔁 Update Network Source with Actual IP

1. Get your current public IP  
   (Search: _"What is my IP"_)  
2. Copy the IP address  
3. Back in the console:  
   - Go to **Network Sources**  
   - Select `officenet`  
   - Click **Add Network**  
   - Choose **Public IP** and paste your real IP  
   - Delete the old `1.1.1.1` test IP  
4.  Click **Update**

---

## ✅ Test Bucket Creation

1. Go back to the **storage-admin** user session
2. Create a Bucket (Accept Default Values)
   > Error: Not Authorized to create a Bucket (Due to unauthorized IP Address stated in the Policy)
3. Try to add a Network Source with your IP Address.
5. Try creating the bucket again

- ✅ **Bucket creation successful** — request is now from a valid IP

---

## 🧠 Conclusion

This demo shows how to:

- Create **network sources**
- Add **trusted IP addresses**
- Use **policy conditions** to enforce **IP-based access**

---

### 🎯 This ensures that:

- Only **trusted locations** can perform critical actions  
- **Security posture** is improved without over-complicating IAM
