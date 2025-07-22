# 🛡️ OCI Demo: Policy Inheritance and Policy Attachment

In this demo, we will explore how to set up policies in a tenancy and understand how they work across compartments.

---

## 🧭 Environment Setup

Logged in as: **Tenancy Admin**

**Compartment Hierarchy:**
- Root Compartment (`<tenancy-name>`)
  - Compartment A
    - Compartment B
      - Compartment C

---

## 🎯 Objective

Create and test policies for a group `production/network admin` to:
- Manage **Virtual Cloud Networks (VCNs)** in **Compartment C**
- Manage **Policies** in **Compartment C**

---

## 📝 Step 1: Create Policy in Compartment C

Navigate to:  
**Console → Identity & Security → Policies → Create Policy**

### Policy Name:
`Test-C`

### Compartment:
`Compartment C`

### Policy Statements:
```text
Allow group production/network admin to manage virtual-network-family in compartment C
Allow group production/network admin to manage policies in compartment C
```

✅ Click **Create**.

---

## 🔍 Step 2: Test Policy as User (John Rose)

John Rose is a member of `production/network admin`.

### Test VCN Access:
Navigate to **Networking → VCNs**

- Try in **Root Compartment**: ❌ *No access*
- Try in **Compartment C**: ✅ *VCN creation successful*

### Test Policy Access:
Navigate to **Identity → Policies → Compartment C**

- ✅ Edit policy (change "manage" to "use")
- ✅ Save changes

---

## 🧹 Step 3: Delete Policy in Compartment C (Admin)

Back as **Tenancy Admin**:

- Go to **Compartment C → Policies**
- ❌ Delete the `Test-C` policy

---

## 🏗️ Step 4: Create Policy in Compartment A for C

### Attempt 1:
Try reusing same policy text in **Compartment A**:

```text
Allow group production/network admin to manage virtual-network-family in compartment C
```

❌ Error: Compartment C not in visible subtree

###Fix:
```text
Allow group production/network admin to manage virtual-network-family in compartment B:C
Allow group production/network admin to manage policies in compartment B:C
```

✅ Click Create Policy

---

# 🔁 Step 5: Verify Access Again as John Rose

## 🔄 Refresh Page in Compartment C

- ❌ **No policy shown** (since attached in A)
- ❌ **No access to edit/view policy** (no permission granted in A)

---

## ✅ Summary

- ✅ **Policies must be attached appropriately** based on compartment visibility
- ✅ **Use full path** (e.g., `B:C`) if scoping access from higher compartments
- ✅ **Only users/groups with explicit access** to compartments where policies are attached can manage/view them

> 💡 **Admin Tip:**  
Structure policies wisely to maintain clear and secure access control.
