# 📘 Lesson: Dynamic Groups in OCI


## 🔁 Quick Recap: Key IAM Terms

- **Principal**: Identity of the caller accessing a resource.
- **User**: A human identity with access to OCI.
- **Instance**: A virtual machine or compute host in OCI.
- **Service**: OCI-managed application (e.g., Compute, IAM).
- **Resource**: An OCI entity such as a database, bucket, or load balancer.

---

## 🧱 Resource Principal Types

### 1. Infrastructure Principal
- **Analogy**: Birth Certificate 🧾 — confirms identity at creation.
- **Purpose**: Instance acts as a principal.
- **Example**: A VM calling Object Storage to upload data.

### 2. Stacked Principal
- **Analogy**: Passport 📘 — builds on existing identity for further access.
- **Purpose**: Service controlling a resource with the authority to act.
- **Example**: A Database taking backups to Object Storage.

### 3. Ephemeral Principal
- **Analogy**: Temporary Badge 🪪 — short-lived access credentials.
- **Purpose**: Temporary, injected identity.
- **Example**: OCI Functions calling another service (like Vault) during runtime.

---

## 🧠 What is a Dynamic Group?

A **Dynamic Group** allows you to group **resource principals** (like instances or functions) in a way similar to how you group users.

- **Purpose**: Grant access policies to non-human actors.
- **Examples**:
  - Instance calling Object Storage
  - Database writing backups to Vault
  - Functions invoking other services

---

## 🔄 Why "Dynamic"?

Membership is defined using **matching rules** — not static additions. This means:

- No manual updates
- Membership updates automatically as resources are created or deleted

---

## 🧪 Matching Rule Examples

- **By Compartment**:
  ```plaintext
  ALL {instance.compartment.id = 'ocid1.compartment.oc1..xyz'}
  ```

- **By Specific Instance**:
  ```plaintext
  ALL {instance.id = 'ocid1.instance.oc1..abc'}
  ```

- **By Resource Type**:
  ```plaintext
  ALL {resource.type = 'dbaas' AND resource.compartment.id = 'ocid1.compartment.oc1..xyz'}
  ```

- **For Functions or Certificates**:
  ```plaintext
  ALL {resource.type = 'fnfunc' AND resource.compartment.id = 'ocid1.compartment.oc1..xyz'}
  ```

---

## 🔐 Writing Policies for Dynamic Groups

### ✅ Example 1: Object Storage Access
```plaintext
Allow dynamic-group <domain>/<dynamic-group-name> to manage buckets in tenancy
Where target.bucket.name='example-bucket' and request.region='us-ashburn-1'
```

### ✅ Example 2: Database Backups
```plaintext
Allow dynamic-group DatabaseBackUp to manage objects in tenancy
```

---

## 📌 Dynamic Group Workflow
1. Create a Dynamic Group
2. Define a Matching Rule (compartment, resource type, etc.)
3. Write a Policy to give access
4. 🔒 No access will be granted until a policy is written

---

## ✅ Summary
- Dynamic Groups allow resource principals (instances, databases, functions) to act on services.
- Membership is automated via matching rules.
- You must write policies to enable access.
- Supports fine-grained access control in OCI.
