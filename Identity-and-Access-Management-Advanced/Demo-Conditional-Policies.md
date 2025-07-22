# 🧪 Conditional Policies Demo – OCI

## 🎯 Use Case

Allow members of the **NetworkAdmin** group to manage **Virtual Cloud Networks (VCNs)** in the entire tenancy, *except* in the **Production** compartment.

---

## 👣 Steps Performed

### 1. Login as Tenancy Admin
- Go to **Identity & Security > Policies**.
- Attach the policy at the **root compartment** (applies tenancy-wide).

### 2. Create Policy
- **Name**: `Demo-Condition`
- **Manual Policy Statement**:
  ```hcl
  allow group 'Production'/'NetworkAdmin' to manage virtual-network-family in tenancy 
  where target.compartment.id != 'ocid1.compartment.oc1..<Production_Compartment_OCID>'
  ```
- Copy the OCID of the Production compartment and replace in the policy above.

### 3. Verify Access as NetworkAdmin (User: John Rose)
- Root Compartment: Can create VCN ✅
- Production Compartment: Access denied ❌
> Error message: "Authorization failed"

---

## 🧠 Key Concepts
- Use `where` clause for fine-grained access control.
- `target.compartment.id` allows scoping based on specific compartment.
- Multiple conditions can be combined using:
  - `any {}` → logical OR
  - `all {}` → logical AND
- Always quote string values.
- Use wildcards when matching patterns (e.g., names, tags).

---

## 🪣 Bonus Example: Object Storage Conditions
To allow limited access to object storage:

### 🔐 Full access for admins:
```hcl
allow group Admins to manage object-family in tenancy
```

### ✍️ Limited access for writers:
```hcl
allow group ObjectWriter to inspect buckets in tenancy
where all {
  request.permission = 'OBJECT_CREATE'
  target.bucket.name = 'example-bucket'
}
```

> ✅ Only allows ObjectWriter group to create and inspect objects in specific buckets.

---

## ✅ Summary
- Conditional policies provide granular, compartment-level access control.
- Attach policies at the correct level (tenancy or compartment).
- Use conditions like target.compartment.id and target.bucket.name to restrict access.
- Combine conditions for fine-tuned security.
