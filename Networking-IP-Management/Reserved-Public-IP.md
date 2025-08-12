# 📘 Reserved Public IP Addresses

## 🔹 Key Characteristics

- **Persistent**:  
  Exists **beyond the lifetime** of the instance.  
  Terminating the instance does **not** remove the IP.
  
- **Creation**:
  - Created **one at a time**.
  - After creation, can be **assigned** to a private IP.
  - **Regional limit**: Up to **50 reserved public IPs** per region.

- **Unassignment**:
  - Can be unassigned at any time.
  - Unassigned IP returns to the **tenancy’s pool** of reserved IPs.
  - **Never** automatically deleted — persists until **manually deleted**.

- **Scope**:
  - **Regional** — can be assigned to a private IP in **any availability domain** within the region.

---

## 🔹 Behavior with VNICs

- Each **VNIC** can have:
  - 1 Primary Private IP
  - Up to 32 Secondary Private IPs
- If a private IP (with a reserved public IP) is **moved** between VNICs (e.g., from `VNIC 1` to `VNIC 2`):
  - The **reserved public IP** moves **along with** the private IP.

---

## 🔹 Creation Steps (OCI Console)

1. Provide a **name**.
2. Select the **compartment**.
3. Choose the **IP address source** (e.g., *Oracle*).

---

## 🔹 Advantages

- **Persistence**: Not ephemeral — survives instance termination.
- **Flexibility**:  
  - Can be unassigned/reassigned to **any resource** when needed.
  - Works with both **primary** and **secondary** private IPs.
- **Security**:  
  - Allows controlled assignment, reducing unnecessary exposure.
- **Cost**: Free, even when unassociated.

---

✅ **Summary**:  
Reserved public IP addresses are persistent, region-scoped, flexible, and remain until you delete them manually. They are ideal for scenarios where you need a stable, reusable public IP that can survive instance changes.
