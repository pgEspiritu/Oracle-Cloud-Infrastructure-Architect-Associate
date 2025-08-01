# 🛣️ Working with Route Tables in Oracle Cloud Infrastructure (OCI)

In this demonstration, we'll explore:

- How to view existing route tables
- How to create a new route table
- How to add a route rule
- How to associate a route table with a subnet

---

## 🔍 Viewing Existing Route Tables

Navigate to the **OCI Console** and access the **Virtual Cloud Networks (VCNs)**. You'll see two VCNs created from earlier demonstrations.

1. Click on a VCN created using the **wizard**.
2. Under **Resources**, select **Route Tables**.
3. You will typically see:
   - A default route table
   - A private subnet route table

Each route table displays the number of associated route rules.

### Demo VCN (Manual Creation)

- Only **one default route table** is present.
- **State**: Available
- **Number of Rules**: 0 (no visible rules)
- 🔸Note: There is an **implicit local route** not visible in the console. It allows internal communication between subnets.

---

## ➕ Adding a Route Rule

Before adding a route rule, we need a gateway.

### Step 1: Create a Private Subnet

- Keep all defaults
- Provide the CIDR block
- Click **Create Subnet**

### Step 2: Create a NAT Gateway

- Give it a name
- Keep defaults
- Click **Create NAT Gateway**

### Step 3: Add Route Rule to Existing Route Table

1. Go to the **default route table**
2. Click **Add Route Rules**
3. Select **Target Type**: `NAT Gateway`
4. Set **Destination CIDR Block**: `0.0.0.0/0`
5. Select the NAT Gateway from the list
6. Click **Add Route Rules**

✅ Successfully added a route rule to the default route table.

---

## 🆕 Creating a Custom Route Table

1. Click **Create Route Table**
2. Provide a name (e.g., `Custom Route Table`)
3. Adding a rule is optional — click **Create**

🔸Note: Custom route tables also have **implicit local routing**.

### Add a Rule to the Custom Route Table

1. Select the custom route table
2. Click **Add Route Rules**
3. Example:
   - **Target Type**: `Internet Gateway`
   - **Destination**: Appropriate CIDR (e.g., `0.0.0.0/0`)
   - **Target Gateway**: Select from available internet gateways
   - Click **Add Route Rules**

---

## 🔁 Associating Route Table with a Subnet

By default, subnets are attached to the default route table.

### Change Route Table Association

1. Go to the subnet (e.g., `privatesubnet`)
2. Click **Edit**
3. Select the new route table (e.g., `Custom Route Table`)
4. Click **Save Changes**

✅ Route table association updates successfully.

---

## ✅ Summary

- You explored existing route tables
- You created and modified route tables
- You added route rules to send traffic through gateways
- You learned how to associate subnets with route tables

📌 Remember: All route tables (default or custom) have **implicit local routes** for intra-VCN communication.
