# 🛡️ Conditional Policies in OCI

Welcome to the lesson on **Conditional Policies**, where we will discuss what conditional policies look like and how to use them in Oracle Cloud Infrastructure (OCI).

---

## 📜 What Are Conditional Policies?

In earlier lessons, we learned how to write basic policies using the structure:

```text
Allow <Subject> to <Verb> in <Placement>
```

To create **advanced, fine-grained policies**, we use the `where` keyword to include **conditions**. These conditions are evaluated as:

- ✅ **True**
- ❌ **False**
- ⚪ **Not Applicable**

---

## ❓ Why Use Conditions?

Conditions enable more **complex access control**. You can limit access based on attributes of the request or the target resource. 

---

## 🧩 Syntax of Conditional Policies

Use **variables** to add conditions:

- `request.<attribute>` — Attributes about the request itself.
- `target.<attribute>` — Attributes of the resource being accessed.

### 🔐 Example 1: Specific User Access
```text
request.user.id = 'ocid1.user.oc1..exampleuniqueID'
```

## 📦 Example 2: Specific Permissions

```text
request.permission = 'OBJECT_INSPECT'
```
> ➡️ Limits access even if the action is broadly defined (e.g., `manage`).

## 🪣 Example 3:  Specific Bucket

```text
target.bucket.name = 'my-secure-bucket'
```
> ➡️ Applies policy only to the specified bucket.

---

# 🧠 Types of Conditions

## 🔹 Single Condition
```text
request.region = 'phx'
```

- Evaluates to `True` or `False`.
- Uses equality (`=`) or inequality (`!=`) operators.

# 🔸 Multiple Conditions
Use:

- `any {}` → Logical OR
- `all {}` → Logical AND

### ✅ Example using `any`:
  ```text
  any {
    request.permission = 'OBJECT_CREATE'
    request.permission = 'OBJECT_INSPECT'
  }
  ```
  > ➡️ If either permission is present, access is granted.

### ✅ Example using `all`:
  ```text
  all {
    request.region = 'phx'
    request.user.id = 'ocid1.user.oc1..xyz'
  }
  ```
  > ➡️ Both conditions must be met.

---

## 🔠 Value Types
- String values must be enclosed in single quotes:
```text
'user@example.com'
```

Pattern Matching:
Use wildcards to match string patterns.
```text
target.bucket.name = 'HR*'
```
> ➡️ Matches any bucket name starting with "HR".

---

#💡 Real-World Examples
## 🌎 Region-Based Access
```text
Allow group DomainA/PHX-Admins to manage all-resources in tenancy
where request.region = 'PHX'
```
> ➡️ Members can only operate in the Phoenix region.

---

## 📂 Compartment Restriction
```text
Allow group NetworkAdmins to manage virtual-network-family in tenancy
where target.compartment.id != 'ocid1.compartment.oc1..excludedCompartmentID'
```

> Group can manage VCNs in all compartments except the excluded one.

## 🗄️ Autonomous Database Workload Access
```text
Allow group ADBAdmins to manage autonomous-database in tenancy
where any {
  target.workloadType = 'OLTP'
  target.workloadType = 'DW'
  target.workloadType = 'AJD'
}
```
> ➡️ Limits access to specific workload types: OLTP, Data Warehouse, or JSON.

---

# ✅ Summary
- Use `where` clause for fine-grained access.
- Understand the difference between `request` and `target`.
- Use `any {}` and `all {}` for combining conditions.
- Always quote strings and use wildcards wisely.
