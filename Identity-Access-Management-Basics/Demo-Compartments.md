# 📦 OCI Compartments Demo

We’ve seen in the theory lesson that a **compartment** holds all our **cloud resources**. In this demo, we will:

- Explore the process of **creating compartments**
- Learn how to **assign resources** to them
- Discover how to **filter and explore resources** within compartments

---

## 🧭 Navigating to Compartments

Now, as you can see, I am on the **OCI Console**.

To manage compartments:

1. Navigate to **Main Menu**
2. Select **Identity & Security**
3. Click on **Compartments**

Here, you can view all available compartments in your tenancy.

---

## 🌳 Understanding the Root Compartment

Clicking on the first compartment shows us the **Root Compartment**:

- Automatically created when the tenancy is set up
- The **highest-level** compartment
- Contains all **child compartments**

While it's possible to have all resources in the root compartment, it’s best to create **dedicated child compartments** for better resource management.

### 📌 Example:
- **Production** compartment for the production team
- **Development** compartment for the development team

---

## 🏗️ Creating a New Compartment

To create a new compartment:

1. Click **Create Compartment**
2. Enter:
   - **Name**: `sandbox-demo`
   - **Description**: Short description of the compartment

3. (Optional) Enable **Security Zone** for secure operations validation
4. Select the **Parent Compartment**:
   - Selecting **Production** will make it a child of Production
   - Selecting **Root** will place it under Root

> For this demo, we will select **Root Compartment** and click **Create Compartment**

After refreshing the page, the new compartment appears. You can now create a **hierarchy of compartments** — up to **6 levels deep**.

---

## 🚀 Assigning Resources to a Compartment

Let’s create a **VCN** and assign it to our new compartment:

1. Go to **Networking > Virtual Cloud Networks**
2. Click **Create VCN**
3. Enter:
   - **Name**: `demo-01`
   - Select **Compartment**: `sandbox-demo`

This ensures proper **one-to-one resource mapping** — a resource belongs to **only one compartment**, but a compartment can hold **multiple resources**.

4. Keep default settings and click **Create**

Now, our **VCN is created** inside the `sandbox-demo` compartment.

---

## 🔍 Viewing Resources by Compartment

You can **filter resources** by compartment:

- Use the **Scope Filter** to view VCNs or other resources by compartment

To **explore all resources** in a compartment:

1. Go to **Main Menu > Governance and Administration**
2. Click on **Tenancy Explorer** under **Tenancy Management**
3. Select your compartment (e.g., `sandbox-demo`) to view all its resources

You can also:

- Select **Root Compartment** to view its resources
- Enable **"Show resources in subcompartments"** to see child compartment resources (e.g., Production, Sandbox)

---

## ✅ Summary

In this demo, we covered:

- ✅ How to **create compartments**
- ✅ How to **assign resources** (like VCN) to compartments
- ✅ How to **view and filter resources** using Tenancy Explorer

> Compartments help in logically organizing resources, enforcing access control, and improving manageability in Oracle Cloud Infrastructure.
