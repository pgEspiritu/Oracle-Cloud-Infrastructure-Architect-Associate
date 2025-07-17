# 🛠️ Demo: Creating an Identity Domain in OCI

This demo walks through the steps of creating **multiple identity domains** (Production & Development) in an OCI tenancy for administrative isolation.

---

## 🎯 Use Case
- You have a subscribed OCI **tenancy**.
- By default, OCI provides a **Default Domain**.
- You want to **separate identities** for:
  - **Production Team**
  - **Development Team**

---

## 🧱 Step 1: Create Dedicated Compartments
1. **Log in** to the OCI Console using **default domain admin credentials**.
2. Go to:  
   **☰ Menu > Identity & Security > Compartments**
3. Click **Create Compartment**:
   - Name: `Production`
   - Add Description (optional)
4. Repeat for `Development`.

---

## 🌐 Step 2: Create Identity Domains
1. Go to:  
   **☰ Menu > Identity & Security > Domains**
2. Click **Create Domain**.
3. For **Production Domain**:
   - Select Compartment: `Production`
   - Domain Name: `production` or `production-team`
   - Domain Type: `Free` (can be upgraded later)
   - Create a **domain admin** by entering name & email.
   - Confirm & click **Create Domain**.
4. Repeat for the **Development Domain**.

---

## 📧 Step 3: Activate Domain Admin Account
1. You will receive an **activation email**.
2. Click **Activate Account**.
3. Set a **password** (based on the password policy).
4. Click **Continue to Sign In**.

---

## 🔐 Step 4: Login & Secure Domain Admin Account
1. Select your **new identity domain** during login.
2. Enter domain admin **username & password**.
3. Update your **profile info** or skip.
4. Enable **Secure Verification**:
   - Choose **Mobile App** as 2FA method.
   - Scan QR code with your **Authenticator App**.
   - Your device is now the **second factor**.
5. You are now logged in as **domain admin**.

---

## ✅ Step 5: Verify Domain Admin
1. Go to:  
   **☰ Menu > Identity & Security > Domains**
2. Select `Production` domain.
3. Navigate to **Groups** > **Domain Administrator Group**.
4. Confirm your **admin user** is listed.

---

## 🔁 Repeat for Development Domain
Follow the same process to create and configure the **Development** identity domain and its **admin account**.

---

## 🧾 Summary
- Created **two compartments**: Production & Development.
- Created **two identity domains**: one for each team.
- Set up **domain-specific admin users**.
- Configured **multi-factor authentication** for secure sign-in.
