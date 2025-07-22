# 🛡️ Policy Attachment and Policy Inheritance in OCI

## 🌳 Policy Inheritance

- Compartments inherit policies from their **parent compartments**.
- Example:
  - A **standard admin policy** in the **root compartment** gives access to all compartments.
  - The **admin group** (without a domain prefix) in the default domain has permission to manage resources tenancy-wide.
- **Hierarchy Example**:

Root
└── A
└── B
└── C

- If a policy is attached to **Compartment A**:
  ```text
  Allow group Domain1/NetworkAdmin to manage virtual-network-family in compartment A
  ```
  - Then access is **inherited** by **B** and **C**.

---

## 📎 Policy Attachment

- Policies must be **attached to a compartment** (root or otherwise).
- **Attachment Location Determines Who Can Modify/Delete** the policy:
- Policy in **root**: Only users with tenancy-level permission can manage it.
- Policy in **Compartment C**: Only users with permission in **C** can manage it.
- Policies in **parent compartments** (A or B) can still govern **child compartments** due to inheritance.

### ✅ Example:
- To allow `Domain1/NetworkAdmin` to manage VCNs in **Compartment C**, policy **can be attached to**:
- Compartment C:
  ```text
  Allow group Domain1/NetworkAdmin to manage virtual-network-family in compartment C
  ```
- Compartment B:
  ```text
  Allow group Domain1/NetworkAdmin to manage virtual-network-family in compartment C
  ```
- Compartment A:
  ```text
  Allow group Domain1/NetworkAdmin to manage virtual-network-family in compartment B:C
  ```
- Root:
  ```text
  Allow group Domain1/NetworkAdmin to manage virtual-network-family in compartment A:B:C
  ```

> 🔑 When attaching to higher-level compartments, you must provide the **full path** to the target compartment.

---

## 📌 Key Points

- **Inheritance** flows **downward**, from parent to child compartments.
- **Attachment location** controls **who can manage the policy**.
- Best Practice:
- **Attach policies** in the compartment they relate to.
- Assign **policy admins** thoughtfully based on project scope.
- **Restrict policy creation rights** to reduce unintended access.

---

## ✅ Summary

- **Policy Inheritance**: Permissions flow down from parent to child compartments.
- **Policy Attachment**: Determines who can edit or delete the policy.
- Full path references (`A:B:C`) are needed when defining access from higher levels.
- Keep policies organized and secure by attaching them at appropriate levels.

🧠 **Tip**: Carefully plan your compartment structure and policy hierarchy for secure and maintainable access control.
