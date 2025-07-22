# 🏷️ Tag-Based Access Control in OCI

Using **OCI tagging**, you can simplify and scale access control across your tenancy by avoiding repetitive policy definitions for each compartment or group.

---

## 📌 What Is Tag-Based Access Control?

Tag-based access control enables you to write policies based on **tags** instead of explicitly listing compartments, groups, or resources.

This approach:
- Reduces repetitive policy writing
- Scales easily across environments
- Allows dynamic access control via tagging/un-tagging

---

## 🧾 What Are Tags in OCI?

OCI tags are metadata in **key-value pairs** applied to resources.

Examples:
```text
Operations.Environment="Production" 
Operations.Project="Alpha"  
HumanResources.Environment="Production"
HumanResources.CostCenter="42"
HumanResources.Project="Beta"
```
You can use these tags in policy statements to control access.

---

## ✅ Benefits of Tag-Based Policies
- Scope access across multiple resources, groups, compartments
- Add/revoke access without changing policies
- Support dynamic authorization using tag values

---

## 🔧 How Does It Work?
In tag-based access control, you:
1. Apply tags to requester or target.
2. Use variables like:
  - `request.principal.group.tag`
  - `request.principal.compartment.tag`
  - `target.resource.tag`
  - `target.resource.compartment.tag`

---

## 🔹 Tagging the Requester
Tag the group, dynamic group, or requesting compartment.

### 📌 Example 1: Group-Based Access
```text
Allow any-user to manage instance-family in compartment HR 
where request.principal.group.tag.operations.project = 'Prod'
```
✅ Any group tagged with` operations.project = Prod` gets access.

### 📌 Example 2: Dynamic Group Access
```text
Allow dynamic-group DevInstances to manage object-family in tenancy 
where request.principal.compartment.tag.operations.phase = 'Prod'
```

---

## 🔹 Tagging the Target Resource
Apply tags to the target resource or its compartment.

### 📌 Example 3: Target Resource Tagged
```text
Allow group DomainA/GroupA to manage all-resources in compartment HR 
where target.resource.tag.operations.project = 'Prod'
```

### 📌 Example 4: Target Compartment Tagged
```text
Allow group DomainA/GroupA to manage all-resources in tenancy 
where target.resource.compartment.tag.operations.project = 'Prod'
```

---

## 🧪 Real-Life Examples

### 📦 Example 1: Admin Access to Shared Compartment
You have:
- Compartments: ProjectA, ProjectB, ProjectC
- Admin groups: A-Admin, B-Admin, C-Admin
- All tagged with: `employeeGroup.role = Admin`

🟡 Problem: Give all admins access to a new Test compartment without creating a new group.
🟢 Solution:
```text
Allow any-user to manage all-resources in compartment Test 
where request.principal.group.tag.employeeGroup.role = 'Admin'
```
✅ Any group with this tag automatically gets access.
❌ No need to modify policy when adding/removing admins.

### 🧪 Example 2: Test Engineers Access to Test Compartments
Structure:
- ProjectA, ProjectB, ProjectC each contain: `test`, `prod` compartments
- `test` compartments tagged with: `ResourceGroup.role = Test`
  
🟢 Policy:
```text
Allow group DomainA/Testers to use all-resources in tenancy 
where target.resource.compartment.tag.ResourceGroup.role = 'Test'
```
✅ Testers get access across all tagged test compartments.
🔄 Revoke access by changing/removing tag — no policy update needed.

---

## ⚠️ Important Notes
- ✅ All services support:
  - `request.principal.compartment`
  - `request.principal.group`
  - `target.resource.compartment.tag`

- ⚠️ Not all services support:
  - target.resource.tag

🔗 Refer to [OCI official docs](https://docs.oracle.com/en-us/iaas/Content/home.htm) for latest service support.

---

## ✅ Summary

| Feature               | Benefit                                       |
|-----------------------|-----------------------------------------------|
| 🔄 Dynamic Control     | Grant/revoke access without editing policies  |
| 🔖 Simplified Management | Tag once, apply to many                       |
| 🔐 Least Privilege      | Limit access based on tag scope               |

Tag-based access control gives you **powerful**, **scalable**, and **flexible** policy writing capabilities in **OCI**.
