# 🎓 Part 2: Optimizing OCI IAM Policies


## 🧩 Scenario: Launching a Compute Instance in Compartment A

Let’s say you want to **launch a compute instance** in `compartment A`.

- The **VCN** has already been created by an admin user.
- You’ve been added to **group X** as the operator.

To proceed, you’ll need a few permissions.

---

## 🔐 Step 1: Allow Subnet Attachment

To allow instances to attach to a subnet, we use this policy:

```text
Allow group X to use subnets in compartment A
```

This policy implies:
- `SUBNET_READ`
- `SUBNET_ATTACH`
- `SUBNET_DETACH`

---

## ⚙️ Step 2: Allow Instance Management

To manage instances, we use:

```text
Allow group X to manage instances in compartment A
```

This provides:
- `INSTANCE_CREATE`
- `INSTANCE_DELETE`
- Additional instance management permissions

---

## 🗂 Step 3: Read Application Catalog Listings

To access the application catalog:

```text
Allow group X to read app-catalog-listing in compartment A
```

This allows group X to view available resource listings in the compartment.

---

## 🔄 Optimization: Merge Policies
We notice group X has multiple permissions across separate policy statements.
🔧 Optimization: Merge all permissions into a single policy statement:

```text
Allow group X to { SUBNET_READ, SUBNET_ATTACH, SUBNET_DETACH,
                  INSTANCE_INSPECT, INSTANCE_READ, INSTANCE_UPDATE, INSTANCE_CREATE_IMAGEZ
                  INSTANCE_POWER_ACTIONS, INSTANCE_ATTACH_VOLUME, INSTANCE_DETACH_VOLUME } in compartment A
```
>  Policy statements is used insted of Verb to minimizes policy statements.

✅ Benefits:
- Simplifies management
- Keeps within IAM policy statement limits
- Easier to audit and govern

---

## 🔐 Enforce Least Privilege
Instead of using verbs like manage, which can be broad, define explicit permissions:
  - Only include permissions required for:
    - Launching compute instances
    - Attaching to subnets
    - Assigning to network security groups
This avoids over-permissioning and aligns with the principle of least privilege.

---

## 👥 Multiple Groups, Same Permissions
If multiple groups (e.g., `X` and `Y`) need the same permissions:
Use a single statement:

```text
Allow group X, Y to manage instances in compartment A
```

Or better, be explicit:

```text
Allow group X, Y to { SUBNET_READ, SUBNET_ATTACH, SUBNET_DETACH,
                  INSTANCE_INSPECT, INSTANCE_READ, INSTANCE_UPDATE, INSTANCE_CREATE_IMAGEZ
                  INSTANCE_POWER_ACTIONS, INSTANCE_ATTACH_VOLUME, INSTANCE_DETACH_VOLUME } in compartment A
```

---

## 🧠 Use Naming Patterns
Apply permissions dynamically using patterns:

```text
Allow group DevOps to manage all-resources in compartment ProjectX*
```
- Matches all compartments starting with `ProjectX`
- Combines policies for prod/dev into one using a naming convention

---

## ✅ Summary
In this lesson, we learned how to:
 - 🔗 Merge policy statements for clarity
 - 🔒 Enforce least privilege
 - 🧠 Use patterns for dynamic permissions

These optimizations:
- 🔄 Simplify IAM management
- 🧼 Reduce redundancy
- 🛡 Improve security posture
