# 🧪 OCI Compartment Quotas and Budgets Demo

Let’s first understand the difference between **service limits** and **compartment quotas**.

---

## 📌 Service Limits vs. Compartment Quotas

| Feature             | Service Limits                        | Compartment Quotas                                  |
|---------------------|----------------------------------------|------------------------------------------------------|
| Defined by          | Oracle                                 | OCI Administrator                                    |
| Purpose             | Predefined maximum for each service    | Custom limits per compartment to control usage       |
| Location to view    | OCI Console → Tenancy Management → Limits, Quotas, and Usage | OCI Console → Identity → Quota Policies  |

To **view service limits for your tenancy**:

1. Go to the **OCI Console**.
2. Navigate to **Tenancy Management > Limits, Quotas, and Usage**.
3. Choose the desired service (e.g., **Virtual Cloud Network**).
4. Select the **region** to see region-specific limits.
   - Example: In your home region, the limit for number of VCNs may be `300`.

> ⚠️ Limits can vary across regions.

---

## 🔒 Setting Quotas in a Compartment

To restrict or allow specific resource usage in compartments, you can set **quota policies** using simple syntax.

### Example: Limit VCN creation to 1 in `security-sandbox` compartment

#### Step-by-Step:

1. Go to **Identity → Quota Policies**.
2. Click **Create Quota Policy**.
3. Provide a **Name**: `quota-policy-security-sandbox`
4. Add a **Description**.
5. Add **Policy Statements**:
    ```text
    zero virtual-network-family quotas in compartment security-sandbox
    set virtual-cloud-networks quota 1 in compartment security-sandbox
    ```
6. Click **Create Quota Policy**.

#### Why use `zero` first?

It’s a best practice to **deny all** (`zero`) access to a resource first, then **explicitly allow** what’s needed.

---

## ✅ Verifying the Quota Policy

1. Navigate to **Networking → Virtual Cloud Networks**.
2. Select the **security-sandbox** compartment.
3. Try to **create a VCN** named `test-01`. It will succeed.
4. Try to create **another VCN** named `test-02`.
    - ⚠️ You will receive an error: **Quota limit exceeded**.

---

## 💰 Setting Budgets

To **track spending and get alerts**, set up **Budgets**.

### Steps:

1. Go to **Billing and Cost Management → Budgets**.
2. Click **Create Budget**.
3. Provide:
    - **Name**: `security-sandbox-budget`
    - **Description**
    - **Target Compartment**: `security-sandbox`
    - **Amount**: `$100`

4. Add **Alert Rules**:
    - Threshold: `80%` → Alert at `$80` usage
    - Configure:
        - **Email notifications**
        - Or integrate with **Event Rules** and **Notifications Service**

---

## 🧾 Summary

- **Service Limits** are set by Oracle and apply tenancy-wide.
- **Quotas** allow administrators to:
    - Use `set` to define limits
    - Use `unset` to revert
    - Use `zero` to block access
- **Budgets** let you:
    - Monitor spending
    - Trigger alerts at specified thresholds

---

Thanks for your time!  
This demo showed how to use **compartment quotas** to control resource usage and **budgets** to monitor OCI spending.
