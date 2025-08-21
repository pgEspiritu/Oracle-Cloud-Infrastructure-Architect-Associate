# Demonstration: Site-to-Site VPN (Part 3)

## 🔹 Step 1: Configure Security Rules & Route Tables

### On-Prem Network (Ashburn)
- **Security List Rules**  
  - Added **Ingress Rule**  
    - **Source**: OCI VCN CIDR  
    - **Protocol**: ICMP (to allow ping traffic)  
- **Route Table**  
  - **Destination**: OCI VCN CIDR  
  - **Target**: Private IP of **CPE VM**  
  - 🔹 Note: **Source/Destination Check disabled** on the CPE VM

### OCI VCN (Phoenix)
- **Security List Rules**  
  - Added **Ingress Rule**  
    - **Source**: On-Prem CIDR  
    - **Protocol**: ICMP
- **Route Table**  
  - Added **Static Route**  
    - **Destination**: On-Prem CIDR  
    - **Target**: Dynamic Routing Gateway (DRG)

---

## 🔹 Step 2: Test Connectivity

### From On-Prem → OCI
- From Ashburn **ping VM** → Phoenix **test VM private IP**
  ```bash
  ping <OCI-VM-Private-IP>
  ```
- ✅ Successful response
From OCI → On-Prem
  - SSH into Phoenix test VM
  - Ping Ashburn ping VM private IP
    ```bash
    ping <On-Prem-VM-Private-IP>
    ```
    - ✅ Successful response

---

## ✅ Summary
- Configured security lists and route tables on both sides
- Successfully tested ICMP traffic:
  - On-Prem → OCI ✅
  - OCI → On-Prem ✅
- Site-to-Site VPN is fully operational
