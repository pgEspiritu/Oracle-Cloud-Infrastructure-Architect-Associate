# 📘 OCI Compartments Explained

## 🔰 What Is a Compartment?

When you create or access an OCI account, you get a **tenancy**, also known as the **root compartment**.

📁 Think of the root compartment as the **main folder** on your computer. Just like creating **subfolders** to organize files, you can create **sub-compartments** within OCI to organize cloud resources.

Examples:
- A `Network` compartment for networking-related resources like VCNs and load balancers
- A `Storage` compartment for block storage and file storage

You can also organize compartments by:
- Project
- Team
- Region
- Environment (e.g., `production`, `development`)

> ⚠️ Although you can place all resources in the root compartment, **best practice** is to create dedicated compartments to isolate and manage resources.

---

## 🧠 Features of Compartments

### 1. ✅ **One Resource, One Compartment**

Every resource in OCI belongs to **one and only one compartment** at a time.

📝 Example: A virtual machine placed in `Compartment A` cannot also be in `Compartment B`.

---

### 2. 🔐 **Access Control via Policies**

Access is defined using **policy statements**.

- Users are added to **groups**
- Policies allow a **group** to perform actions (`verbs`) on a **resource type** in a **compartment**

📝 Example:

```plaintext
Allow group DevTeam to manage block-storage in compartment Development
```

This allows only the DevTeam group to manage block storage resources within the Development compartment.

---

## 🔄 3. Cross-Compartment Resource Interaction

Resources can interact even if they are in **different compartments**.

📝 **Example:**  
A VM in **Compartment A** can be connected to a **VCN** in **Compartment B**.

---

## 🔁 4. Moving Resources Between Compartments

OCI supports **moving resources** between compartments.

📝 **Example:**  
Move a VM from **Compartment A** to **Compartment B** when project ownership changes.

---

## 🌐 5. Compartments Are Global

Compartments are **not tied to a specific region**.

You can place resources from **multiple regions** into the **same compartment**.

📝 **Example:**  
Create a compartment `Compartment A` in **Phoenix**. You can also place an instance in **Lisbon** into `Compartment A`.

---

## 🧱 6. Nested Compartments (Up to 6 Levels)

OCI allows you to create **nested compartments** for deeper logical organization.

📁 **Example:**

ProjectX
├── TeamA
│ └── Frontend
├── TeamB
│ └── Backend


You can assign **granular policies** to each nested level.

---

## 📝 Summary

- **Compartments** are logical containers for organizing OCI resources.
- They help implement **access control** and **resource isolation**.
- Features include:
  - ✅ Cross-region support
  - 🔁 Resource movement
  - 🧱 Nested hierarchy (up to 6 levels)

Use compartments **strategically** to mirror your organization’s structure and access requirements.

---

## ✅ Policy Recap

### Example Policy

```plaintext
Allow group NetworkAdmin of domain production to manage virtual-network-family in compartment production
```

This allows the NetworkAdmin group in the production domain to manage networking resources within the production compartment.
