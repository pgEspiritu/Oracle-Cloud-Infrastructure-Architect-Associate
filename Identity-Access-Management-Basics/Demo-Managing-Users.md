# OCI IAM Demo: Creating Users

Welcome back. In this demo on **creating users in OCI IAM**, we will continue with our previous use case where we have two domains: `production` and `development` within our tenancy. In the `production` domain, we created two groups: **NetworkAdmin** and **VaultAdmin**.

Now, in this demo, we will:

- Create **three users**:
  - **One** using the Console and add them to the **NetworkAdmin** group.
  - **Two** using the **CSV import** option:
    - One added to **NetworkAdmin** group.
    - The other added to **VaultAdmin** group.

---

## Step 1: Creating a User via Console

1. Log in as **Production Domain Admin** (with permission to access resources within the `production` domain only).
2. Navigate to:

```text
Main Menu > Identity & Security > Identity > Domains
```


3. Select your **Production** domain and go to **Users**.
4. Click **Create User**, then fill in:
- Name: `Saurabh Patil`
- Username: `SPatil`
- Email Address: _(required based on domain settings)_
- Assign the user to the **NetworkAdmin** group
5. Click **Create**.

✅ **User created successfully!**

---

## Step 2: Activating the User Account

- Check the mailbox for the activation link.
- Click **Activate Account**.
- Set the password and click **Reset**.
- Log in via: [https://cloud.oracle.com](https://cloud.oracle.com)

### Logging in as the New User

1. Enter:
- **Tenancy Name**
- **Domain**: `Production`
- **Username**: `SPatil`
- **Password**
2. Click **Sign In**.
3. Set up **Multi-Factor Authentication (MFA)** if prompted.

> ℹ️ `Saurabh Patil` can now log in, but has **no access to resources** yet, since **no policies** are assigned.  
> ✅ The user can still manage profile settings like password, email, etc.

---

## Step 3: Creating Users via CSV Import

1. Log out from the user and log back in as **Production Domain Admin**.
2. Go to:

```text
Main Menu > Identity & Security > Identity > Domains
```



3. Select **Production Domain** > **Users**.
4. Click **More Actions** > **Import Users**.

### Preparing the CSV File

- Download the **sample CSV** file.
- Open the file and **delete demo data**.
- Add information for new users.

**Required Fields**:

| Column            | Notes                                                                 |
|-------------------|-----------------------------------------------------------------------|
| User ID           | Leave blank (system will assign one)                                  |
| First Name        | First name of the user                                                 |
| Last Name         | Last name of the user                                                  |
| Primary Email     | User’s email address                                                   |
| Primary Email Type| Must be one of: `home`, `work`, or `other`                            |

> ⚠️ Using an invalid `Primary Email Type` (like `personal`) will cause the import to fail.

5. Save the CSV file.
6. Select the file in the Console and click **Import**.

### Tracking the Import Job

- A Job ID will be generated.
- Click it to view **status and logs**.
- If import fails, detailed error messages will appear.
- ✅ In our case, the import is **successful**.

---

## Step 4: Assigning Imported Users to Groups

1. In the Console, go to:

```text
Main Menu > Identity & Security > Identity > Domains > Production > Groups
```


2. Click the group name (e.g., `NetworkAdmin` or `VaultAdmin`).
3. Click **Add User**.
4. Select the appropriate user(s) to assign to the group.
5. Click **Add**.

✅ Now the users are successfully added to their respective groups.

---

## Recap

- Created a user via Console and activated the account.
- Imported multiple users using a CSV file.
- Assigned imported users to appropriate groups.
- Users are **created**, **activated**, and **grouped**, but still need **policies** to access resources (covered in upcoming lessons).

---

> 📌 **Best Practice:**  
> Always create groups aligned with organizational roles first, and then add users to those groups. Use policies to grant access at the group level.
