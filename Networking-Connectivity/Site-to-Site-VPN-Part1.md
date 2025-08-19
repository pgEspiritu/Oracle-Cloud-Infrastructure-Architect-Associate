# Lesson: Site-to-Site VPN in OCI

## 🔹 What is Site-to-Site VPN?

Site-to-Site VPN (also known previously as **VPN Connect** or **IPsec VPN**) provides an **IPsec-based connection** between your **on-premises environment** and an **OCI Virtual Cloud Network (VCN)**.

- On-premises environment ↔️ Dynamic Routing Gateway (DRG) ↔️ VCN
- Uses a **Customer Premises Equipment (CPE)** device on the on-premises side
- Establishes a **secure IPsec tunnel** between your data center and OCI

👉 The traffic traverses over the **public internet**, but because it’s encrypted via IPsec, it remains secure.

---

## 🔹 What is IPsec?

IPsec ensures **encryption and decryption** of packets during transmission.

- **Encryption before sending** → Data is unreadable in transit
- **Decryption on arrival** → Data becomes usable at destination
- Traffic travels over the **public internet securely**

---

## 🔹 IPsec Modes

There are two IPsec modes:

1. **Transport Mode**
   - Encrypts **only the payload (data)**, not the header
   - Header remains intact (origin/destination info visible)

2. **Tunnel Mode**
   - Encrypts **entire packet** (header + payload)
   - Provides higher security
   - ✅ **Oracle supports tunnel mode**

---

## 🔹 Benefits of Site-to-Site VPN

1. **Cost-effective**  
   - Uses the public internet (no dedicated leased lines required)
2. **Quick setup**  
   - Great for proof-of-concept (POC) or testing
3. **Secure**  
   - Encrypted IPsec tunnels ensure data confidentiality
4. **Redundancy**  
   - Each VPN connection comes with **two tunnels** (Tunnel 1 & Tunnel 2)
5. **Routing options**  
   - Static routing  
   - Dynamic routing (**BGP**)  
   - Policy-based routing  

⚡ Oracle recommends configuring the **same routing type on both tunnels**.

---

## 🔹 Components of Site-to-Site VPN

Here’s a simplified architecture:
```text
 On-Premises Network ----(CPE)====[IPsec Tunnel]====(DRG)---- VCN (OCI)
```

---


### Key Components:
- **On-Premises Environment**
  - Customer Premises Equipment (**CPE**) – hardware or software-based VPN device
- **OCI Region**
  - **VCN** – your cloud network
  - **Dynamic Routing Gateway (DRG)** – connects VCN to on-premises
- **Site-to-Site VPN Connection**
  - Connects **CPE ↔ DRG**
  - Contains **two redundant tunnels**

---

## 🔹 CPE and CPE Object

- The actual **CPE device** is located on-premises.
- On OCI side, you must create a **CPE Object** → a **virtual representation** of your CPE.
- **CPE Object** requires:
  - Public IP address of the CPE device
  - Optional Internet Key Exchange (IKE) identifier

🔑 A single **CPE Public IP** can support **up to 8 IPsec connections**.

---

## 🔹 IPsec Connection

- Represents the actual **Site-to-Site VPN connection**
- Connects **CPE Object ↔ DRG**
- Each IPsec connection has **two tunnels**:
  - Each tunnel has:
    - A **public IP**
    - A **shared secret** (used for encryption/authentication)

---

## 🔹 NAT Scenario

Sometimes, the CPE device is **behind a NAT device**:

- NAT device provides the **public IP**
- CPE has a **private IP**
- In this case:
  - Update the **Internet Key Exchange (IKE) identifier**
  - Set it to the **private IP** of the CPE instead of public IP

---

## 🔹 IKE Versions Supported

Oracle supports:
- **IKEv1**
- **IKEv2**

---

## ✅ Summary

- Site-to-Site VPN connects **on-premises networks** with **OCI VCNs** using **IPsec tunnels**.
- Uses **tunnel mode** for full packet encryption.
- Comes with **two redundant tunnels** for reliability.
- Supports **static**, **dynamic (BGP)**, and **policy-based routing**.
- Requires **CPE Object + DRG + IPsec connection** on OCI side.
- Works even if CPE is **behind NAT** (with proper IKE configuration).


