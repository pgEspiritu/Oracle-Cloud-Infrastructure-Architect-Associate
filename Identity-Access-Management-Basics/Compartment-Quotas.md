# 📘 OCI Lesson: Compartment Quotas and Budgets

## 🎯 Objective
Understand how to control resource usage and spending within compartments using **Quota Policies** and **Budgets** in OCI.

---

## 🧠 Scenario
You want to:
- Limit total **bare metal machine instances** to **10** across all departments.
- Allow **only 4** of those instances to be used by the **Production** team.

---

## 📌 Compartment Quotas

OCI allows administrators to **limit resource consumption** using **quota policies**.

### 🛠️ Quota Policy Syntax
```text
set <service-family> quota <quota-name> to <value> in compartment <compartment-name>
```

---

# 🧾 Example: VCN Quota Policy

## ✅ Goal  
Allow only **4 Virtual Cloud Networks (VCNs)** in the `production` compartment.

## 🔤 Policy  
```text
set vcn quota vcn-count to 4 in compartment production
```

## 🔍 Breakdown

- `set` → defines the quota  
- `virtual-network` → service family  
- `VCN-count` → quota name  
- `4` → max allowed  
- `production` → target compartment  

👉 Refer to [OCI documentation](https://docs.oracle.com/en-us/iaas/Content/Quotas/Concepts/quota_policy_syntax.htm) for valid service families and quota names.

---

## 🧾 More Examples

### 🚫 Allocate only one Exadata resources in the entire tenancy
```text
set database quota /*exadata*/ to 1 in tenancy
```

## 📉 Limit Compute Cores for Specific VM Shapes

```bash
set compute-core quota standard2-core-count to 10 in tenancy
```

## 🔁 Quota Action Keywords

| Action | Description                                  |
|--------|----------------------------------------------|
| `set`  | Define quota for a resource                  |
| `unset`| Reset quota back to OCI default limits       |
| `zero` | Remove access to a resource (quota = 0)      |

---

## 🧪 Example Using `zero` and `unset`

```bash
# Deny Exadata for all
zero exadata quota * in tenancy

# Allow Exadata only in production
unset exadata quota * in compartment production
```

---

## 💰 Compartment Budgets

Control cost by setting **monthly budgets** on compartments.

### Example:

- **Budget**: $2,000/month for the `production` compartment  
- **Threshold Alerts**: 80%, 90%, 100%

🔔 OCI sends notifications when thresholds are reached.

---

## ✅ Summary

- OCI policies use a **readable syntax** to manage who can access what and where.
- **Quotas** help enforce resource limits across your tenancy.

### Use:
- `set` to **define quotas**
- `unset` to **revert** to OCI default limits
- `zero` to **deny all access**
- **Budgets** let you **monitor and control** cloud spending.

