# 📘 Lesson: Understanding Policies in OCI IAM

## 🔐 What Is Authorization in OCI?

**Authorization** controls what actions a particular user can perform in OCI. This is implemented via **policies**, which define **who can do what in which scope**.

By default, **everything is denied**. You must explicitly allow access through policies. OCI follows the **principle of least privilege**, ensuring users only get the access they truly need.

---

## 📜 OCI Policy Syntax

The general structure of an OCI policy is:

```text
Allow <subject> to <verb> <resource-type> in <location> [where <condition>]
```


### 🧩 Policy Components:

1. **Subject** – Who is allowed? (e.g., user, group, dynamic group)
2. **Action** – What action is allowed? (verb + resource type)
3. **Placement** – Where is the action allowed? (tenancy or compartment)
4. **Condition** *(optional)* – Extra filter criteria

---

## 👥 Subject Clause

Subjects are typically defined as:

- `group <domain-name>/<group-name>`
- `dynamic-group <domain-name>/<dynamic-group-name>`
- `any-user` – All users in the tenancy

### 📌 Examples:

```hcl
Allow group production/NetworkAdmin to manage virtual-network-family in compartment sandbox
Allow dynamic-group production/ComputeGroup to use object-family in tenancy
```

## 💡 Tip
If you omit the domain name, the **default domain** is implied.  
> ✅ **Best Practice**: Always prefix domain names for clarity.

---

## 👥 Chaining Multiple Groups in One Policy

```hcl
Allow group production/A-Admin, production/B-Admin to read all-resources in compartment dev
```

---

## ⚙️ Action Clause

### 🔑 Verbs (Access Levels)

| Verb    | Description                          |
|---------|--------------------------------------|
| inspect | View metadata only                   |
| read    | View data                            |
| use     | Read & modify existing resources     |
| manage  | Full control (create, update, delete)|

> These verbs map to multiple API operations behind the scenes.

---

### 🔧 Resource Types

- **all-resources** – Grants access to every resource in OCI
- **Aggregate Resource Types** – e.g., `virtual-network-family`, `database-family`
- **Individual Resource Types** – e.g., `vcn`, `subnet`, `db-system`

---

### 📌 Verb + Resource Examples

| Policy Statement     | Description              |
|----------------------|--------------------------|
| inspect object       | View object metadata     |
| read object          | Download object contents |
| use object           | Perform actions like re-encrypt |
| manage object        | Full control (create/delete) |

---

## 🎯 Example Policy

```hcl
Allow group production/NetworkAdmin to manage virtual-network-family in compartment sandbox
```

---

## 🧭 Placement (Scope)

You can define the scope of access using:

- `in tenancy` – Applies to the entire tenancy
- `in compartment <name>` – Named compartment
- `in compartment id <ocid>` – Specific compartment using OCID

### 📌 Example

```hcl
Allow group production/NetworkAdmin to manage virtual-network-family in compartment sandbox
Allow group default/SecurityAdmin to read audit-events in compartment id ocid1.compartment...
```

---

## 📚 Using OCI Documentation

Refer to the **OCI Policy Reference Documentation** to:

- Discover aggregate and individual resource types  
- Understand permissions for each service  
- See real-world policy examples  

---

## ⚠️ Special Case: Identity Resources

Unlike other services, **Identity resources do not have aggregate resource types**.  
You must use individual types like:

- `manage users`
- `manage groups`
- `manage policies`
- `manage compartments`

---

## ✅ Summary

OCI policies use a **plain English-like syntax** to define access.

A policy consists of:

- **Subject** (who)  
- **Verb + Resource** (what)  
- **Location** (where)  
- *(Optional)* **Condition**

**Verbs:**

`inspect`, `read`, `use`, `manage`

**Resource Types:**

`all-resources`, aggregate, or individual

✅ Always use **domain-prefixed group names** for clarity.  
📖 Use the **OCI documentation** to verify resource names and permissions.
