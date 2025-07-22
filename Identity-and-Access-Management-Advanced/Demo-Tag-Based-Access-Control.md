# 🚫 Prevent Accidental Deletion with Tag-Based Access Control in OCI

## 🏗️ Scenario Overview

We have **four compute instances** running in a **demo compartment**.

One of these VMs—`Prod-Web-VM`—is running a **mission-critical application**.  
If someone **accidentally deletes** this instance, it could lead to:

- ❌ Application outage  
- ❌ Potential data loss

Even if the user has **IAM permissions**, we want to ensure this **specific instance cannot be deleted**.

---

## 🔖 Why Tag-Based Access Control?

Tags in OCI are **metadata** that can be assigned to cloud resources. They help:

- Organize and manage resources
- Label based on environment, purpose, owner, etc.
- In our case: **Flag resources as protected**

---

## 🛠️ Step-by-Step Implementation

### 1️⃣ Create a Tag Namespace

1. In the OCI Console, search for **"Tag"**
2. Go to **Tag Namespace** under *Services*
3. Click **Create Tag Namespace**
4. Choose your **working compartment**
5. Name it: `operations`
6. Add a description and click **Create**

---

### 2️⃣ Create Tag Key Definition

1. Click into the `operations` namespace
2. Click **Create Tag Key Definition**
3. Key: `instance_type`
4. Description: Classify instance criticality
5. Value Type: **List of values**
6. Values: `critical`, `non-critical`
7. Click **Create Tag Definition**

---

### 3️⃣ Apply Tags to Instances

#### For `Prod-Web-VM`:
- Go to the instance → **More Actions** → **Add Tags**
- Select:
  - **Namespace**: `operations`
  - **Key**: `instance_type`
  - **Value**: `critical`

#### For Other VMs:
- Tag them with:
  - **Key**: `instance_type`
  - **Value**: `non-critical`

✅ All compute instances are now tagged.

---

### 4️⃣ Configure IAM Policy

Go to:
- **Identity & Security** → **Policies**
- Find your existing policy and click **Edit**

#### Original Policy:
```text
Allow group 'Default'/'SecOps' to manage instance-family in compartment Sandbox
```

Modified Policy with Tag Condition:
```text
Allow group 'Default'/'SecOps' to manage instance-family in compartment Sandbox
where target.resource.tag.operations.instance_type = 'non-critical'
```
📌 This allows management only for instances tagged as non-critical

---

## 5️⃣ Test the Policy

### ✅ Try to Terminate `Prod-Web-VM`
- **Tag:** `critical`
- **Result:** ❌ *Permission Denied* (as expected)

### ✅ Try to Terminate Non-Critical VM
- **Tag:** `non-critical`
- **Result:** ✅ *Success*

---

## ✅ Conclusion

This demo shows how **tag-based access control** in **OCI** can:

- 🔒 Protect critical resources from unintended actions  
- 🛡️ Enforce granular IAM policies  
- ⚙️ Ensure availability and reliability of key infrastructure  

