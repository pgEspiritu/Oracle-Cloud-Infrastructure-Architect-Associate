# Advanced Policies in OCI: Enforcing Least Privilege


## 🔐 What Are Permissions?

Permissions are **atomic units of authorization** that control a user's ability to perform operations on resources. These permissions are managed using **verbs** like:

- `manage`
- `inspect`
- `use`
- `read`

These verbs simplify the process of granting multiple related permissions by grouping them into a broader access level.

---

## 🔧 How Policies Work

Policies are built using **two main elements**:

- A **verb** (e.g., `manage`)
- A **resource-type** (e.g., `volume`)

OCI then **automatically grants predefined permissions** in the background. You don’t need to manually assign each permission.

---

## 📘 Example: Volume Resource

Here’s what happens behind the scenes for the `volume` resource:

| Verb     | Permissions Added                   | API Access Included             |
|----------|-------------------------------------|----------------------------------|
| inspect  | `VOLUME_INSPECT`                   | `ListVolume`, `GetVolume`       |
| read     | `VOLUME_INSPECT` + others          | —                                |
| use      | `INSPECT`, `UPDATE`, `WRITE`       | —                                |
| manage   | All permissions incl. `CREATE`, `DELETE`, `MOVE` | Full control           |

> 🔍 **Note**: Permissions are always in **UPPERCASE** like `VOLUME_INSPECT`, `VOLUME_UPDATE`.

---

## 🎯 Enforcing Least Privilege with Advanced Policies

Let’s rewrite policies using advanced techniques.

### ❌ Policy A (Too Broad)
```text
Allow group DomainA/AuditDG to manage objects in compartment AcmeCorp
```
- Uses `manage` → grants all permissions
- ❗ Violates least privilege

### ✅ Rewrite: Restrict to Specific Bucket & Permission
```text
Allow group omainA/AuditDG to manage objects in compartment AcmeCorp 
where
all { target.bucket.name='audit_logs_bucket',
    request.permission='OBJECT_CREATE'
    }
```
- Restricts to:
  - Specific bucket
  - Specific permission (`OBJECT_CREATE` only)
 
---

### ✅ Example: Deny Delete Permission
Objective: Allow Group XYZ to list, create, update, write, and move block volumes — but not delete.
Method 1: Explicitly Define Allowed Permissions
```text
Allow group DomainA/XYZ to manage groups in tenancy where
any {
request.permission='VOLUME_INSPECT',
request.permission='VOLUME_CREATE',
request.permission='VOLUME_WRITE',
request.permission='VOLUME_UPDATE',
request.permission='VOLUME_MOVE'}
```

Method 2: Exclude a Permission
```text
Allow group DomainA/XYZ to manage groups in tenancy where
request.permission != 'VOLUME_DELETE'
```

Method 3: Use API Operation
```text
Allow group DomainA/XYZ to manage groups in tenancy where
any {
request.operation='ListVolumes',
request.operation='GetVolume',
request.operation='AttachVolume',
request.operation='CreateVolume',
request.operation='ChangeVolumeCompartment'}
```

---

### 🗂 Example: Upload/Inspect in Buckets Only
Objective: Group should only upload or inspect objects in any bucket.
```text
Allow group DomainA/ObjectWriters to manage objects in compartment ABC
where any {request.permission='OBJECT_CREATE', request.permission='OBJECT_INSPECT'}
```

Further restrict to a specific bucket:
```text
Allow group DomainA/ObjectWriters to manage objects in compartment ABC where
all {target.bucket.name ='BucketA',
    any {request.permission='OBJECT_CREATE',
        request.permission='OBJECT_INSPECT'
        }}
```

---

### 🕒 Time-Based Policy Example
Objective: Allow contractors to use instances only at specific times.
```text
Allow DomainA/Contractors to use instances in compartment contractors where
all { request.utctimestamp after '<TIME>',
    request.utc-timestamp before '<TIME>'
    }
```

---

## ✅ Summary
- Use verbs to simplify access control.
- Use permissions and conditions to go granular.
- Combine target.resource.name, request.permission, request.operation, and request.time for full control.
- Avoid broad manage access unless absolutely required.

---

## 💡 Admin Tip
Structure policies wisely to maintain clear and secure access control. Applying the least privilege principle helps protect your OCI resources while giving users exactly the access they need—no more, no less.
