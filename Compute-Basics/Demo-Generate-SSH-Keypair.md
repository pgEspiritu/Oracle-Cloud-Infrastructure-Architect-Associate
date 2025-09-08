# 🔑 Demonstration: Generating an SSH Key Pair

## 📌 Introduction
In this demo, we will learn how to generate an SSH key pair using two methods:  

1. **OCI Cloud Shell**  
2. **PuTTYgen (Windows)**  

An SSH key pair consists of:
- **Private key** → stays securely on your computer.  
- **Public key** → shared when creating an OCI instance for authentication.  

---

## 🖥️ Method 1: Generate SSH Key Pair Using Cloud Shell

1. Log in to the **OCI Console** (Ashburn region, in this example).  
2. Launch the **Cloud Shell** from the console.  
3. Run the following command to generate a key pair:

   ```bash
   ssh-keygen
   ```
4. When prompted:
  - Accept the default save location: ~/.ssh/id_rsa
  - Optionally, enter a passphrase for extra security.
5. Output:
  - Private key → `id_rsa`
  - Public key → `id_rsa.pub`
  ```bash
  ls ~/.ssh
  # id_rsa    (private key)
  # id_rsa.pub (public key)
  ```
⚠️ Important:
Anyone with access to the private key can connect to your instance. Always store it securely.

---

## 🖥️ Method 2: Generate SSH Key Pair Using PuTTYgen (Windows)

1. Open PuTTYgen (PuTTY Key Generator).
2. Click Generate and move your mouse around the blank area to generate randomness.
3. Once generated:
  - Copy the public key text and save it as mykey.pub.
  - Save the private key by clicking Save private key.
  - The private key will be saved in .ppk format (e.g., mykey.ppk).
4. Example:
  - `mykey.pub` → public key
  - `mykey.ppk` → private key

---

## ✅ Summary

- Cloud Shell Method generates keys in id_rsa and id_rsa.pub.
- PuTTYgen Method generates .ppk private key and .pub public key.
- Use the public key when creating OCI instances, and keep the private key secure on your machine.
